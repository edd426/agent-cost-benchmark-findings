> Curated public snapshot, exported 2026-09-16. Historical statements retain their original dates; later corrections may supersede them. Identifiers, code, and fixture/answer-key details are withheld. See [README](../../README.md) for scope and limitations.

# ISO-1 (#87) — architecture note (helm framing, 2026-08-22)

[Internal model-routing notice omitted from public export.]

## The pattern

fix2 (FAILED review) and fix3 (FAILED review, 2026-08-22) failed with the same
verdict: **"still bypassable."** Every fix in the chain has the same shape — a
reviewer finds a reachable path, the fix ADDS A DENY RULE for it, the next
reviewer finds a different reachable path. fix3's own commits: "deny
unregistered /tmp checkouts", "add the missing workruns deny". The SW-OPUS-1
skeptic found the same in miniature: "the deny list has exactly two Read entries
and neither covers WORKRUNS_ROOT", with a full answer-key checkout under it.

## The diagnosis

The isolation is a **denylist** — enumerate bad paths, block them one at a time.
Denylists **fail open**: default is "allowed", so any un-enumerated path is
reachable and completeness is unprovable. Convention #21 (verified) states the
structure directly: the two layers cover DIFFERENT surfaces — sandbox denyRead
governs Bash, permissions.deny governs the Read tool — "neither is
comprehensive alone." Two incomplete denylists on different doors; patching
either lengthens its list without ever closing it.

## The reframe

**Invert to deny-by-default (positive isolation / allowlist):** stage only what
the review needs into an isolated location and allow nothing else. A forgotten
path is then DENIED, not exposed — the failure mode flips from fail-open to
fail-closed. Partial working proof already exists: the swarm-review staging
(SW-OPUS-1 ran a worktree at the pin, outside the repo; the grader provably read
ZERO answer-key files, audited). Open question for the design lane: how fully the
current tooling ([implementation detail withheld]) implements deny-by-default vs
still leaning on enumerated denials.

## Consequence for the next review

- Do NOT swarm-review another denylist patch — that polishes the wrong
  architecture. Order: decide architecture → rebuild on positive isolation →
  swarm-review THAT.
- The Opus-xhigh beat-swarm IS well-suited to the review once there is a
  positive-isolation build: hole-hunting is a coverage problem (one beat per
  bypass-surface class — Bash layer, Read-tool layer, env, path-resolution/
  symlink, staging integrity). The earlier "swarm multiplies the sandbox
  surface" objection dissolves under staging: all shards share ONE staged
  sandbox, no per-shard multiplication.

## The decision for Evan (direction/risk)

**Rebuild ISO-1 on deny-by-default, or attempt a third denylist patch?**
Helm recommendation: REBUILD — two failed patches on "still bypassable" is the
evidence the list will never close. If approved: a non-Fable Opus lane produces
the positive-isolation design (hole detail stays out of the Fable context),
returns it at summary level, build, then the Opus-xhigh beat-swarm reviews it.

## DECISION (Evan, 2026-08-22): one more patch, then deny-by-default

Evan chose: **attempt ONE more denylist patch (fix4); if it fails review,
switch to deny-by-default (positive-isolation rebuild) — no fix5.** This is the
last patch. The fallback is PRE-COMMITTED, so the outcome is low-regret: fix4
passes → cheap win + unfreeze; fix4 fails → rebuild, having spent only the patch
cost. Helm recommendation was rebuild-first; Evan's patch-first-with-fallback is
recorded as his call and is a reasonable de-risk.

Execution:
- fix4 built by a non-Fable Opus lane (reads #87 + the fix3 review; helm stays
  boolean). Because it is the LAST patch, it must be COMPREHENSIVE — address
  every hole the fix3 review named at once, not incrementally.
- fix4 reviewed by the **Opus-xhigh beat-swarm** (Evan's requested approach for
  the next ISO-1 review; hole-hunting is a coverage problem the swarm fits),
  under staging isolation so the review of the isolation fix is itself
  answer-key-isolated. This is also the swarm-review wild-ledger's first genuine
  multi-surface infra target.
