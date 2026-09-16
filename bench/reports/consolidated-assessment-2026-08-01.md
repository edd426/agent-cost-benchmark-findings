> Curated public snapshot, exported 2026-09-16. Historical statements retain their original dates; later corrections may supersede them. Identifiers, code, and fixture/answer-key details are withheld. See [README](../../README.md) for scope and limitations.

# Consolidated research assessment — 2026-08-01

Requested by Evan: everything learned across the program (~700 scored runs,
2026-07-09 → 08-01), assessed against whether the research direction serves
his actual work. Sources: synthesis-2026-07-11.md (master, Batches A–R),
batch reports T→today, findings.json, the P3/P4/P8 elicitation ground truth,
this week's judgment/GPT/XXL results. Maturity grades: **[R]** replicated or
frozen-prereg measured; **[M]** measured once; **[D]** directional.

## I. What we actually know now

### 1. Economics: caching ≫ routing, and scale finally has a price [R]
The 5× cache lever dwarfs every routing gain we ever measured (all ≤2×). New
this week: the XXL crossover finally resolved after six attempts — **Opus 5
solo completes the largest task in the suite (repo-wide migration): $172.74,
82 min, 1080 turns, oracle-pass** [M]. The old "solo cracks at XXL" was
cap-relative; given room, one strong context holds the whole problem. Solo
remains the default architecture at every scale we can test.

### 2. Routing: shape decides, and judgment is now a measured shape [R]
Haiku failure spans 0% (bounded format) → 69% (exhaustive sweep) → ~100%
(judgment). The judgment family graduated this week under frozen prereg:
**haiku 1/19, sonnet 18/18, opus5 18/18** across three landmine mechanisms —
and haiku's failures are the catastrophic kind (confidently deletes the
load-bearing resource). A "check dependencies" prompt line moves haiku only
0/3→2/6 [D]: the gap is disposition AND capability; you cannot cheap-prompt
seniority.

### 3. Cross-vendor: big tiers converge, cheap tiers diverge by mechanism [M]
After the dialect adjudication (see §5): **Sol (big GPT-5.6) matches the
strong-Claude ceiling on judgment** (kv 6/6 adjudicated, net 5/6, storage
6/6) and on sweeps (docs 6/6). Note the phrasing: our judgment tasks cannot
discriminate WITHIN the strong tier (sonnet and opus5 are both 18/18), so
"Sol ≈ Sonnet" was an under-determined gloss — Evan's working assessment
(2026-08-01) is **Sol ≈ Opus**, and nothing measured here contradicts it.
Separating Sol-vs-Sonnet-vs-Opus needs a task with headroom above Sonnet. **Luna (cheap GPT-5.6) is NOT a Haiku upgrade for judgment**: it
genuinely deletes the prod vault (11/12 across efforts) and high reasoning
effort does not rescue it [M, frozen prereg] — but it is competent at bulk
mechanical edits (5/6) and its docs weakness is specific to
omission-DETECTION, not editing (the second-instance rule caught an
over-broad claim before report). Caveats stand: codex scaffold + host config
ride along in every GPT number; tokens-only economics (subscription, no USD
comparability).

