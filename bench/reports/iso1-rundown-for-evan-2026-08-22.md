> Curated public snapshot, exported 2026-09-16. Historical statements retain their original dates; later corrections may supersede them. Identifiers, code, and fixture/answer-key details are withheld. See [README](../../README.md) for scope and limitations.

# ISO-1 (#87): the whole thing, in plain language

**For Evan, 2026-08-22.** Written because the fix cycles have gone on long enough
that the thread is hard to hold. Assumes you remember nothing about it.

[Internal model-routing notice omitted from public export.]

---

## 1. What ISO-1 actually is

ISO-1 is the guarantee that **a model being scored on a benchmark task cannot
read the answer key for that task.**

The mechanics matter, so here they are concretely. Every task in [implementation detail withheld]
has two parts that live side by side on disk:

- the **workspace** — the broken Terraform, the stale docs, whatever the model is
  asked to fix. The model gets a directory and a prompt.
- the **answer key** — usually [implementation detail withheld], sometimes
  [implementation detail withheld], sometimes written out after a run as [implementation detail withheld].
  This is the hidden marking scheme. The grader reads it at the end to score the
  run. The model is never supposed to see it.

Both sit on the same laptop, in the same home directory, often a few directories
apart. Nothing about the filesystem stops a process from reading either one. The
only thing standing between the model and the answer key is a configuration we
generate that tells Claude Code "you may not read these paths."

**The concrete example.** docs-omissions asks the model to read a change log and
a set of docs and report which activities were documented and which were silently
omitted. The answer key is a JSON file listing the omitted activity IDs —
a short list of activity ids (redacted here — see the note below). A model that reads that file scores
a perfect result in about four seconds, having done none of the work the task is
measuring. We know exactly what that looks like because our own test does it on
purpose: the isolation smoke's "green control" removes the denies and reads the
key, precisely so we can prove our leak detector is working. It fired 14 canary
sentinels doing so, today.

**What makes this hard, and why it has taken four attempts.** There are two
completely separate enforcement mechanisms, and this is the single most important
mechanical fact in the whole story:

| layer | what it governs | can it be bypassed? |
|---|---|---|
| permissions.deny — the **tool layer** | the Read, Glob and Grep *tools* the model calls | **Yes, trivially.** It only inspects tool calls. |
| sandbox.filesystem.denyRead — the **OS layer** | Bash and every subprocess Bash spawns, via macOS Seatbelt | **No.** It is a kernel-level file-read-data deny. |

If we only block the tool layer, the model runs [implementation detail withheld] — or
[implementation detail withheld] — inside a Bash call, and reads the key
straight through. That is not theoretical: it was demonstrated on this laptop
twice, independently, on 2026-08-22, and it is reconfirmed by a free test in the
repo that takes two seconds to run. Every task template allows [implementation detail withheld],
and Terraform reads files transitively through [implementation detail withheld] and local-exec, so the
Bash channel cannot simply be closed.

The whole ISO-1 saga is: we kept fixing the layer that doesn't hold.

## 2. Why it matters, and what the freeze has cost

**If a key leaks, the affected numbers are not wrong — they are meaningless.**
The benchmark exists to measure whether a model can do platform work. A run that
read the key measures whether the model can find a file. Both produce "PASS," and
after the fact you generally cannot tell them apart from the score alone: you have
to go back to the transcript and check what it read. So a leak does not add noise
we can average out. It silently converts an unknown fraction of results into
something that looks like data and isn't.

That is why this became a hard freeze rather than a "fix it when convenient."
**Since 2026-08-21, freeze #87 has blocked all providerless dispatch**, which
means:

- **Q2** — frozen mid-flight.
- **the 18-task admitted bank** — the whole admitted set, undispatchable.
- **the Haiku sweep and the Opus-classify sweeps.**
- **MH-1 round 6** re-review draws.

Roughly three days of experimental throughput, and it is still blocked as of
tonight.

**One thing worth being clear-eyed about:** ISO-1 was not found by us auditing
ourselves. It came out of a Sol review as a BLOCKER, and it was found *after* runs
had already been executed. The freeze protects future results. What it does not do
is tell us the status of results collected before it — that is a separate question
nobody has asked yet, and I flag it here because it is the kind of thing that is
easy to not notice you have not asked.

## 3. The fix history, and your fix4-vs-fix5 question