- On swarm-review PASS → freeze lifts (Claude-only providerless dispatch);
  Q2 + admitted bank + Haiku/Opus-classify sweeps unblock. On FAIL → the
  pre-committed deny-by-default rebuild.

## CROSS-POLLINATION: the SW-OPUS-LOW operator found the likely ISO-1 fix (2026-08-22)

Solving its OWN staging isolation (so a low-effort shard couldn't read the SEB-1
key), the SW-OPUS-LOW operator empirically demonstrated the core ISO-1 thesis and
a working fix, in a fresh context, independent of the #87 chain:
- **A Claude-Code permission deny-list is INSUFFICIENT** — a [implementation detail withheld] read
  of the key BYPASSED it. This is the ISO-1 fail-open problem, reproduced: the
  tool-layer denylist doesn't govern a subprocess's own syscalls.
- **An OS-level sandbox-exec posture HELD** — deny file-read-data of the main
  repo, allow .git (so worktree git still works); under it, Read/cat/head/sed
  AND the python3 interpreter read of a known key path are ALL denied at the
  SYSCALL level, while staging reads and git work. Residual = the shared git
  object DB (audited, as SW-OPUS-1's accepted D-14).

Architecture implication: ISO-1 should be fixed at the **OS/syscall layer
(deny-by-default sandbox-exec), not the Claude tool-permission layer** — a tool
denylist, however complete, is bypassable by any subprocess the review can spawn.
This is the strongest evidence yet for the deny-by-default direction, and it hands
fix4 a PROVEN mechanism. Note: an OS-level deny of the whole main-repo root also
closes the "arbitrary-name key copy" hole below IF the copy lands under the denied
root (denial is by directory, not by answer/ pattern) — the residual shrinks to a
copy placed outside the denied root (e.g. /tmp or the staging root itself).

## fix4 lane pre-finding (architecture level, captured at the 2026-08-22 pause)

Before the pause, the fix4 lane reached (read phase only, nothing built) an
architecture-relevant conclusion worth preserving: **most of the remaining holes
appear denylist-closable** (the tooling supports the pattern mirroring fix4
would need), **BUT one hole is structurally NOT closable by any denylist — an
answer key COPIED TO AN ARBITRARY NAME outside any answer/oracle pattern.**
Catching that needs a content/inode inventory, not a path denylist. That single
hole is direct deny-by-default evidence: a denylist can only block paths it can
name, and an arbitrarily-named copy has no nameable pattern. Technical detail
(CLI glob/precedence mechanics) stays in the fix4 lane's report on resume — not
ingested here.

Implication for Evan's patch-then-rebuild plan: fix4 may PASS the swarm review on
the nameable holes yet still leave the arbitrary-name-copy hole open. Decide on
resume whether that residual is acceptable under a Claude-only unfreeze (the
review will surface it) or whether it alone justifies going straight to
deny-by-default. This is exactly the fork Evan pre-committed to.

## DECISIVE: the two layers are tool (bypassable) vs OS (not) — fix4 uses OS

fix4 ran the enforcement question to ground (test_iso1_os_bypass.sh + paid
smoke, reproducing the SW-OPUS-LOW result on this host). Answer:
- **permissions.deny = the TOOL layer.** A [implementation detail withheld] / cat bypasses
  it (subprocess reads don't go through the Read tool). This is what fix2/fix3
  leaned on and why they failed.
- **sandbox.filesystem.denyRead = the OS layer** — it compiles to a macOS
  Seatbelt/sandbox-exec file-read-data deny and stops subprocess reads
  (cat/head/sed AND python3 open() all denied at the syscall layer). This is the
  SAME mechanism the SW-OPUS-LOW operator called "sandbox-exec" — not two
  mechanisms, ONE OS layer under two names. My earlier note implying a separate
  sandbox-exec adoption was wrong; there is one OS layer.
- **fix4 already uses it:** its Hole-3 fix mirrors the answer/oracle patterns
  into sandbox.denyRead (the OS layer). So fix4 is NOT a tool-only denylist
  patch — it is an OS-level deny of the answer surfaces. The honest fork verdict
  is therefore "the tool denylist alone can't close the subprocess channel, but
  the OS layer can and fix4 uses it" — NOT "a denylist fundamentally can't."

Implication for the patch-vs-rebuild fork: **fix4 IS effectively the
deny-by-default approach already**, scoped to answer PATTERNS rather than
whole-repo. The one residual (arbitrary-name copy OUTSIDE every denied root) is
closable later by a SMALL delta — widen the OS denyRead from answer-patterns
to whole-repo-except-staging (that is "full" deny-by-default). Evan has ACCEPTED
the residual for the Claude-only unfreeze, so this widening is optional/future,
not required now. 14/14 deterministic probes + 17/17 paid smoke green.

## fix4 BUILT + READY (2026-08-22) — OS-sandbox worked; one honest residual

fix4 COMPLETE (iso1-fix4-build-2026-08-22.md, READY FOR SWARM REVIEW: yes,
6 hole-group commits 558970a..df4bd17). The cross-pollination PAID OFF: fix4
adopted the OS-sandbox mechanism and the decisive new probe proves a SUBPROCESS
read (python3-style) of a pattern-only answer tree is now DENIED — the exact
channel fix3 left open. 6/6 fix3-review holes + the bypassable scope refusal +
fix3-build defects all fixed with fail-closed probes; 13/13 deterministic probes
+ 17/17 paid smoke green.

ONE residual, LEFT-OPEN HONESTLY (not fake-closed): an answer key copied to an
ARBITRARY NAME OUTSIDE any denied root/pattern — a path-deny structurally cannot
name it (needs content/inode inventory). This is the deny-by-default evidence.
DECISION for Evan at the swarm-review step: is this residual acceptable for a
Claude-ONLY unfreeze? (Helm read: it requires a deliberate copy-to-arbitrary-
name action outside the denied tree, which our own experiment agents do not do —
low risk for a Claude-only unfreeze; but the swarm review assesses it, and if it
weighs the residual too heavy, that IS the deny-by-default trigger.)

SEQUENCING (convention #21: concurrent swarm reviews sharing [local path withheld]
are NOT supported; and fix4's own Gate A flags the live SW-OPUS-LOW worktree as
an answer-copy on the host):
  SW-OPUS-LOW checkpoint → depth go → grade → TEARDOWN its pin worktree →
  host freeze-clean → THEN dispatch the ISO-1 Opus-xhigh swarm review of fix4 →
  PASS lifts freeze (with the residual judged acceptable) / FAIL → deny-by-
  default rebuild. The ISO-1 review does NOT run concurrently with SW-OPUS-LOW.

## EVAN DECISION (2026-08-22): accept the residual, unfreeze after verify

Evan: "unfreeze and don't let the residual be blocked." The arbitrary-name-copy
residual is ACCEPTED for the Claude-only unfreeze — it must NOT block. But the
two-reviewer gate (convention #14) still runs: the Opus-xhigh swarm review
VERIFIES the 6 fix3-review holes are actually closed (fix2/fix3 both self-
reported green and failed independent review — the verification is the safety,
separate from the residual). Instruction to that review: the arbitrary-name-copy
residual is a KNOWN, EVAN-ACCEPTED limitation — do NOT fail on it; fail ONLY if a
hole fix4 claims to close is in fact still open. Swarm-review PASS → UNFREEZE
(Claude-only providerless dispatch); FAIL (a claimed-closed hole still open) →
deny-by-default rebuild.

[Temporary personal scheduling and operational dispatch instructions omitted.]

## Historical handoff excerpts withheld

Duplicated operational handoff text is omitted; the architecture and decision chronology above are retained.