### 4. Verification is the product, in both directions [R — the program's central finding]
Forward: no cheap model's completion claim survives contact (40+ failed runs,
all claimed success; self-report 0/16; a $0.20 reviewer with
escalate-on-unparseable achieves 100% recall; a runnable checker rescued the
one cell we could test at [M]). Backward — this week's twist: **our own
verifiers failed the same way twice**, calibrated on Claude's phrasing (the
r106 sentinel command-shape gap; the kv/net token lists that mis-scored a
correct GPT agent 0/6). The literature says the same (τ-bench's do-nothing
agent; "Failure as a Process": false premises are the #1 trigger). The
generalizable law: *a check that cannot distinguish a real solution from a
differently-phrased or differently-shaped one will silently mis-route
trust* — at work exactly as in the harness.

### 5. The integrity machinery earns its cost [R, lived twice this week]
Pre-registration + adversarial review + skepticism caught, before external
report: a name-pattern leak and a gameable oracle in new fixtures (one free
review saved a 54-run batch), a false vendor-separation headline (Evan's
skepticism → retraction inside 2 hours), an inert safety guard under codex
(exposure swept: zero), and a $92 ceiling overshoot. Two corrections shipped
with full audit trails. This discipline is not overhead; it is why any of
the numbers above deserve belief.

### 6. Restart/handoff (Batch T) [R] — awaiting its cross-vendor act
Compact-summary handoff was the best restart arm (6/6); leftover artifacts
are fuel on fact-residue failures; the real trap is omission persistence
(successors trust plausible partial work). Untested where it now matters
most: cross-vendor succession (Claude→GPT), which is Evan's actual daily
pattern and newly cheap to test via the codex runner.

## II. Mapped against Evan's real work (P8/P4/P3 ground truth)

| His routing row (P8 §3) | What the program now says |
|---|---|
| Decommission/cleanup: delegate + watch live | Correct posture, now quantified: cheap tiers act confidently-wrong (the 1000h failure class), so watch-during or sonnet-tier. Luna: do not route this at all. |
| Terraform/pipeline: plan-gate | Matches Rule 4 exactly; SLOW-1 (built) measures the real failure — agents not waiting for the slow signal. |
| Ticket/docs: cheap + end-check | Supported: bulk edits are cheap-safe (haiku ~100% bounded-format; luna 5/6); omission-DETECTION sweeps are not (both vendors' cheap tiers). End-check = a census, not a read-through. |
| Emails/comms: never | Untested by design; no reason to spend here. |
| Failure-cost asymmetry 1/1/10/1000 | Designed into 17g scoring; the judgment family is the only instrument that prices the 1000h class. Reporting layer still owed. |

**The honest gap (P4 workload triangulation):** the suite is deep on
Terraform-shaped judgment and exhaustive edits (6/15 tasks) and has **zero
Bicep, zero CI/pipeline-repair, and thin investigation/diagnosis** — three of
the heaviest rows in his measured work mix. Depth has outrun breadth.

## III. Direction verdicts (keep / refocus / stop)

**KEEP — high value per dollar:**
- Judgment family + 17g fix→re-freeze (the only 1000h-class instrument; also
  the vendor-routing discriminator).
- Verification/checker thread (SLOW-1 ready; CLAIM-1 needs a red-checker
  task; cross-dialect oracle gate to build — now provably load-bearing).
- Cross-vendor cells via codex (marginal cost ≈ $0; feeds his real routing
  decisions; runner-v2 debt first for any new stratum).
- Realism 12a/12b roll-outs (cheap, directly attack the leak/ceiling disease).

**REFOCUS — right question, wrong next step:**
- Scale/XXL: answered at n=1; buy r3 only as a $173 confirmation, then stop —
  the thread's remaining value is §14, not more reps.
- Handoffs: elevate the cross-vendor variant above the remaining same-vendor
  phase-2 cells.
- Token-savers: §8 only with the search-the-log baseline (the published
  competitor is "grep, free"); §10 only phase-0 first. Both are
  kill-quickly designs — run them to closure, not to nurture.
- Breadth: the next NEW task family should be **Bicep or CI-repair, not a
  fourth Terraform landmine** (P4 says that's where his hours are).

**STOP / stay stopped:**
- Advisor strategy (mechanism blocked twice; revisit only after §14a).
- Older same-tier models, semantic-entropy, best-of-N (parked, correctly).
- Further Luna judgment reps (the question is answered; deletes the vault).

**STRUCTURAL (the meta-verdict):** the binding constraint on the science is
now **session economics, not ideas** — XXL needed six attempts across three
days because one run exceeds a Max session; every night is shaped around
caps. §14 (cloud/API runner) converts that from a nightly tax into a one-time
build and unblocks the advisor besides. It is the highest-leverage
infrastructure item on the board.

**Bottom line on "are we picking valuable subjects":** the two threads that
consumed the most spend — judgment and verification — are precisely the two
that map onto his highest-cost real failure modes (confident wrong deletions;
trusting completion claims), and both produced routing-grade answers. The
program's genuine weakness is breadth drift: the task diet looks like the
harness's history, not his week. One new non-Terraform family plus the §14
runner would fix both.