| attempt | what it tried, in one sentence | outcome |
|---|---|---|
| **attempt 1** | Hard-coded six deny rules into one of the ten settings templates. | **Failed review.** Nine of the ten templates still had the hole, and Sol found two checkouts under [implementation detail withheld] holding byte-identical answer keys that no rule covered. |
| **fix2** | Computed the deny list per-run instead of hard-coding it, so new directories get covered. | **Failed review.** Six remaining holes; the deny list still had to name each place a key could be. |
| **fix3** | Closed those six holes; routed review launches through a fail-closed profile. | **Failed review.** Verdict: "scope refusal and both isolation layers remain bypassable." Second consecutive fix to self-report green and then fail independent review. |
| **fix4** | The comprehensive last patch — fixed everything the fix3 review named at once, and, crucially, moved the answer-key denies into the **OS layer**. | **Failed review** (this is the big one — see below). |
| **fix5** | The pre-committed rebuild: stop listing what to block, block everything and hand back only the workspace. | Built and committed today (c62c445). **Not yet independently reviewed.** |

### Your question: "wasn't fix4 basically deny-by-default already?"

**You are half right, and the half you are right about is the important half.** It
is a fair reading of the architecture note — I wrote in it that fix4 "IS
effectively the deny-by-default approach already." That sentence was true about the
*enforcement layer* and misleading about the *coverage rule*, and the distinction is
the whole difference between the two builds.

What fix4 got right: it enforces at the OS layer. That is the part that actually
holds, and it was a genuine advance over fix2 and fix3 — fix5 keeps it unchanged.

What fix4 still did the old way — **it denied by NAME.** Its OS-layer rules said,
in effect, "deny anything matching [implementation detail withheld], [implementation detail withheld], [implementation detail withheld],
plus this list of specific directories we enumerated when the run started." So:
[Quoted source material omitted from the public export.]
[Quoted source material omitted from the public export.]

fix5's rule is: deny your entire home directory, the repo, the workruns root, the
temp directories — the whole territory — and then re-grant read access to exactly
one directory, the workspace this run is supposed to work in. Plus two named
toolchain files (.gitconfig, .terraform.d) so git and Terraform still function.

The practical difference, stated as a test you can apply yourself:

| | fix4 | fix5 |
|---|---|---|
| key at [implementation detail withheld] | blocked (matches the pattern) | blocked (inside the denied repo) |
| key copied to [implementation detail withheld] | **readable** — matches no pattern, in no listed directory | **blocked** — it is under home |
| key in a directory created after the run started | blocked only if it kept an [implementation detail withheld] component in its path | **blocked** — the container was denied, not the leaf |
| a place none of us has thought of yet | **readable** | **blocked** |

That last row is the point. A deny-list fails **open**: the default is "allowed," so
anything nobody enumerated is reachable, and you can never prove the list is
complete — which is exactly why three consecutive reviews each closed with "still
bypassable" on a *different* path each time. Deny-by-default fails **closed**: a
path nobody thought of is denied, and the thing you have to get right is the short
list of what you deliberately allowed, which is auditable in a way an infinite list
of what you forgot to block is not.

**This also shrinks the residual you personally accepted.** You signed off on
leaving open the "answer key copied to an arbitrary filename" case, correctly, on
the grounds that a path deny-list structurally cannot name it. Under fix5 that copy
*is* blocked, as long as it lands anywhere in the denied territory — because denial
is now by location, not by name. What remains is a copy placed in [implementation detail withheld], [implementation detail withheld],
[implementation detail withheld] or [implementation detail withheld], which we must leave readable because that is where the
interpreters and binaries every task needs to execute live. Strictly smaller than
before, and now stated rather than implied.

**So why did fix4 fail review, if the OS layer was right?** Mostly for reasons that
have nothing to do with pattern-versus-container, which is the genuinely bad news
in this document and is section 5's subject.

## 4. Historical answer-key exposure

The original note records that a marking scheme had entered private Git history. Exact locations, retrieval instructions and answer-related payload descriptions are withheld. Removing a key from the current working tree does not remove historical copies; this public repository is a fresh static export and includes none of the source Git history.

## 5. Honest value assessment

### What it has cost

Rough, in your units (session/weekly %, per your standing preference), and rough is
the honest word — we only started the standing meter ledger tonight, so the earlier
cycles are reconstructed from commit density rather than measured:

- **~50 ISO-1 commits across three days** (2026-08-20 → today), spanning five build
  lanes and four independent review cycles.
- **The fix4 review alone consumed most of a 5-hour session bucket** — it was at 61%
  used with the depth pass still running, and that bucket also carried other work.
  It was eight pinned model cells: six shards, a depth pass, a grader.
- **Three of the four reviews ran on codex**, which is the scarce meter. Codex weekly
  moved roughly 75% → 81% over the period, though not all of that is ISO-1.
- Weekly all-models sits at ~72%, boosted through Aug 31.
- Against that: **three days of experimental throughput blocked**, which is the
  larger cost and does not show up on any meter.

### What is still exposed

This is the part I most want you to actually read, because it reframes the problem.

The fix4 review confirmed **48 blocker-grade defects**. Today's rebuild — executed
exactly as pre-committed — closes **4 of them**. About 44 survive, because they were
never path-coverage problems at all:

- **The instruments are unsound.** [implementation detail withheld] returns
  "EVIDENCE-OK" on an evidence directory containing **zero probe output**, and again
  when the only recorded result is FAIL. And the leak-scanning classifier does not
  read several channels the transcript actually emits. Meaning: *the greens we have
  been reporting to each other for four cycles were, in part, unfalsifiable.*
  I hit this live today — a probe scored FAIL on a read that the raw transcript shows
  was correctly denied, because the scorer picked the wrong tool call.
- **Some dispatch paths skip the gates entirely.** [implementation detail withheld]
  launches a model on the raw template with no isolation gates at all. The debrief
  runner never runs the host inventory. A scope check passes vacuously on a
  directory that does not exist.
- **Operator-level hardening is weak** — the lock can be dodged by relocating a
  directory, its token sits in plaintext inside the directory it guards, the review
  exemption can be spoofed with an environment variable.
- **The codex review lane never got any of this.** It runs a completely separate
  profile builder that is still the old architecture.

**The honest framing: the pre-committed rebuild was scoped, in good faith, against
the failure we expected (another missed path) and not against the failure we got.**
The rebuild is correct as scoped. It is not enough to lift the freeze.

### The three options, and what I recommend

**(a) Remediate everything, then review.** Safest, and the most expensive: it is a
rebuild of the gate and instrument layer plus a second architecture inversion on the
codex lane. Multiple sessions, and the freeze holds throughout. My concern is not the
cost so much as that it keeps us in a loop that has already run four times.

**(b) Narrow unfreeze now**, on the strength of the OS layer alone. Tempting, and I
do not recommend it as stated — not because the OS layer is weak (it is the one
thing in this story that has consistently held) but because the *evidence* for any
future green comes from instruments the review just showed will report success on an
empty directory. You would be unfreezing into a state where we cannot tell whether
the next leak happened.

**(c) Re-scope or abandon** — accept that laptop-level isolation costs more than it
returns, and change the design so leakage is detected after the fact by auditing
transcripts instead of prevented up front. Worth naming honestly, and I do not
recommend it: post-hoc auditing has to be trustworthy too, and it would be built on
the same classifier that is currently one of the broken instruments.

**My recommendation: a middle path — split the remaining 44 by threat model and fix
only the half that a *model* can reach.**

The threat here is a model incidentally reading a key during a run. It is not a
hostile operator: you are the only operator. That distinction cuts the remaining
work roughly in half:

- **Fix first (model-reachable, or required to trust any green):** the evidence gate
  that passes on empty, the classifier's unscanned channels, and the dispatch paths
  that launch models outside the gates. Without the first two, no future PASS means
  anything — including a PASS on the rebuild.
- **Accept with a recorded note (operator-reachable):** the lock dodge, the plaintext
  token, the environment-variable spoofs. Every one requires someone to deliberately
  set an environment variable to defeat a safeguard on their own laptop. Record them
  as known and accepted rather than spending review cycles on them.
- **Decide separately:** codex-lane parity. If the codex review lane stays on the old
  architecture, any unfreeze is Claude-lane only — which may be perfectly fine, but
  should be a decision rather than a discovery.

Then one review of that, and the freeze lifts on the result.

**The risk I am accepting on your behalf in recommending this**, stated plainly so
you can overrule it: the operator-reachable defects are real and I am proposing we
ship with them open. If this benchmark is ever run by someone other than you, or
published as a harness others use, that judgment inverts and they have to be fixed.

**The one thing I would not do is a fix6-style patch cycle.** Four cycles have now
produced the same shape of outcome: self-reported green, independent review finds it
elsewhere. The instrument problem is the reason that keeps happening, and it will
keep happening until the instruments are fixed. That is the recommendation's real
argument.

### Where this stands right now

- The rebuild is **built and committed** (c62c445), all deterministic gates green,
  live probe run, detector confirmed alive.
- **Freeze #87 still holds.** I did not lift it and it should not be lifted on the
  rebuild alone.
- The rebuild's own independent review is **queued but deliberately not dispatched** —
  a review costs most of a session bucket, and if you take the recommendation above,
  what should be reviewed changes. Dispatching first would spend it twice.

Full technical detail: bench/reports/iso1-fix5-rebuild-2026-08-22-opus.md.
The review that triggered all this: bench/reports/iso1-fix4-review-2026-08-22-opus.md.
