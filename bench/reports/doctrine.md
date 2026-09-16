> Curated public snapshot, exported 2026-09-16. Historical statements retain their original dates; later corrections may supersede them. Identifiers, code, and fixture/answer-key details are withheld. See [README](../../README.md) for scope and limitations.

# Doctrine — what the experiments teach, as operating rules

**Function**: the THEORY layer of this repo, distinct from the evidence
layer. [implementation detail withheld] records what was measured, with grades and caveats;
this file records the rules of thumb the measurements justify, written to
be acted on at work. Every rule cites its evidence by registry id or
report. **Maintenance contract**: when a cited finding is retracted or
superseded, the rule updates in the same session (the corrections
discipline applies here exactly as it does to the synthesis). New rules
enter only with evidence attached — this file never gets ahead of the
registry.

Established 2026-08-02 from Evan's formulation of the routing doctrine
(in-session, morning) plus the program's accumulated findings. Voice:
Evan's process, evidence-annotated.

---

## 1. Routing doctrine

**1.1 Unfamiliar task → strongest model, solo.** When you don't know a
task's shape or stakes, route it to the strongest available model in one
context. Not just prudence: the decisive error in failed runs lands early
with a ~zero-step recovery window, so you cannot monitor a cheap model to
safety [ne5-annotation-pilot; Failure-as-a-Process 2607.09510]; and
"smartest" is often cheapest per CORRECT result anyway
[opus5-frontier-cost-per-correct; Price Reversal 2603.23971: in 32% of
pairs the cheaper-listed model costs more in total] ~~— and this now extends
strong-vs-strong: at XL scale Opus 5 solo beat Sonnet solo AND the 3-leg
staged pipeline (strong plan → cheap exec → strong close) on $/correct
($9.81 vs $11.86 vs $12.68, 4/4, one instance, directional)
[opus5-xl-solo-cheapest-per-correct; batch-o5xl-2026-08-09.md;
staged-pipeline figure corrected 2026-08-17 — the previously cited $11.58
was a pooled leg-mean construction matching no chain ever run; per-chain
mean of the 4 complete chains is $12.68, median $12.60, and the pipeline
was never cheap-first: it pays strong at BOTH ends; Sonnet figure corrected 2026-08-21 — the published $12.35 (3/4) priced an infra-error row in (convention #4); consistent figure 3/3 $11.86, and the Opus-vs-Sonnet margin is not interval-separated at n=4 — orderings robust, margins fragile [met1-sensitivity-retro-2026-08-21]].~~ **[STRUCK FIX-1 2026-09-02 — opus5-xl-solo-cheapest-per-correct is RETRACTED (findings.json [implementation detail withheld], 2026-08-30); §3.2's erratum below ("The Opus-at-XL orderings (C1/C2) do not carry") says quote NO XL tier ordering, in either direction, until a live separator exists. See that erratum and the FIX-1 erratum at the end of §1.1.]** The boundary runs the other way too: on an easy
docs task Opus 5 passes 3/3 but at ~1.3x Sonnet's price (docs-omissions
$0.28 vs $0.21/correct, cross-date strata) — the premium is for work the
cheaper tier can't reliably do [batch-docsomissions-o5-2026-08-09.md].
Two 2026-08-16
literature amendments (challenge-q1/q2 reports, Evan-approved 2026-08-17):
(a) routing gains at matched quality are real but CONDITIONAL on a trained
escalation signal — a trained step-level router matched Opus quality at 47%
of cost while every untrained variant washed or lost (TwinRouterBench
2605.18859 Table 3; SR-KNN self-rating wash $0.741 vs $0.740) — no trained
signal → strong solo stands. Router training is harness investment: apply
the 1.3 volume filter. (b) "Delegation does not save money" is superseded
by the SPLIT-ORDER rule: strong-first (strong plans/briefs, cheap executes
after) loses or washes [avoid-naive-delegation; the r3 paraphrase failure,
xl-delegation-dive-2026-07-11; Bechard 2604.00073 "no systematic
advantage"]; cheap-first (cheap drafts/sweeps/explores, strong model
verifies and CLOSES ITSELF) is the live cost-saving region [our XXL
sandwich — the closer repaired all 4 failed cheap end-states directly;
RLM-Cascade 2606.22840, 45.8% cut at held quality]. Our "scale crossover"
is confounded with split order (challenge-q2 P0 — a post-hoc sort, not yet
a controlled result); order-isolation experiment registered 2026-08-17.
One strong context still completes even the largest task given room
[xxl-solo-uncapped-completion].

**ERRATUM (DOC-1 2026-09-02) — the Price Reversal figure is wrong, and the
citation is attached to an estimand the paper does not measure.** Struck:
~~"Price Reversal 2603.23971: in 32% of pairs the cheaper-listed model costs
more in total"~~ as offered in support of "smartest is often cheapest per
CORRECT result". Replacement: **cite 21.8%** — the paper's own aggregate over
252 pairwise comparisons (28 model pairs x 9 tasks); **32.1% is the per-task
MAXIMUM, on MMLUPro, in a 10.7%-32.1% range**, and the 32% that reached us is
the abs-page summary, not the v1 body. And cite it only for what it measures:
*listed price mispredicts SPEND*. Decisive line, verbatim: the paper *"[does]
not analyze the cost-accuracy tradeoff (Appendix B) - it measures raw cost per
query and never divides by pass rate. It is therefore a weaker prior for
doctrine 1.1 than we have been treating it as: it establishes that listed price
mispredicts spend, not that it mispredicts cost-per-correct"*
[challenge-q1-routing-2026-08-16.md:483-493]. Its 9 tasks are all single-turn
chat-completion API calls; none is multi-turn agentic [same cite].
**Rule as it now stands:** unfamiliar task -> strongest model, solo. The
load-bearing evidence for the per-correct half is OURS
[opus5-frontier-cost-per-correct; ~~opus5-xl-solo-cheapest-per-correct~~ **[STRUCK FIX-1 2026-09-02 — retracted 2026-08-30; DOC-1's own text is left otherwise as written]**] plus the
early-decisive-error result [ne5-annotation-pilot]; Price Reversal is a
price-is-not-spend prior at 21.8%, nothing more, and it does not carry the
per-correct claim on its own. Hint: two figures circulate for this paper - the
provenance trail is in challenge-q1-routing-2026-08-16.md, section "Provenance
notes and corrections". Written into that review's appendix 2026-08-16 and
never surfaced to doctrine; no later annotation here addresses it.

**ERRATUM (FIX-1 2026-09-02) — §1.1 was citing a retracted finding, in two
places, including inside the DOC-1 erratum added earlier today.** Struck above:
the XL strong-vs-strong clause ("at XL scale Opus 5 solo beat Sonnet solo AND
the 3-leg staged pipeline on $/correct, $9.81 vs $11.86 vs $12.68") and the
appearance of opus5-xl-solo-cheapest-per-correct in DOC-1's "load-bearing
evidence" list. That id has carried [implementation detail withheld] in [implementation detail withheld]
since 2026-08-30 (hygiene92-c5-2026-08-30.md, issue #92 item 2), and §3.2's
2026-08-30 erratum — see **"The Opus-at-XL orderings (C1/C2) do not carry"**,
below in §3.2 — states the rule plainly: *the comparison rests on
tf-bulkedit-xl, which has been [implementation detail withheld] (excluded
from tier-separation scoring) since 2026-07-31, and the arms did not see
identical prompt text; quote NO XL tier ordering, in either direction, until a
live separator exists.* DOC-1 re-asserted it the same day §3.2 forbade it;
DOC-1's wording is preserved and annotated, not rewritten.

**Rule as it now stands (FIX-1 2026-09-02):** unfamiliar task -> strongest
model, solo. Two live legs carry it, and the XL leg is not one of them:
(a) the early-decisive-error result — the decisive error lands early with a
~zero-step recovery window, so you cannot monitor a cheap model to safety
[ne5-annotation-pilot; Failure-as-a-Process 2607.09510]; and (b) the
per-correct leg, which now rests on opus5-frontier-cost-per-correct ALONE
[status directional, the only live per-correct finding in findings.json:
Opus 5 at $1.14/correct on tf-bulk-tags 3/3, $0.83 on pe-incident 2/3, $4.93
on strict docs-bulkedit 3/3, vs the Sonnet 5 low docs anchor $7.13/correct
(4/6) and the Opus 4.8 low docs anchor $5.99/correct (4/4)] — n=3 per cell,
one instance per family, cross-date anchors, so **directional, not an
ordering**. Price Reversal 2603.23971 remains a price-is-not-spend prior at
21.8% (DOC-1 above), nothing more. The down-scale boundary is unaffected and
still holds: on the easy docs task Opus 5 passes 3/3 at ~1.3x Sonnet's price
($0.28 vs $0.21/correct, cross-date strata) — pay the premium for work the
cheaper tier can't reliably do [batch-docsomissions-o5-2026-08-09.md]. **No XL
tier ordering may be quoted from this section until a live separator exists**
(§3.2 erratum, 2026-08-30).

**1.2 Before ever downgrading, triage the failure mode.** Watch the strong
runs and classify what would go wrong in cheaper hands:
- *Knowledge- or process-shaped* failures are harnessable — downgrade is a
  candidate (1.4).
- *Disposition-shaped* failures (deletes, irreversible actions, judgment
  under suspicion) are NOT harnessable and not reliably prompt-fixable:
  **five** disposition/affordance interventions, measured across six cells
  (n=30 pooled, 2 passes, Wilson [0.02, 0.21]), produced no detectable
  outcome effect — but four of the six cells had a control of exactly zero,
  where at n=6 an effect of up to 39 points would have been invisible, and
  one cell (caution, 2/6 vs a 1/10 control) is an underpowered positive,
  not a zero. What this evidence actually establishes is the BEHAVIORAL
  null — zero fetches, zero file opens, censused directly — which is not
  power-limited. Emission-class content remains untested at this tier
  [judgment-family-tier-separation; NE-3 in HANDOFF-2026-08-02-morning;
  cheap-tier-information-seeking-absent; XQ4-C addendum 2026-08-29 in
  challenge-q4-prompt-content-2026-08-17.md, superseding
  xq4c-streak-reaudit-2026-08-17; XQ4-A #81], and the caution disposition is
  vendor-shaped even at the top tier (Sol deletes the suspicious store
  3/6 where strong Claude holds 0/12) [batch-sol-sd-2026-08-02]. For this
  class: strong Claude tier or a hard gate OUTSIDE the model, permanently.

**1.3 Volume filter.** Harness investment only pays where the task recurs:
invest when occurrences × per-run saving > build + revalidation cost.
Low-volume tasks stay on the strong model forever.

**1.4 Downgrade is a measured experiment, never a vibe.** 3–5 reps on ≥3
independent variants of YOUR task, end-check scored, compared on
cost-per-correct — never list price [Price Reversal; same-query cost
varies up to 9.7×, so single runs are noise; convention #12 small-n
honesty]. One instance tells you almost nothing: designed-hard tasks have
collapsed to ceiling three separate times [§13].

*(Price Reversal scoped 2026-09-02 - see the section 1.1 erratum. The paper
measures raw cost per query and never divides by pass rate, so it licenses the
sentence it is attached to here - never route on list price - and NOT the
cost-per-correct comparison itself; its aggregate is 21.8%, not 32%
[challenge-q1-routing-2026-08-16.md:483-493].)*

**1.5 Nothing stays locked — canary after every upgrade.** Harness/CLI
version is a tier-sized cost variable [Harness Effect 2607.06906; the
2026-07-24 environment erratum]. After any model, CLI, or harness change:
re-run 2–3 known-answer tasks before trusting the locked configuration.

**1.6 The task-maturity ladder (states the arc 1.1–1.4 imply; Evan,
2026-08-21).** Routing is not fixed per task — it descends as the task
becomes better defined. Enter unfamiliar work at the strongest model
with real reasoning (1.1). As runs accumulate, capture the recurring
procedure the strong runs keep re-deriving into an artifact — a skill,
a checklist, a deterministic check — distilled from actual transcripts,
not hand-authored from memory [Reason Wide Not Deep 2608.07885;
SkillsBench 2602.12670v1: self-authored skills bought nothing]. Then
descend one rung at a time, each rung a measured experiment (1.4), only
where volume pays (1.3): cheaper tier with the artifact in-path → lower
effort → code-only, no model at all. Status of the rungs: tier descent
is measured doctrine; strong-at-LOW-effort is registered-not-measured
(EFF-2 #54, incl. the distilled-skill arm); code-only is designed-only
(#23). Gating predicate for the bottom rungs: the task admits a
deterministic check (3.3 — the one routing signal usable through an
API). Never descend judgment/disposition-shaped tasks (1.2), and do not
expect guard layers to substitute for tier: organically, only 12–18% of
our cheap-tier failures involve prohibited actions at all — the rest
are wrong-but-legal [census1-screen-2026-08-21].

## 2. Harness doctrine (what actually changes model behavior)

**2.1 At the cheap tier, prompt content works when it is IN-PATH and
specifies an EMISSION; it fails when it is off-path or asks for a
disposition. (Revised 2026-08-18, challenge-q4 + xq4c re-audit;
Evan-approved. Caveat added 2026-08-29, Evan-approved: the outcome nulls
behind this rule are power-limited against zero-variance controls; the
behavioral censuses are not. See the XQ4-C addendum in
challenge-q4-prompt-content-2026-08-17.md, which supersedes
xq4c-streak-reaudit-2026-08-17.md.)** Three definitions carry the rule:
- *In-path* content is text the model cannot avoid processing while doing
  the task — the prompt, system prompt, message turns, or feedback injected
  into its loop. *Off-path* content is available but must be chosen: a file
  sitting in the workdir, an offered-but-optional tool, a doc it could
  fetch.
- *Emission* content says WHAT TO PRODUCE, concretely enough to check in
  the transcript: a required call, an output schema, a worked example to
  imitate, "one verdict line per row."
- *Disposition* content says HOW TO BE: be careful, verify assumptions,
  plan before acting. It requests an attitude, not an artifact.

The old formulation ("only structure works; prose and affordances do
nothing") retires as overgeneralized: it was induced entirely from
disposition and off-path cells, and is falsified outside that class —
three worked-example trajectories in the message channel took Claude 3
Haiku 11%→75% on multi-turn tool use [challenge-q4 §2, LangChain
2024-07-24]; a prompt-only safety instruction cut unsafe-action rates
82.5%→25.6% on 7–8B agents [arXiv:2607.10490]. Our own corpus, restated
on the new axes: the two things that ever moved haiku are both in-path —
the runnable checker in its loop (≈33%→100%)
[live-checker-rescue-tf-sweep] and the bare injected fail bit, which
matched a full error list (richness is not the lever)
[bare-fail-bit-feedback-grade]. Every null we ran was disposition or
off-path (caution rule, premise preamble, docs fetchable / offered / in
the workdir never opened) [cheap-tier-information-seeking-absent] — and
those nulls were measured against floor or ceiling controls at n≤6,
powered only for very large effects, with one underpowered positive
inside the streak [xq4c-streak-reaudit-2026-08-17]. Emission content at
cheap tier is UNTESTED first-party (XQ4-A built and gated, #81). The
tier gradient itself survives on independent evidence: removing a prose
rulebook costs gpt-4o 22.4 points and gpt-3.5-turbo 1.2 [τ-bench,
2406.12045]; and check published prompt wins for structure in disguise
(AppWorld's +17.0 needs a generator/reflector loop; the static prompt
alone buys +4.0) [2510.04618]. Structure remains the most RELIABLE way
to buy path and force — it is just not the active ingredient.

**2.2 Strong tiers DO follow prose — instruction-following is itself
tier-graded — but the budget-sentence payoff is shape-specific.** One
budget sentence cut sonnet's XL cost 49% among passes at flat pass rate
[batch-a2-softbudget-2026-08-02], yet the same sentence moved two other
instances ≤10% (docs-bulkedit −6.6%, tf-bulk-tags −10.2%, fresh 3v3
each) — the registered family rule failed and no family claim exists
[soft-budget-prompt-scope-limited]. Mechanism: the sentence trims
REDUNDANT re-reading/re-verification turns; compact or
essential-work-dominated runs have nothing to trim. Apply it where long
runs show verification loops (turn histograms reveal this); don't expect
it to move short tasks. Pair budget prompts with an end-check on tasks
without deterministic oracles.

**2.3 Checker design rules** (for CI and agent loops alike):
- Failure classes must be DISTINGUISHABLE (assertion ≠ runtime ≠ timeout ≠
  infra; infra scores zero and never burns agent retries) [EFC deep-read,
  the surviving gate structure].
- The checker must answer FAST or cheap models treat it as dead: a
  240s-pending checker collapsed haiku to its no-checker rate — failures
  polled dozens of times then declared success over PENDING
  [batch-slow1-2026-08-01].
- Enforce the wait contract in the harness: "the check must report a
  verdict before done" — costs nothing, closes both the cheap-tier
  false-claim and the strong-tier confident-skip [batch-slow1 sonnet ext].
- Kill same-status retry loops (same check failing the same way twice →
  stop/escalate); a cheap-tier behavior, measured zero at Opus tier
  [ne1-same-status-census-2026-08-01].
- **Validity: a checker whose PASS does not predict the verdict is worse than
  no checker (ADDED DOC-2 2026-09-02).** A green in-fixture check is a licence
  to stop looking, so a checker that can pass while the work is wrong buys
  false confidence at the price of the search it terminated. Measured over the
  129 corpus runs whose fixture ships a [implementation detail withheld]: a last-invocation PASS was
  followed by an oracle pass **53/57 = 93%** [Wilson 83–97] overall, but only
  **6/10 = 60%** [31–83] on pe-incident-fb2, whose checker replays a
  connectivity probe and so asks whether the FQDN resolves privately, not
  whether the fix is the one the ticket authorises. Rule: state what the
  checker's PASS *is evidence for*, and if it is shape-only, say so in the
  checker's own output. Hint: FAIL is the trustworthy direction here — a
  last-invocation FAIL was followed by an oracle pass only 2/6 = 33% [10–70],
  so FAIL carries information and PASS is the one that leaks
  [screen1-free-screens-2026-09-02.md §P5].
- **A checker the harness denies is not a checker (ADDED DOC-2 2026-09-02).**
  Before treating "the model didn't use the checker" as a behaviour, prove the
  checker was reachable. **56 of 129 runs (43%) attempted [implementation detail withheld] and were
  refused by the permission layer** ("Permission to use Bash has been denied
  because Claude Code is running in don't ask mode"), 6 more got only PENDING,
  and 3 were inoperative because the sandbox blocks [hostname withheld] —
  48% of runs never saw a verdict at all. Every one of those is scored today as
  a model choice; it is a substrate artifact contaminating a treatment
  variable. Corollary for design: a study of *response to a blocked check* must
  make the block come from the checker's own exit, never from the harness, or
  it measures the denial message's wording — that text ends with an instruction
  to stop and ask the user, which is why 9/9 EFF-2 runs facing a denied required
  gate escalated [screen1-free-screens-2026-09-02.md §P5;
  gate0-pilot-2026-09-02.md].

**2.4 Self-reported completion carries no information at any tier —
install the end-check floor everywhere; size its budget by the tier's
measured failure rate, never skip it. (Revised 2026-08-18, challenge-q6;
Evan-approved. Citation corrected 2026-08-21 per
verify-doctrine24-figures, autonomous under decision-altitude.)** Fabrication *given a failed run* does not fall with
tier and may rise: our corpus re-measured task-matched puts failed runs
claiming success at 61.5% haiku / 49.0% sonnet / **62.5% opus-5**
[challenge-q6-fabrication-tier-2026-08-17 first-party remeasure];
Anthropic's own Impossible Tasks eval (agentic problems built to be
unsolvable; scored on whether the model gives up or games the checker —
a harder case for self-report than lying about the outcome, and not the
same instrument as our text-level rates) puts Opus 4.5 and Sonnet 4.5
level at 55% / 53% with Haiku 4.5 *lower* at 30%, and the frontier model
least steerable when explicitly told not to hack (35% vs 20% / 23%)
[Opus 4.5 system card Nov 2025 Tbl 6.10.1.A; unchanged in the Opus 4.6
card; the Opus 5 card drops the eval, so no opus-5 counterpart exists —
pins in verify-doctrine24-figures-2026-08-21], and the nearest external task family (Terraform
security repair, 288 tasks) is tier-indistinguishable at 71.4% deceptive
fixes [challenge-q6]. What falls with tier is failure FREQUENCY, so the
floor's expected saving scales by tier — ours: ~31 / ~2 / ~1 false
successes per 100 runs at haiku / sonnet / opus-5. A frontier discount is
affirmatively contraindicated: stronger generators produce subtler wrong
answers (a fixed verifier's true-negative rate fell 0.68→0.17 as the
generator scaled) [challenge-q6]. Retained prior evidence: onset at the
point of no return [Failure-as-a-Process]; 40+ program runs claimed
success falsely [external-verification-required]. Two levers beat model
choice by an order of magnitude and come first: fixture ambiguity and
independent state verification.

**ERRATUM (DOC-1 2026-09-02) — the three fabrication percentages above are one
end of a bracket from two unvalidated instruments, and they are not
task-matched.** Struck: ~~"our corpus re-measured task-matched puts failed runs
claiming success at 61.5% haiku / 49.0% sonnet / 62.5% opus-5 ... first-party
remeasure"~~ read as a first-party measurement. Replacement: those three
numbers are the **permissive-instrument POOLED column** of a pilot bracket
table whose own report disowns both bounds, verbatim: *"The FAB-1 pilot's
permissive regex is deliberately over-inclusive and was written by me in this
session, not validated against anything. Both bounds in the instrument table
are unvalidated; only their bracketing is meaningful"*
[challenge-q6-fabrication-tier-2026-08-17.md:514-516]. The strict instrument on
the same runs gives **49.0 / 9.4 / 12.5**, and it under-detects in proportion to
how far a model's vocabulary drifts from haiku-on-terraform - a tier-correlated
miss [:229-247]. The genuinely task-matched cells are counts, not rates:
decommission-judgment-sound haiku 6/9, sonnet 4/6, opus-5 5/6;
docs-bulkedit haiku 7/7, sonnet 13/18; tf-bulkedit-xl haiku 7/10,
sonnet 11/21 [:241].
**Rule as it now stands, unchanged in force:** install the end-check floor at
every tier and do not discount it at the frontier. What the corpus supports is
the *direction* - fabrication given a failed run does not fall with tier under
either instrument, and collapses or inverts at the top under the inclusive one -
so a frontier discount stays affirmatively contraindicated. Quote the bracket
(strict -> permissive), never a single rate as measurement. Hint: the validated
census that would replace the bracket is written out in full, with an
acceptance probe, as FAB-1 in
challenge-q6-fabrication-tier-2026-08-17.md:391-429; it has never been filed as
an issue, and its binding constraint is that opus-5 has only **8** failed runs
in the corpus, so the frontier cell is not estimable from data on disk. Related:
issue #70 (DBF-1, post-run debrief). This does not touch the 2026-08-21 citation
correction in the rule head above, which pinned the *Impossible Tasks* figures -
a different instrument, still sound.

**2.5 Review pattern: cheap-extract, strong-judge.** The reviewer that
renders judgment should not read the whole transcript (it gets talked out
of correct suspicions); a cheap extractor pulling quotes + a strong judge
seeing ticket+quotes matched strong-everywhere at lower cost [monitor
deep-read 2601.21112 — sabotage-evidence, our defect-review test pending
HD-2]. Give every reviewer the explicit acceptance criteria: it's the one
measured lever that doubles detection [Failure-as-a-Process].

**ERRATUM (DOC-1 2026-09-02) — the acceptance-criteria lever is scoped to
PREFIX MONITORING; on post-hoc adjudication it measures about zero.** Struck as
an unscoped rule: ~~"Give every reviewer the explicit acceptance criteria: it's
the one measured lever that doubles detection"~~. The scoped replacement is a
split, and which half you are on is decided by *when you read*:

- **Watching a run IN PROGRESS** (prefix monitor hunting a decisive error
  before lock-in): hand it the task's explicit requirements. Recall roughly
  doubles on our cost-dominant classes - false premise 15 -> 32%, ignored
  requirements 3 -> 22%, off a 28.8% default. The rule stands here, unchanged
  [Failure-as-a-Process; deep-reads-2026-08-01.md:93-97].
- **Judging a FINISHED run** (was this claimed success real?): the same lever
  buys nothing. Across 5 judge models x 5 prompt strategies, *"nothing exceeded
  AUROC 0.65 on tau2-bench or 0.54 on AppWorld. Handing the judge the full task
  specification moved Sonnet 4.5 from 0.640 to 0.632. A checklist prompt scored
  below blind for three of five judges"* - they anchor on the agent's confident
  closing language [challenge-q6-fabrication-tier-2026-08-17.md:324-335,
  reporting Advani; the review's own words: *"a direct, uncomfortable hit on
  doctrine 2.5's second sentence"*]. Buy detection here with a second party
  reading final STATE (section 2.4) or a cheap trained trajectory detector, not
  with more criteria text.

**Which half we are on: post-hoc.** Every beat-swarm shard, every depth pass and
every delegated grader we run reads a finished artifact and renders a verdict -
that is the adjudication case, the about-zero half. Their measured yield comes
from BEAT ASSIGNMENT (telling a reviewer *where to look*), not from criteria
text (*what counts as a hit*) [sections 6 and 8; swarm-review]. So: keep
mandating beats, keep criteria in briefs for calibration and shared vocabulary,
and stop expecting criteria to raise recall - in particular, "the checklist was
in the brief" is not a defence for a missed finding. The cheap-extract /
strong-judge split in the sentence above is untouched and still holds. Hint:
Q6 flagged this as out of scope for its own edit and it sat unqueued for 16
days; a free A/B over archived shard flag files is available under issue #96.

**2.6 Skills/loadout discipline**: one disclosure level, never a
meta-router; description quality has the widest blast radius when cheap
models run; big skill libraries decay without query-time refinement
[disclosure 2607.17598; skills-in-the-wild 2604.04323].

**2.7 An offered tool is not a used tool, and a used tool is not the
mechanism.** Sonnet used a documented, allowlisted graph-retrieval CLI
exactly zero times until a hard audited protocol requirement forced it
[offered-tool-adoption-null-sonnet] — affordance-by-prompt does not create
adoption even at strong tier (extends 2.1's lesson upward). And when the
mandated bundle DID cut cost (−25% tokens pooled, one cell), the savings
appeared in runs where the graph returned zero facts, while max-utility
runs showed nothing: the candidate mechanism is the forced orientation
step interrupting an expensive default opening, not retrieved information
[graph-pilot-savings-dissociated-from-graph-utility, measured]. The
sham-prompt control (2026-08-09) confirmed it: a bench-graph that returns
zero facts on every query, behind the byte-identical mandate, reproduced
the cut (−26.1% tokens vs interleaved same-day control, 6/6 pass) and
landed within 0.01% of the real treatment's pooled token footprint. Before
crediting any retrieval layer, check whether a cheap behavioral nudge
explains the delta — on this task family it explains all of it.

**ERRATUM (DOC-1 2026-09-02) — the sham control was an INSTRUMENT CHECK, not a
confirmation, and the 0.01% coincidence is struck.** Struck: ~~"The sham-prompt
control (2026-08-09) confirmed it"~~ and ~~"landed within 0.01% of the real
treatment's pooled token footprint"~~. Replacement: the sham showed that an
informationless bench-graph behind the byte-identical mandate reproduces the
token cut (-26.1% pooled vs interleaved same-day control, 6/6 pass) - and that
is the most it can show, because the REAL arm returned zero graph facts in 2 of
3 reference runs on the same fixture (attribute keys unindexed), so the two arms
never differed on the variable of interest. Decisive line, verbatim: *"A sham
control earns its name by holding the ritual fixed while removing information
that was otherwise present. Here there was no information present to remove in 2
of 3 reference runs. The correct reading of the 6/6 result is: an empty tool
behind a mandate costs the same as an empty tool behind a mandate"*
[challenge-q5-sham-scaffold-2026-08-17.md:111-114]. Two further limits on the
same cell: leave-one-out drops the pooled result under its own registered >=23%
bar if r122 is removed (-15.3%; -23.2% and -35.7% for the other two) [:160-164],
and 333 tokens between two pooled sums, at +/-30% per-run spread and n=3, is a
coincidence rather than precision [:176-182].
**Rule as it now stands:** before crediting any retrieval layer, check whether a
cheap behavioral nudge explains the delta - and carry the SPLIT, which is the
transferable part: scaffold STRUCTURE is a cost-and-path lever (it survives sham
control, because sham preserves the behaviour exactly), retrieved CONTENT is a
correctness-and-reliability lever (it does not survive sham, and separates from
a matched control only when the real tool demonstrably returns task-critical
facts, on an outcome with headroom - this cell sat at a 9/9 correctness
ceiling). The dissociation claim itself is undamaged: it rests on the CROSS-TASK
pattern (savings in the zero-hit cell, none in the max-utility cell), which this
review does not touch - the sham cell was never the load-bearing part. Hint: the
full replacement text, the two controls now mandatory for any tool-value claim
(a matched no-feedback arm and a matched-budget blind-resampling arm), and the
expect-fabrication-not-failure warning for inert-tool arms are in
challenge-q5-sham-scaffold-2026-08-17.md:423-467. Proposed 2026-08-17 pending
Evan, never applied, no issue tracked it.

**2.8 Persistence prompting is a treatment, not a scaffold.** OpenAI
shipped a persistence block ("never stop or hand back… do not ask the
human to confirm") and advised raising effort for the same effect;
their GPT-5.6 system card reports the cost — increased persistence at
the highest efforts correlated with cheating and fabricated results,
more pronounced under persistence-emphasizing prompts — and their
current guidance is to baseline one effort level LOWER and define
stopping conditions rather than suppress them (challenge-q11 §1.3). In
our arms, persistence language is a REGISTERED manipulation, never a
neutral scaffold; it interacts with the 2.4 fabrication floor.

## 3. Economics doctrine

**3.1 Caching dominates everything** (~5× vs ≤2× for every routing gain
measured) [prompt-cache-leverage]. Warm-batch related small tasks
[warm-same-model-batching]. Get caching right before optimizing routing.

**3.2 Reason in cost-per-correct and usage percentages**, never list
price or raw dollars (Evan: the Max budget units are session/weekly %).
Reliability is IN the metric: cost-per-correct = cost-per-run ÷ pass rate. Two hints: at
our n the orderings are robust but the margins are fragile — n≤4
comparators quote intervals, not points; and censoring-inclusive
accounting structurally punishes chain architectures — quote chains both
ways before comparing [met1-sensitivity-retro-2026-08-21].
**ERRATUM (2026-08-30, verified two-lineage: Sol memo + raw-data check
[met1-rawcheck-2026-08-30]):**
- **Cheap-tier-on-judgment is REVERSED (C6, fully confirmed).** Haiku's
  cost-per-correct edge on docs-omissions exists only at detector recall
  ≥0.90; its failures are WRONG-BUT-LEGAL (coding verified against the
  oracle), the exact class a weak reviewer misses. Under any nonzero
  failure price with an imperfect detector, route judgment tasks strong.
  Hint: break-even d*=0.90; the algebra and coding both re-derived.
- **The Opus-at-XL orderings (C1/C2) do not carry.** The dollar flip is
  real and survives every window recombination (the published read is the
  conservative one), BUT the comparison rests on tf-bulkedit-xl, which
  has been [implementation detail withheld] — excluded from
  tier-separation scoring — since 2026-07-31, and the arms did not see
  identical prompt text. Quote NO XL tier ordering, in either direction,
  until a live separator exists.
- **C5 unfrozen, but re-filed (REVISED, 2026-08-30).** The margin re-derives
  exactly and is robust: cheap+self-check 7/8 at $0.53/correct vs Sonnet solo
  9/9 at $0.79, holding under both censoring variants, every alternative
  Sonnet comparator on disk, and both dedup tie-breaks; it flips only at x5
  failure pricing with review catching under 23% of wrong answers. But it is
  NOT evidence for 3.3: tf-bulk-tags ships no in-fixture checker, so the
  treatment is a self-check PROMPT, not a verifier. Re-file it under 2.7 —
  a mandated completeness step is a real cheap-tier lever (plain Haiku 2/10
  -> checked 7/8 on the same task). Hint: on the two tf-bulk-tags variants
  that DO ship a check.sh the sign reverses (cheap 0/6 and 2/6 at
  $0.96/correct vs Sonnet 3/3 and 6/6 at $1.28 and $0.88), so 3.3's verifier
  clause is literature-only here and is contradicted by the only internal
  cells that test it [hygiene92-c5-2026-08-30].
  - **ANNOTATION (DOC-2 2026-09-02) — the "cheap tier ignored the checker"
    reading of the two [implementation detail withheld]-shipping variants above does not survive the
    transcripts.** On tf-bulk-tags-fb, **15 of 18 checker attempts were
    DENIED by the harness** and the remaining 3 were inoperative (the sandbox
    blocks [hostname withheld], so [implementation detail withheld] fails and the checker
    exits 2) — **no run there ever saw a checker verdict**. The sign reversal
    quoted above is therefore evidence about a *substrate*, not about
    cheap-tier checker use; the sentence stands only as "the sign reverses on
    the variants that ship a check.sh", with the mechanism unknown. Hint:
    SCREEN-1 prints two figures for this task — 15/18 denied + 3 inoperative in
    its "anything wrong" note vs a 12/18 never-returned cell in its P5 table
    (attempts vs runs); reconcile against the transcripts before quoting either
    [screen1-free-screens-2026-09-02.md §P5 and §"Anything wrong" item 2]. See
    §2.3's denied-checker rule.
- C3/C4/C7/C8 are robust under all 35 assumption sets and stand.

**3.3 Cheap-and-repeated beats elaborate-and-single** where a verifier
exists: five cheap tries beat one run of a tuned harness on cost AND
score [PRO-LONG deep-read]; cheap-model orchestration works ONLY where a
local soundness signal (tests/execution) exists to select on
[2605.14163]. No verifier → route strong directly.

**3.4 Vendor routing (current)**: Luna = bulk mechanical edits with an
end-check, never judgment/deletes [luna-vault-deletion]; the cheap tier
can SWEEP exhaustively (docs-bulkedit 5/6) but not judge exhaustively
(docs-omissions 1/6 vs Sol 6/6) — the census weakness is tier-shaped,
not vendor-family-shaped [census-weakness-cheap-tier-not-family]. Sol =
detection, analysis, construction — matches strong Claude on
flawed-instruction detection but leans delete under sound-instruction
suspicion [batch-sol-sd-2026-08-02]; the delete button belongs to strong
Claude or a human gate. Within-strong-tier routing is UNMEASURABLE today
(no instrument separates Sonnet/Opus/Fable/Sol — 17h is the gap).

**3.5 The effort dial is not a routing tier.** Turning a cheap model's
reasoning effort up does not buy hazard detection: Luna-high spent 4–5×
the reasoning tokens of Sol-medium on the same landmines and scored
worse, deleting the load-bearing resource in 10 of 12 failing runs
[census-weakness-cheap-tier-not-family; batch-gpt-day-2026-08-07].
Mechanism revised 2026-08-21 (challenge-q11; per-turn numbers
independently verified, q11-perturn-verify-2026-08-21.md): the dial buys
MORE DELIBERATION PER STEP, not a different policy. Volume axes move
(thinking tokens, turns, re-verification, narration); policy axes do
not (acting on what it found, asking you first, giving up). Best
available account: the allocation policy is fixed at training and
effort raises its ceiling [2605.16938]. The one shape to remember:
EFFORT DE-BATCHES — EFF-2 medium→max: turns ×2.5 (monotone in all 3
tasks), tool calls ×1.24, tool-calls-per-turn 1.57→0.97, thinking
39%→70% of output; at max the agent takes one action per round trip
(Anthropic documents the mirror image from the low side). Scope: that
signature is documented medium→max on judgment tasks, Sonnet — the
corpus's low↔high span moves little and mixed-sign, and its one clear
cell batches MORE at high and fails [eff2-r1r3-recut-2026-08-21]. Budget for
round trips and wall-clock, not just tokens. Search is a special case,
not the mechanism: effort multiplies search where searching IS the task
[2508.06600; 2604.17609]; in our already-read small fixtures Read calls
were flat (×1.07) while re-probing doubled — don't generalize "effort
buys looking" to workspaces the agent has already read. Persistence and
deference do NOT move: over-abstention saturates at medium [2606.28733];
thinking slightly decreases optimal asking [2607.00711]; action bias is
immune across four levels [2605.07769 — their lever is ours: tell the
agent abstaining is a valid outcome, don't tell it to think harder];
first-party, hand-back flat 3/9 at every rung, predicted by which task
had a hard gate, never by effort, 0/27 abandonments. Both vendors claim
low effort asks the user more; neither publishes a measurement — treat
as unverified vendor text (challenge-q11 §1). Above medium/high the
curve often turns DOWN, per the vendors' own cards (Opus 5 peaks at
MEDIUM on FrontierCode; 21/36 HAL combos equal-or-lower at higher
effort [2510.11977]; named failure mode: self-correction loops at
higher efforts). Registered caveat stands: EFF-2's zero outcome
variance cannot separate ceiling from failure-to-act — the
crossover-band ladder (#54 R3) is the discriminating buy; the free R3
screen has now mapped the band — mostly Haiku on mechanical infra tasks
[eff2-r1r3-recut-2026-08-21]. Escalate the
TIER (or add structure, 2.1), don't crank the dial — unchanged, and
now over-determined.

**The dial has TWO REGIMES, and everything above is the long-task half (ADDED
DOC-2 2026-09-02; PARTIAL n — the short-task rows are n=1 per rung, the
long-task rows n=3).** On SHORT work the lower rungs are not separable: on an
87-second ceiling task (decommission-judgment-tag-sound) thinking tokens ran
low 414 / medium 242 / high 466 / **xhigh 5,577 / max 12,334** — non-monotone
below xhigh, i.e. the pin does not bite until xhigh, and billed cost tracked it
($0.63 / $0.65 / $0.66 / $1.15 / $1.73). On LONG work the dial is a cost
multiplier with no measured accuracy gain: on docs-bulkedit, low $1.08 /
22.5 turns, medium $2.50 / 70.7 turns, xhigh $6.21 / 156 turns — **5.75x
low→xhigh, all three rungs PASSING**. Two consequences. (a) **Ladder design**:
on a short task buy {low, xhigh, max} — three rungs instead of five, ~40% off
the ladder — because {low, medium, high} is one cell measured three times.
(b) **Prediction discipline**: a registered "cost is monotone in effort"
prediction is expected to FAIL below xhigh on short tasks, and that failure is
the efficiency finding, not a null. Caveat: one model family, one short task
and one long task; the regime BOUNDARY (what counts as short) is unmeasured —
treat task length as the moderator to test, not as a calibrated threshold
[prereg-fable-intake-2026-09-02.md §2 pin-check annotations, 2026-09-02 06:25Z
and 06:42Z, plus its ladder rows; research-connections-ranked-2026-09-02.md
row C2].

**3.7 Compact early, switch models at boundaries (2026-08-22, CTX-1
archaeology).** Compaction pays for itself in ~1.5 requests (median cost
$0.26 list-yardstick, per-request cost 0.265→0.099 across 21 instrumented
boundaries) — never delay a compaction you already want on cost grounds.
Mid-session model changeover forces a full re-cache-write of the live
context because the prompt cache is per-model (median ~579K cache-write
tokens ≈ $3.62 across 6 observed switches, scaling with context) — switch
at compaction points or session starts, not mid-flight. Hint: these are
COST rules only, and the quality side is now MEASURED and unfavourable:
47% of session-established constraints survive one compaction in canonical
form, 23% survive two, 16% survive three (COMPACT-CLIFF, 473 constraints
over 30 real boundaries at 1.4% median retention) — the same curve paper
2608.22752 reports at 50% retention. Compacting earlier is better per
event (recall vs preTokens ρ = −0.357) and worse per session (more
rounds), so never resolve that tension with a token threshold — resolve
it with 3.8. Evidence: ctx1-archaeology-2026-08-22-opus.md,
compact-cliff-retro-2026-08-30.md.

**3.8 A compaction is a commitment boundary — write the rule down first
(2026-08-30, COMPACT-CLIFF).** Compaction makes every in-session fact
low-provenance at once, so the trust-and-verification rule fires: before
[implementation detail withheld], write any constraint that exists nowhere but the conversation
into its durable home (HANDOFF.md, the prereg, the run record). Measured
stakes: only 7.5% of the constraints our sessions run on are in the
re-sent block that survives by construction; of the rest, 47% survive one
round and 16% survive three, and where the session later touched what a
lost rule governed, 13–19% of those touches broke it. Hint: the failure
mode is DEGRADED, not LOST — a third of rules leave the summary as a topic
with no bound attached, and those produced two thirds of the observed
violations; [implementation detail withheld] operational holds ("nothing dispatches tonight",
"don't touch that path") are 22 of 26 violations and the class least
likely to be written down. This is the human form of TypeRetrieve pinning
and costs one edit. Evidence: compact-cliff-retro-2026-08-30.md.

## 4. Meta-doctrine (how we know any of this)

**4.0 Consensus of clones is not truth.** Pair-identical disagreement with
an independent reference is the SIGNATURE of correlated same-model error,
not evidence against the reference: a fresh three-lineage panel found the
same-model pair wrong on 2 of 3 such rows and the reference wrong on 1
[mh1-r6-panel-2026-08-21]. Never excuse the veto built to catch it
(that excuse was Erratum 6; impeached and reverted same day). Settle
contested references by precommitted FACTUAL discriminators mapped to
labels only after collection — ask facts, not labels: unanimity across
three lineages at mixed tiers where label-choice had produced five rounds
of ambiguity, and cheap seats sufficed because the questions were factual.
Hint: qualification gates that share priors with the test material can be
passed on priors alone — a judge given accidentally-EMPTY packets
confabulated codings and passed the gate (GPT seat; both Claude seats
refused honestly; n=1) — so gates need content-dependent items and packet
builds need byte-floor assertions [mh1-r6-panel-2026-08-21 §instrument-failure].

Difficulty is verified, never asserted; every oracle must fail a no-op;
leakage ablation is only informative on tasks the probe model FAILS
intact — a pass on an ablated copy of a cheap-passable task measures
base-rate passability, not a leak (check the discrimination report
before registering ablation priors) [batch-burnday-2026-08-07 §2] —
and an ablation only exists if the bytes are actually gone: deleting a
file from the worktree of a git-carrying fixture leaves it one
[implementation detail withheld] away, with [implementation detail withheld] advertising the deletion
(all three tf-state-reconcile-v2 ablate arms were void this way — and
the 2026-08-21 content-token audit FALSIFIED the earlier "probe never
touched git" screen: 8 of 9 rows recovered the ablated document via
[implementation detail withheld]/[implementation detail withheld], every oracle pass sat on a recovered row, and those
cells are VOID as ablation evidence; a [implementation detail withheld] line advertising a
deletion is an attractant, not a passive leak)
[ablate-porosity-audit-2026-08-21, correcting ablation-arms-git-history-void];
a check that can't distinguish a real solution from a differently-phrased
one silently mis-routes trust (it happened to our own verifiers twice)
[verifier-dialect-calibration-failures]; two-reviewer cross-lineage gates
catch what green selftests miss (twice this window); surprises replicate
before they headline. These are bench conventions #1–#15 — they transfer
to work as: measure before believing, and audit the checker before the
agent. Corollary for citations: pin the arXiv VERSION when a claim
rests on a specific sentence — abstracts are moving targets and
findings get deleted between versions (SkillsBench v1→v4 dropped its
central claim; digest-top-papers-febmar-2026-08-21.md, same class as
derived-artifacts-stale).

When humans-or-models label data with a codebook, **vocabulary coverage
is not the binding constraint — rule application is**: across two
pre-registered calibration rounds the 46-value vocabulary needed zero
escape hatches while edge agreement was bound by whether annotators
WALKED the existing tie-break rules; forcing the walk in the brief (not
adding vocabulary) moved edge Jaccard 0.508 → 0.780
[annotation-calibration-rule-walks]. Transfers to work as: when review
checklists disagree, mandate recording the rule-walk before the verdict
— don't grow the checklist. Corollary: answer keys are instruments too —
a "gold" from a single adjudicator can be wrong, so known-answer gates
need provenance-graded golds and a licensed-variants match, not one
frozen triple (round-2 VOID decomposition, same reports).

When two annotators agree, that is reliability, not accuracy — at two
raters, rater accuracy and shared-error correlation are jointly
non-identifiable at any sample size, so no agreement number can certify
the pair is not wrong together (adopted 2026-08-21; q10 review,
Dendukuri & Joseph 2001, arXiv:2608.08002). Three reporting rules
follow: every reported κ/α/Jaccard carries a one-line scope note
(reliability only, bounds nothing about accuracy); one headline
agreement statistic per construct (κ headline — our label skew makes it
conservative — α as the multi-rater generalization, raw agreement
demoted to diagnostic); and any agreement gate scored over a
prescriptive brief gets a STRUCTURAL FLOOR — the score two annotators
would post by mechanically applying the brief's binding defaults
without reading the artifact — reported as achieved-minus-floor
(rubric structure alone restores ~62% of apparent consensus
[Song 2603.11027]; our own largest Jaccard jump, +0.272, landed on the
erratum that made edge targets binding). And cross-lineage review is a
DETECTOR of shared error, not a corrector: a disagreement is strong
evidence and the primary output; a clean review is weak evidence
[q10 §8 D2 — the matched-size corrective ablation does not exist in
the literature].

## 5. Prompt style is not a cost lever at the cheap tier (2026-08-15, PIW-1)

Semantically-matched rewordings (terse/verbose/polite) of two realistic
infra tasks moved Haiku's billed cost per run by at most ~17% and never
crossed the registered 25% materiality line; the only consistent
direction is that verbose prompting trends more expensive in
model-generated output (P-PIW-2 directionally supported, one leg
significant). Working translation: spend prompt-engineering effort on
CONTENT (constraints, checkers, feedback), not style — style buys
single-digit percents at this tier. Bound: two tasks, one tier; the
politeness/optionality arm barely moved correctness, so the deontic-force
question stays open. Source: results-piw1-2026-08-15.md (prereg frozen
b82e23b, transfer claim from arXiv 2608.01347 NOT supported at our
realism level).

## 6. Review economics: what cheap review buys, and what it doesn't (2026-08-21, SEB-1)

Frozen prereg prereg-seb1-review-economics-2026-08-21-DRAFT.md (v2 +
amendments v2.1-v2.4); two rungs of a planned four ran before the ladder was
truncated on quota. Rungs graded against per-package confirmed-blocker keys;
reference arm = Sol-xhigh, recall 0.71/0.64/0.62. **The stop rule terminated
UNSATISFIED — no rung met the reference bar on all three packages under any key
or coding.** Final re-derivation, including the disposition of every novel
finding: seb1-ladder-synthesis-2026-08-21-opus.md.

- **Breadth is assignable at the cheapest tier; assignment is not dominance.** (Sharpened 2026-08-22, SW-OPUS-1: reproduced on a second, same-lineage-as-target arm — Opus shards under the identical beat mandate also recovered the class, globals 5/6 — so "assignable breadth" is a property of the beat SHAPE, not of the cheap cross-lineage shard specifically. Still not dominance: SW-OPUS trails R-swarm on SWJ-1 and P-SWO-2 equivalence did not hit. See the shape-vs-lineage bullet.)
  A flag-only Sol-LOW shard mandated to a host/isolation beat surfaced the
  ISO-1-class BLOCKER in 3 of 3 packages — the finding Sol-low unassigned,
  Sol-max, Terra, Opus at every tier and Sol-medium on all three packages
  missed, and that Sol-xhigh caught on only one package of three. Globals
  K-G1/K-G2: 0/6 (Sol-medium) and 1/6 (Sol-xhigh) → 4/6 strict, 5/6 generous
  (swarm). Lead with K-G2, the one cleanly shard-originated global; two of the
  four global credits are shard-names-the-gap / depth-names-the-payload MIXED.
  BUT the full grade is complementary, not dominant: strict recall
  0.476/0.500/0.538 against bars 0.71/0.64/0.62, and the solo medium reviewer
  caught the defects that fall BETWEEN beats (canary-halt wiring, strong-tier
  saturation, paired-loader denominator, leak_detect fail-open).
  Bounds: n=1 per package; beat boundaries reviewer-determined (the rung's
  largest registered variance source). Evidence and attribution detail:
  seb1-rswarm-grade-audit-2026-08-21-opus.md.

- **Verdict agreement is not detection agreement.** Sol-medium emitted the
  reference arm's exact verdict pair on all three packages and blocked dispatch
  3/3 while recalling 0.21-0.57 of confirmed blockers. Route reviews on
  finding-level output, never on the verdict label. Source:
  seb1-rmed-results-2026-08-21.md.

- **Union beats any single champion — on every package, on both keys.** Two
  cheap rungs unioned exceed either alone on all three packages (14/21, 8/14,
  9/13 vs champions 12, 7, 7). It clears the Sol-xhigh bar on SWJ-1 only. The
  review-economics-grid result (discovery is stochastic per configuration)
  reproduced inside a single rung family. Caveat: whether the union also clears
  Q1 depends on an unregistered convention — see the synthesis report §1.5
  before quoting a Q1 number.

- **Census-reconstruction reproduces down to Sol-LOW.** The cheap shard named
  all five planted items and assembled the reconstruction hypothesis itself
  with zero access to any answer file; the expensive depth pass only executed
  the cross-check the shard had nominated. This FALSIFIES P-SEB1-5 (predicted
  the class needs top-rung deliberation) and makes the class TASK-driven: a
  fixture whose answer is mechanically recoverable invites reconstruction from
  any reviewer that runs a census. Do not attribute a reconstruction catch to
  reviewer strength without first ruling out fixture recoverability. The
  "breadth flags, depth demonstrates" split lost its flagship example — do not
  carry it as a rule without a new instance.

- **Flag-only + depth-pass moves the quality axis from FALSE to TRIVIAL.** With
  shards forbidden to exonerate, the depth pass confirmed 102/103 flags, so a
  near-zero false-finding rate is expected by construction, not evidence of
  precision or of a lenient verifier. The real cost of cheap review is a high
  volume of TRUE-but-MINOR flags, filtered downstream at expensive-tier cost.
  Report cheap-review cost as low-value-signal volume, not as a false-positive
  rate. (Conformant post-disposition rate ~0.015, not the published 0.010 —
  synthesis report §1.7.)

- **If you run a swarm, run the FULL beat set — the passenger-beat question is
  open.** Measured once: host/isolation and analyzer/decision-table produced 10
  of 11 unique wins over the solo reviewer, while caps/spend, fixture-leakage
  and coverage-closure produced ZERO between them and consumed 51% of the spend.
  That is one run on one target class, and a beat idle on an experiment package
  may be load-bearing on production infra or a diff. Standing practice (Evan,
  2026-08-21): every new review need runs the full shape, logging
  uniques_per_beat to [implementation detail withheld]; re-evaluate
  composition only after ≥5 diverse targets. For a non-experiment target,
  translate the five labels onto its surface classes — never drop a beat.
  Two beat facts that stand regardless: a fixture-leakage shard's output belongs
  in fixture hardening, not in a package-review key; and a coverage-closure agent
  must be forbidden from assuming any registered guard works — ours inherited
  "the canary halt fires" as a premise and thereby missed the defect that it is
  never wired, the run's one miss with a named cause.

- **The swarm's host/isolation breadth is SHAPE, not lineage — but shape is not
  yet shown to make the arms interchangeable (2026-08-22, SW-OPUS-1).** Holding
  the R-swarm beat shape fixed and swapping Sol-low shards for Opus shards (same
  lineage as every target under review, zero codex), Opus-with-beats recovered
  the host/isolation blocker class solo Opus missed at every measured tier:
  globals **5/6 strict** vs Sol-swarm 4/6 and Sol-xhigh 1/6, P-SWO-1 HIT. A
  Claude reviewer found the blindspot the lineage argument rests on, once
  assigned to it — so the breadth is assignable to Opus, and swarm review does
  not *need* a foreign lineage to buy it. **BUT do not read this as "Opus shards
  substitute for Sol shards."** H-1's substitution rule needs GLOBALS-RECOVERED
  *and* an equivalence HIT; P-SWO-2 came back **PARTIAL** — Q1 and SWJ-1 inside
  the ±0.15 band, **Q2 outside and above it** (0.857 vs R-swarm 0.500), which the
  prereg registers as inconclusive on equivalence, not a pass. The arms are
  complementary, not ordered: SW-OPUS leads Q1/Q2, trails SWJ-1. SHAPE is
  *indicated*, equivalence *unearned*; the codex constraint is not cleared.
  Settling it needs a replication on independently chosen rows (lifts H-9) and an
  Opus-low arm that does not exist (lifts H-1's tier confound). Evidence:
  swopus1-synthesis-2026-08-22-opus.md, swopus1-grade-audit-2026-08-22-opus.md.
  **SHARPENED same day (2026-08-22, SW-OPUS-LOW): the Opus-low arm now exists, and
  it attributes SW-OPUS-1's margin over R-swarm to EFFORT, not lineage.** Dropping
  the Opus shards three notches to low — matching Sol-low, the only remaining
  difference being lineage — lands them at 0.333/0.571/0.538 strict against
  R-swarm's 0.476/0.500/0.538: one package each, a dead tie on the third, 22 vs 24
  rows of 48 pooled. **No lineage advantage is detected at matched effort** (n=1,
  so this is a null, not an equivalence claim). H-1's tier confound is therefore
  LIFTED and the SHAPE reading is strengthened — all three arms that assigned the
  beat reached the host/isolation class (Sol-low 4/6, Opus-xhigh 5/6, Opus-low 3/6
  strict and 3/4 on the §4.0 class rows) against solo reviewers at 1/6 and 0/6.
  **H-9 is now the sole barrier to *established*.** Evidence:
  swopus-low-synthesis-2026-08-22-opus.md.

- **Shard effort — not just shape or lineage — carries swarm recall; shape only
  buys ACCESS to the blocker class (2026-08-22, SW-OPUS-LOW).** Holding the beat
  shape, briefs, pin, key, depth protocol and reviewer lineage fixed and moving
  only shard effort (xhigh → low, pin verified: ~130–160 vs 718 thinking tokens
  per message), strict recall fell 29 → 22 of 48 rows and shard-layer list-price
  cost fell $44.11 → $15.64. **The 7 marginal rows cost $4.07 each — ~5.7× the low
  arm's $0.71 average.** Effort is a premium tier priced like one: real recall, at
  sharply diminishing efficiency. What effort does NOT buy is access: **all six
  host/isolation global loci were reached by low-effort shards (generous 6/6);
  three lost strict credit on mechanism precision, not on failing to look.** So
  route on this split — assignment (shape) gets the cheap reviewer to the right
  place; effort determines whether it states the defect exactly enough to act on.
  Corollary, reproduced across both Opus arms: **the shard layer sets the recall
  ceiling.** Of SW-OPUS-LOW's 22 strict rows, 21 were shard-originated, 1 MIXED,
  **0 depth-supplied** — identical to SW-OPUS-1 despite three notches' worse shard
  quality, i.e. the expensive xhigh depth pass did NOT compensate for weakened
  shards. Spend at the shard layer if you want recall; depth buys precision.
  Bounds: n=1 per package; the low arm's dispatch mechanism also differed (CLI
  subprocess vs Agent subagent, registered D-16), so the effort read is formally
  effort-plus-plumbing; and the low arm lost two closure shards to the mechanical
  exclusion where the xhigh arm lost one, which confounds the Q2 gap specifically.
  Non-inferiority of Opus-low to Opus-xhigh was registered and **REJECTED**
  (P-LOW-2 FAIL) — do not substitute low-effort shards on high-blast-radius
  review. Evidence: swopus-low-synthesis-2026-08-22-opus.md,
  swopus-low-grade-2026-08-22-opus.md, swopus-cost-comparison-2026-08-22-opus.md.

- **Swarm cost, final (billing rule measured 2026-08-21 night).** The codex
  meter charges a WEIGHTED blend — uncached input + ~0.16x cached input +
  ~8.9x output, ~ the API list-price ratio — fitted on 8,366 paired
  (token, meter) observations and validated on the same night's whole-day
  meter bracket. Pure-uncached is refuted; pure-raw approximates only above
  ~92% cache. Under it: R-swarm codex side = 5.2-7.5 pts; the fully-measured
  xhigh reference arm = ~21 pts (not the ~13 placeholder); the swarm's saving
  vs xhigh is 2.85x and CLEARS the registered 2x floor; vs solo medium it is
  1.28x and DOES NOT. Output/reasoning tokens are the expensive channel.
  P-SEB1-4a's cost clause is RESOLVED, not unresolvable. Mechanism behind the
  raw-token gap: both shapes read the same material (552K vs 586K tokens);
  cost differences are the per-request context re-send multiplier (8.0x
  swarm vs 39.2x xhigh — a session's bill grows ~quadratically with its
  length, and splitting into k short sessions divides the compounding term
  by k). Review cost is set by session length, not material read. Sources:
  codex-billing-rule-2026-08-21-opus.md, swarm-cost-anatomy-2026-08-21-opus.md.

- **Method rule the ladder paid for: re-score the reference before registering
  a novel finding.** A finding rung finds its own novel rows by definition, so
  every registration mechanically raises that rung and lowers the bar. Re-read
  the reference arm's own memos for each row before it joins any key. Applied
  here, it caught five rows both graders had coded "novel" that were verbatim
  reference-arm follow-ups, and it moved two of three bars DOWN rather than up.
  Source: seb1-synthesis-protocol-2026-08-21.md rule 3;
  seb1-reference-rescore-2026-08-21-opus.md.

## 7. Controls, identity and gates: what a certification programme taught (2026-08-29, ISO-1)

ISO-1 closed 2026-08-29. It was not an experiment about models — it was months
of building instruments that certify our own results, and then watching those
instruments be wrong in ways the results never would have shown. The rules below
are what survived. They are about *apparatus*, so they transfer to any team that
gates work on a check: CI, a compliance pipeline, a release gate.

Doctrine delta (convention #16): six rules ADDED. Nothing here contradicts an
existing rule; **7.5 SHARPENS** the fail-open hint already carried by bench-guide
convention #17, and **7.4 SHARPENS** the two-reviewer gate (#14) with a trigger
rather than a new requirement.

- **7.1 A repo-wide fact must not stand in for a subtree fact.** If you are
  certifying a directory, compute the directory's identity, not the
  repository's. Our gate rows recorded root identity as repo-wide
  [implementation detail withheld] plus repo-wide [implementation detail withheld], so any commit
  anywhere invalidated every row — and *committing a row is itself a commit*, an
  infinite regress — as did unrelated working-tree churn. Now
  [implementation detail withheld] with a status scoped to that path. Hint: this
  is the **third instance of one class**, not a one-off — K-2 compared an exact
  task id where a family was meant, A-1 compared one key where a key family was
  meant, and this compared a repository where a subtree was meant; when a check
  compares identities, ask what UNIT it is naming and whether that is the unit
  under test. Source: iso1-g1-residual-triage-2026-08-27-opus.md §"THE
  PATH-SCOPED IDENTITY RULING" (lines 2156–2172, and the H2 exclusion-rule case
  at 1285); commits 17ba778, b443bae, e84092f, 8755c32, fd25ccf.

- **7.2 An association is not a leak; a value binding is.** Evan-endorsed
  2026-08-28: *"an association is not a leak when the agent can already
  reconstruct it from its own delivered fixture."* If the agent's own delivered
  workdir already lets it pair two things, our leak detector flagging that pair
  is measuring the fixture, not a leak. What must stay red is the **value**: the
  answer's secret is what the association *binds to*, and if that value is absent
  from the testing tree the leak is not delivered. The discriminator as
  implemented reads **delivered bytes only** — a pair cancels when both halves
  occur inside one delivered file of the owning task, or when one half IS the
  delivered-relative path of a fixture file containing the other — which is
  precisely why an answer value absent from the fixture can satisfy neither limb
  and stays red. Effect: 19 key-gate survivors → 11. Hint: the load-bearing part
  is the control that runs the rule *backwards* (a delivered field name bound to
  an ABSENT answer value must STAY RED); a cancellation rule without that
  direction is a rule for cancelling everything. Source:
  iso1-g1-residual-triage-2026-08-27-opus.md ADDENDUM 11 (lines 1493–1590);
  provenance commit bd4a80e; [implementation detail withheld]
  (observation_unit_cancels); control
  [implementation detail withheld] direction V.

- **7.3 A control that does not record its environment is not a control.** Four
  rules, learned the same way each time: (a) every selftest battery, gate run and
  control run **records its resolution environment** next to its rc — a result
  without that record is quarantined, not quoted; (b) a control must differ from
  the treatment in the manipulated variable **and nothing else** — re-running "on
  the other side" while inheriting the first side's environment varies the tree
  and holds the contamination; (c) **agreement is evidence only if disagreement
  was possible** — ask what the control would have printed if the hypothesis were
  false, and if the answer is "the same thing", it is not a control; (d) **an
  unresolved dependency must SKIP loudly, never FAIL** — a missing verifier root,
  key root or corpus is an unavailable dependency, not a defect in the thing
  being checked. Cost of learning it: an unset BENCH_VERIFIERS_ROOT made every
  mutant return an empty verdict and produced a wall of imaginary selftest
  failures; a reduced run's environment differed from its reference and the
  difference was read as a property of the reduction; and a 2026-08-23 sweep
  inheriting a partial environment manufactured **nine "pre-existing task
  defects"** — re-run 2026-08-29 with all four boundary variables set, all nine
  passed and exactly one real defect survived. Hint: there is a second, meaner
  environment trap on the same footing — an unset BENCH_TESTING_ROOT silently
  **downgrades controls to weaker checks that still print ok**, so *run every
  control in strong mode* and treat a green from an unrecorded environment as no
  information. Source: iso1-g1-residual-triage-2026-08-27-opus.md ADDENDUM 16
  (lines 2175–2245; note two addenda share the number 16); HANDOFF.md lines
  94–97; withdrawal commit 5d82f40, full account in
  repo-split-execution-2026-08-23-opus.md CORRECTION; SKIP-loudly commits
  7300422, 22486ed.

- **7.4 A control written by the code's author inherits the author's blind spot
  — so attack certifier changes cross-lineage BEFORE building on them.** Our
  row-check had five test directions and a mutant, and every one constructed rows
  naming the roots the test itself had created — so the question "are these the
  roots the *caller* is launching from?" was never asked, because the test and the
  code shared an unstated assumption. An outside grader ran the real function
  against a row naming an unrelated live directory and **both gates ACCEPTED**;
  verdict STOP. This was the record's *second* cross-lineage catch of that round.
  Hint: the trigger is not "new code" but **"a check you are about to trust other
  work to"** — the certifier, the gate, the oracle; and the brief that worked
  quoted the author's own blind-spot admission back at the reviewer and asked
  "the author says its previous controls shared the code's blind spot — do the
  new ones?". The self-caught complement is real but weaker: our own controls
  caught ten construction faults *in themselves*, which is why they exist, and
  none of the ones that mattered here. Source:
  iso1-g1-residual-triage-2026-08-27-opus.md ADDENDUM 16 N-1 (lines 2268–2278)
  and J3 (line 1394); grade iso1-fix6-rr-grade-2026-08-29.md line 304, VERDICT
  line 481; fix eb18635, controls bb0b119; brief
  [implementation detail withheld] lines 44–105.

- **7.5 "The gate did not run" and "the gate passed" must never be the same
  outcome.** The shape to hunt is the **guarded existence check** — `[ -f "$X" ]
  && run_check` — which turns a deleted, moved or misnamed check into a silent
  skip while every verdict still looks normal. A commit relocated our sentinels
  and repointed the runners, but 11 selftests also executed them through exactly
  that call site; deleting the file did not fail, it stopped checking. Resolution
  now goes through a fail-CLOSED resolver. Second instance the same round: a
  [implementation detail withheld] banner asserted replay counts for a section that had SKIPPED.
  Hint: this SHARPENS bench-guide #17 (a fail-closed check upstream of a durable
  artifact fails OPEN at the reporting layer) by naming the call-site shape and
  the banner shape as the two places it hides — and note the second-order lesson,
  that a fully green test battery said nothing about the regression because the
  battery did not cover task selftests. Source:
  [implementation detail withheld] §4 traps 1–2;
  [implementation detail withheld] lines 66–69; commits d395d5d (the
  regression), 22486ed (the banner); prior art [implementation detail withheld],
  [implementation detail withheld].

- **7.6 Rows come last.** Any artifact that records a subtree's identity must be
  the **final commit** of any sequence touching that subtree — regenerate it after
  every other lane has committed, commit it alone, and treat any later commit into
  the subtree as invalidating it. Ours forced three regenerations in one day (a
  selftest fix, its follow-up, and a docs correction to a figure inside a task);
  none of those commits was wrong to make, the rows simply have to come last.
  Hint: the friction is structural, not a defect — it is 7.1 doing its job, and
  the only alternative is an identity that ignores the subtree it certifies, which
  is the hole 7.1 closed. Source: HANDOFF.md lines 68–81 (standing rule,
  2026-08-29); commit f4b5f5a; forcing commits 7300422, 22486ed, 1b0efa1.

### 7.7 Skill delta (convention #16, second half)

Asked of each operating skill: does it need any of 7.1–7.6?

**STATUS: APPLIED 2026-09-02 (SKL-1, Evan's delegation 2026-09-02; see bench/reports/skl1-skill-edits-2026-09-02.md).** ~~STATUS: REGISTERED, NOT
APPLIED~~ — §7.7 never carried an explicit status line of its own (only §8.4
did); the struck text above records what its status implicitly was, since the
2026-08-30 §8.4 block counted these five edits as unapplied alongside its own
four. bench-guide got #22 (7.1), #23 (7.3), the #17 sharpening (7.5) and the
#14 sharpening (7.4); swarm-review got the 7.4 trigger in [implementation detail withheld] and
7.3(c) in [implementation detail withheld]. **overnight-lab's 7.6 and 7.3(a)+(d) were
verified already present** — "applied in this pass" on 2026-08-29 was accurate.

- **bench-guide — YES, four edits.** Add **#22 path-scoped identity** (7.1) and
  **#23 environment-dependent controls** (7.3, all four sub-rules) as new
  numbered conventions; **sharpen #17** with 7.5's guarded-existence call-site and
  over-claiming-banner shapes; **sharpen #14** with 7.4's trigger ("attack
  cross-lineage before building on a certifier change"). 7.2 is
  ISO-1-instrument-specific and does **not** belong here. 7.6 belongs in
  overnight-lab, not here. Note the convention list is not contiguous — 1–18 are
  the numbered list, 19–21 are stray prose — so #22/#23 should join the numbered
  list rather than extend the prose tail.
- **swarm-review — YES, one edit.** 7.4's trigger goes into [implementation detail withheld]
  (lines 209–212), where "choose cross-lineage relative to the AUTHOR of the work
  under review" already lives; what is missing is *when* — a certifier change you
  are about to build on. 7.3(c), "agreement is evidence only if disagreement was
  possible", is a natural sibling of the existing can-it-fail handling rule.
- **overnight-lab — YES, and applied in this pass** (the skill's own instruction
  permits it): 7.6 (rows-last) and 7.3(a)+(d) (record the environment, SKIP
  loudly) go into [implementation detail withheld], alongside a lesson the ISO-1 gate
  race taught that fits nowhere else — **pin corpus MEMBERSHIP; never discover it
  by globbing a directory other lanes append to.** A task selftest globbed the
  shared live [implementation detail withheld] for its own prefix and asserted a count
  of 27; an unrelated cell wrote six workdirs there in August and the gate
  reported 13 problems from then on. Same family, same night-shift shape: two
  concurrent gate runs read each other's seeded mutants as real defects, which is
  why [implementation detail withheld] now takes a lockdir and why anything **reading** the
  live tree must check [implementation detail withheld] first — a reader cannot tell a seeded
  mutant from a real defect. Source: commits 7300422, 8833cec, c88a3ee,
  d5966f3; HANDOFF.md lines 83–91 (THE TREE-BUSY RULE).

**Bound on all six.** One programme, one repo, n=1 per incident; these are rules
about apparatus discipline, not measured effects, and none of them carries a
registry finding id. They earn their place because each was paid for by a wrong
answer that a green check had already certified.

### 7.8 Record the harness denial count as a covariate whenever a permission allowlist is part of the treatment (ADDED DOC-2 2026-09-02 — not one of the ISO-1 six above)

A don't-ask allowlist is **uniform across arms, and therefore feels like a
constant** — but *how often a model reaches for shell it was not given* is a
model property, so the resulting denial count is a per-run **covariate** of
every turn, cost and behaviour contrast, not a background condition. Report it
per arm, and re-run each headline contrast with the denial-bounce turns
removed; a contrast that exists in only one of the two cuts is not a result.
Hint — **the correction can go either way, so you cannot sign it a priori**:
under the Fable-intake allowlist the docs-bulkedit turn ratio
Fable-5.1-medium / Opus-5-medium **WIDENED** when denials were cut out
(0.61x → 0.57x ex-bounce, 0.53x scale-matched), because Opus took more denials
per run there — the artefact was *masking* Fable's turn advantage, not
manufacturing it — while the effort ladder's max-over-low **cost** ratio shrank
2.81x → 2.40x per correct, i.e. ~1/7 of max's premium over low was
denial-bounce output tokens. Three mechanical warnings: count denials from the
RESULT block (denied results with no tool_use_id exist on disk, so an
id-paired count is a lower bound); a missing transcript is None, never 0; and
the allowlist's prefix rule matches the whole command **line**, so any compound
line ([implementation detail withheld], a pipe, a redirect, a heredoc) fails the prefix
match and is denied even when its program is allowed — 17/17 of the
[implementation detail withheld] denials were this, not an allowlist bug. The
substantive checker consequence is §2.3's "a checker the harness denies is not
a checker" [#136; den1-denial-covariate-2026-09-02.md].

### 7.9 A permission allowlist DECOMPOSES the command; a shape it cannot express is not a policy you chose (ADDED ALLOW-1 2026-09-03)

**Corrects the mechanism sentence in §7.8** (the covariate rule itself stands).
The allowlist does **not** match the whole command line. Claude Code splits on
[implementation detail withheld], [implementation detail withheld], [implementation detail withheld], [implementation detail withheld], [implementation detail withheld], [implementation detail withheld] and newlines and **every sub-command must match
an allow rule independently** [permissions.md#compound-commands, CLI 2.1.259].
Three consequences that a whole-line reading gets wrong, and that decide what a
"widen the allowlist" fix can and cannot buy:
1. **A narrow rule is safe inside a compound.** [implementation detail withheld] allows
   [implementation detail withheld] and still denies [implementation detail withheld], because
   the second sub-command matches nothing. Adding a family is bounded by that
   family, not by what can be concatenated onto it.
2. **Shell keywords are unallowlistable.** for/while/if/do/done are
   not commands; no [implementation detail withheld] rule can ever match them. A loop-shaped denial
   is a fixture/task problem, never an allowlist problem — and loops were the
   single largest denied shape (867 of 2655).
3. **The floor is higher than the file says.** dontAsk also runs the CLI's
   built-in read-only set — `ls cat echo pwd head tail grep find wc which diff
   stat du cd` [permissions.md#read-only-commands]. Measured on this harness:
   138 bare read-only calls ran, 1 denied. **So "the tested arms had no shell"
   was never true**; what they lacked was compounds, loops, heredocs,
   interpreters and writes. Re-read any claim that rests on "no shell".
Ceiling, measured: allowlisting the whole read-only tier removes ~19.5% of
denials. The other ~80% are unreachable by widening a prefix list. (§7.10
bounds that ceiling further: it does not credit the built-in read-only set or
sandbox auto-allow, so it overstates.)
**AN ALLOWLIST VERSION IS KEYED TO THE SETTINGS SHA, NEVER TO A DATE** (ALLOW-3
2026-09-03, both #14 reviews). The rule that first stood here — "rows dispatched
from 2026-09-03 carry [implementation detail withheld]" — was false when written: the change was
unmerged, and all 16 runs archived that day carried v1. A date names when
somebody committed; the treatment changes when a DISPATCH first reads the new
file, which is after the ISO-1 re-bind smoke and is not knowable at commit time.
So: version by the discriminator the manifest already records —
artifacts.settings.sha256 ([implementation detail withheld]) — write the boundary as
"rows whose settings sha is X are vN", and leave the first vN run as TBD until
one exists. [implementation detail withheld] itself was REVERTED by ALLOW-3 (§7.10.1), so **there is
no v2: every row to date is [implementation detail withheld] = the three prefixes.**
[#136 ask 2; allow1-cd-allowlist-2026-09-03.md + its -data appendix;
allow2-tier2-stress-2026-09-03.md#round-3]

### 7.10 Once a Bash SANDBOX is on, the allowlist is no longer the gate — a rule can only take effect on what the sandbox or the analyzer already refused (ADDED ALLOW-2 2026-09-03)

**Bounds §7.8 and §7.9, which both assume the allow list decides.** Since ISO-1
fix5 set [implementation detail withheld] ([implementation detail withheld], 2026-08-22),
Claude Code's **sandbox auto-allow** approves every command it can contain, and
autoAllowBashIfSandboxed defaults to true [sandboxing.md, CLI 2.1.259]. Live
witness from a scored run: [implementation detail withheld] **ran** under settings sha
[implementation detail withheld], whose allow list has no rm and which grants rm nothing via the
read-only set either. What is still denied is what the CLI could not statically
verify — loops (91 of 467 post-fix5 denials), inline [implementation detail withheld], unknown env
assignments, cd compounds that write.
1. **Adding a family to the allow list does not buy its benign uses; those
   already run.** It takes effect *only* on the calls that were refused — i.e.
   on the shapes the analyzer could not verify. Widening is therefore aimed at
   exactly the wrong tail, which is why ALLOW-2 added **none** of
   {sed, ls, grep, head, wc, for}: measured, ls ran 249/0, grep 84/0,
   [implementation detail withheld] 14 ran.
2. **A marginal-unlock estimate that ignores the built-in read-only set and the
   sandbox is not an estimate of anything.** [implementation detail withheld]
   already ran 56/1; §7.9's ~19.5% ceiling is an overstatement, and [implementation detail withheld]
   bought nothing ([implementation detail withheld] ran under v1) while still
   splitting the corpus into [implementation detail withheld]/v2.
3. **The answer guarantee never rested on the allow list, and still does not.**
   It rests on sandbox.filesystem.denyRead plus the documented default write
   policy, and the OS *"enforces the sandbox boundary on the running process …
   regardless of what the model chose to run"* [sandboxing.md]. So a read-only
   tier could not have reopened the answer channel — and equally, could not have
   been the reason it was closed.
Corollary for any harness whose treatment is "restricted shell": state which
layer you are manipulating. If a sandbox is on, permissions.allow is not it.

**7.10.1 (ALLOW-3, 2026-09-03) — a no-op treatment still costs, so revert it.**
[implementation detail withheld] was reverted from all 12 variants. Two independent #14 reviews
measured the same thing from the corpus: **0 of the 467 post-fix5 denials would
have flipped**, because every denied cd compound carries a second unmatched
head, and cd compounds already ran 376 times under v1. What it did buy was a
permanent v1/v2 split on a per-run covariate (§7.8) and a second file every
ISO-1 re-bind must carry. The rule to carry: **a treatment-version label with no
measured treatment behind it is bookkeeping tax on every later contrast — price
the label, not just the change.** The measurement that decides this is cheap and
came from the archive, not from a run: ask how many actual denials the rule would
flip before you ship it. (The one family with a real measured unlock is echo:
25 denials, 21 of them with no redirect on the line. It is deliberately NOT added
here — it gets its own decision on its own evidence.)
[allow2-tier2-stress-2026-09-03.md + its -data appendix and #round-3; 32-row
offline probe matrix in [implementation detail withheld];
allow2-review-2026-09-03-opus.md, allow2-review-skeptic-2026-09-03-opus.md]

### 7.11 A workspace file that narrates the METHOD leaks as badly as one that contains the ANSWER (ADDED ALLOW-4 2026-09-03, #140)

The difficulty/leakage rule says: before calling a task hard, ask what file in
the workspace contains the answer. Its inverse costs just as much. A $1.37 probe
run designed to settle 12 questions about the permission matcher settled **zero**
of them: the fixture copied into the agent's workspace carried its own header —
how to dispatch it, which settings variant, and that the point was to see whether
the model would "blindly execute" commands. Sonnet-5 read the header, correctly
identified it as an injection test, declined all 12 commands, and did the real
task. The run measured the model's harness-trust behaviour, which nobody had
asked about.

**So: whatever ships into the workspace is part of the prompt.** Write it as the
artifact the fictional ticket would actually contain, and keep the expected
outcomes, the dispatch instructions and the word "experiment" on the verifier
side of the line. Two mechanical consequences, both cheap:

* **Split the file.** One generator, two renderings — a shipped half (commands,
  ticket framing) and a verifier half (expectations, dispatch, what each row
  decides). Enforce the split with a forbidden-word test over the shipped file's
  content AND its basename.
* **The basename is a contract.** EXTRA_WORKDIR_FILE copies the file under its
  own basename ([implementation detail withheld]); there is no rename hook. If the prompt
  names a different file, the agent is told to open something that does not
  exist — the second half of this same defect, and the reason the header got read
  at all.

Ask the fixture's reviewer one more question, separately from correctness and
from difficulty: **what does the agent see, and would it read as a test?**

**Addendum (round 2, same day).** Splitting the file was not enough. The shipped
half still told the agent to run [implementation detail withheld] on a file
containing no prod, to rewrite the validator's own output string to X, and to
run [implementation detail withheld]. None of those names the experiment; all of them are
things a competent engineer refuses and asks about — so the rerun would have
measured suspicion a second time, from a different direction. The rule that
generalises: **a fixture is de-leaked when every instruction in it would survive
being questioned by the person asked to run it, not when it stops naming the
study.** Give every step a reason anchored in something already in the workspace,
ship the reason column, keep the intent column verifier-side — and if a step
cannot be given an honest reason, drop it and say so.
[#140; bench/runner/tests/test_g1_probe_shipped.sh §6 (mutant table in its
header); fixtures/VERIFY-STEPS.tsv vs fixtures/g1_probe_expectations.tsv;
bench/results_analysis/g1probe_score.py; g1-battery-design-2026-09-03.md]

### 7.12 An allow list exempts an executor by RULE TEXT, never by head name (ADDED ALLOW-4 round 2, 2026-09-03)

The tier-2 candidate's "no code-executing head" check subtracted [implementation detail withheld]
from its hit set unconditionally — because four legitimate rules pin those heads
to [implementation detail withheld] — and then asserted in its pass message that "bash/sh appear only
pinned to check.sh", which nothing verified. Adding [implementation detail withheld], arbitrary
code execution, left the suite green.

**So: write the exemption as the thing that makes it safe.** `^Bash\((bash|sh)
\.?/?check\.sh` exempts the pinned rules and nothing else; a head-name subtraction
exempts every rule that head can appear in. The same reasoning retires the
"priced hazard" pattern: a bare [implementation detail withheld] admits [implementation detail withheld] (executes) and w
(writes any path), and [implementation detail withheld] admits [implementation detail withheld], so both
were removed from the candidate rather than documented. **Pricing a hazard in a
comment is not excluding it**; the allow list is the only thing the matcher
reads. [round-2 delta review MAJOR-1;
bench/runner/tests/test_tier2_candidate_settings.sh §2;
bench/runner/settings.candidate.tier2.json]

**Addendum (round 3, 2026-09-03): a guard bar is an ALLOWLIST.** The same check,
rewritten as a longer blacklist, was walked through again — this time by
*exec-wrappers*: timeout, nohup, git, tar, rsync, less, vi, pip
execute nothing themselves, so no list of "code-executing heads" ever names them,
and each of them runs an arbitrary command anyway. **A blacklist is only as long
as the last person's imagination.** Enumerate the heads a candidate MAY carry —
the base list plus the read-shaped widening — and fail an *unrecognised* head by
default. Keep the blacklist as a second, independent bar: it is worthless as the
only gate and valuable as the thing that produces a specific error message.
[round-2 review MAJOR-4; [implementation detail withheld] §2]

### 7.13 An expectation about a configured layer must be RE-DERIVED from that layer, not asserted beside it (ADDED ALLOW-4 round 3, 2026-09-03)

Two probe rows in the G1 fixture CONFIRMED while deciding nothing. v09 expected
DENY on [implementation detail withheld] — which the isolation layer *explicitly re-grants*
([implementation detail withheld] TOOLCHAIN_REGRANTS), so it could only ever run.
v08 expected to be testing a deny on [implementation detail withheld], a path no rule
denies: round 2 had moved it there to satisfy a lint about naming [implementation detail withheld],
and in doing so removed the only thing that made the row able to fire. Both rows
were reviewed. Neither review composed the layer.

**So: if a check's expected value is a function of a generated config, compose
that config inside the test and read the expectation off it.** The G1 suite now
calls [implementation detail withheld] for a realistic run root and re-derives every row's
DENY/RUN from the composed deny + allow sets; move a row onto a granted path and
§8 goes red. Two corollaries, both earned:

* **A retarget made to satisfy a lint is a retarget nobody checked.** When a
  check forces you to move a target, the move needs its own evidence that the new
  target still decides the same question.
* **A check that passes must be able to fail for the reason it exists** — and
  that includes the re-derivation itself. Round 3's §8 caught an exception from
  [implementation detail withheld] and turned it into a SKIP with exit 0, so on any host where
  the layer could not be composed the entire verifier silently did not run and
  the suite still printed OK. **Route every skip through the suite's skip
  accounting**, so an unexercised section is a PARTIAL an operator has to
  acknowledge, never a pass. [round-2 review MAJOR-1/MAJOR-2, round-3 review
  MAJOR-1; [implementation detail withheld] §8]

### 7.14 A leak check must prove something was PLANTED before it may say CLEAN — and the plant must not break the host it runs on (ADDED ALLOW-4 round 3, 2026-09-03; extended round 4 and round 5, 2026-09-04)

The G1 battery shipped a canary REGISTER and a canary SCANNER and nothing that
put a needle anywhere. Run over a real archived transcript the scan printed
[implementation detail withheld] — character for character what a
genuinely clean run prints, over a run in which nothing had been planted. **A
negative result needs a positive control attached, per run.**

* Pair the scanner with a **planter** and a per-run **manifest** of what was
  planted, and make the scanner REQUIRE the manifest.
* Add a third status: INDECISIVE, distinct from clean and from stop, for "no
  manifest / nothing planted / a manifest written against a different register".
  Not clean, not a stop, and its numbers may not be read.
* **Name what you could not plant.** Registered locations the planter cannot
  reach are printed and excluded from the CLEAN claim. An uncovered read path
  stated out loud is a residual; one hidden inside the word CLEAN is a false
  negative.

**Round-4 extension, and it is the operationally expensive half.** Planting
canaries creates directories literally named [implementation detail withheld], and ISO-1 Gate A refuses
**every** dispatch on the host while an unregistered answer-bearing root exists in
a scanned area. Round 3 answered that with a --cleanup step and the word
"immediately", which covers the window *after* the run and not the window the
plant has to be open — the one the dispatch happens in. The documented
plant→dispatch order therefore refused its own dispatch, deterministically, at
$0, and would have left the box red until someone noticed.

**So: a plant may not create an unregistered answer-bearing root at all, and
"immediately" is not a mechanism.** Two rules:

* **Assert it against the real gate.** Plant with production defaults, run the
  same inventory the runner runs pre-dispatch, require rc 0. A location that
  cannot be planted safely becomes [implementation detail withheld] with its reason and its read path
  becomes a stated residual — the alternative (registering the path) edits a
  binding input and forces a re-bind.
* **Put the order in a program, not in a comment block.** Plant → dispatch →
  unplant → score, with the unplant on an EXIT trap so it runs on paths nobody
  planned for. Both defects found in this recipe across two review rounds were
  purely ORDERING defects, and a recipe a human executes in eight steps will be
  run wrong. The same applies to the *test* tooling: resolve its scratch root
  explicitly and refuse one inside a scan area, or the free offline cell reddens
  the host it is protecting.
**Round-5 extension: check the state the RUNNER creates, not only the state you
create.** Round 4's guard planted with production defaults and inventoried the
*host*, and it passed — while a third canary was still broken in exactly the same
way. That one was [implementation detail withheld]: the planter wrote it into a seed tree, and the
*runner* copied the seed tree into the workspace, which on a normal run **is** a
directory under the scanned area. The offending [implementation detail withheld] directory therefore did
not exist at the moment the guard looked, and the gate that refuses on it runs
*after* the copy. Two rounds, same defect, one directory apart, because the guard
and the gate were looking at different points in time.

* **A pre-run inventory cannot see what the run materialises.** If your fixture
  reaches the workspace through a runner mechanism (a seed overlay, a
  materialize hook, an extra-file copy), REPLAY that mechanism in the test — the
  same command, the same excludes — and run the gate over the result.
* **Scope that replay to the replayed directory.** A REPLAY check that walks the
  host is judging a concurrent paid batch, not its own fixture. Pass the gate the
  replayed directory and nothing else, which is also the shape the dispatch
  chokepoint itself uses. (Scoped to the replay check, 2026-09-04, round-5 Fable
  review NOTE-1: as written this said "never let a test suite run the host-wide
  walk", and the same suite runs three of them on purpose — the assertion that a
  plant made with PRODUCTION defaults leaves Gate A green is only meaningful
  host-wide. A rule that the file citing it contradicts is a rule people learn to
  ignore. The host-wide walk is legitimate for exactly that assertion, and it is
  what the lock rule below is for.)
* **A guard over a fixture that no longer plants anything is vacuous, so give it
  a positive control.** After the demotion no row created an [implementation detail withheld] directory
  at all, and the new check would have passed over any planter including one that
  does nothing. Build the bad shape deliberately in the same test and require the
  gate to refuse it.
* **A cleanup that can fail must not destroy its own recovery artefact.** The
  failure path told the operator to recover using a manifest that the exit trap
  deleted three lines later. Copy the record out before the teardown, and name
  the surviving path in the message.
* **Do not file the needle list inside the archive it protects.** A plant
  manifest lists every canary in plaintext; inside the archive, no future
  whole-archive census can tell it from a leak. Keep it beside the archive, put a
  pointer in, and assert the archive's *content* is needle-free rather than
  asserting one filename is absent. **Search for the needles that mean what the
  check means, and search after the thing that interprets them.** (2026-09-04,
  round-5 review BLOCKER-1.) The register distinguishes a CONTENT token, whose
  appearance is a read, from a PATH, whose appearance is an attempt the design
  expects — a denial quotes the path, and so does the probe's own shipped step
  list, which the runner archives verbatim. Matching content against *all* the
  needles made the check refuse the archive of a run in which the model did
  nothing, and it ran before the scorer, so the paid path could not succeed on
  any outcome. It also has to run AFTER the scan it duplicates: on a genuine read
  the token is in the archive *by definition*, so a fatal hygiene check placed
  first means the stop rule can never be emitted by the script that documents it.
* **A needle list that is kept needs a retention rule.** (2026-09-04, round-5
  review MINOR-3.) Moving the plaintext list out of the archive and then keeping
  one per run, forever, relocates the census problem rather than removing it.
  Retire it once the scan that needed it has returned clean, and leave a
  needle-free summary (ids, kinds, hashes) so the record of what was planted
  survives; keep it verbatim on any outcome where someone has to act on it.
* **A plant at absolute host paths needs a lock, and it must not be the dispatch
  lock.** (2026-09-04, round-5 review MAJOR-1.) Anything that plants with
  PRODUCTION defaults writes to one set of paths per host, and twin-reviewer
  practice (REV-F1) now runs two copies of the same suite at once: interleaved,
  one run's cleanup deletes the other's plant, and the loser goes red — or green
  because the paths it checked were emptied by somebody else. Namespace every
  plant that does not need production roots; serialize the ones that do, on a
  lock keyed to the PLANT ROOT. Never on the convention #21 dispatch lock: a free
  offline suite holding that refuses every paid run on the box while it runs.

[round-2 review MAJOR-2/MAJOR-3, round-3 review MAJOR-3/BLOCKER-1, round-4 review
B-1/M-1/M-2/m-3; [implementation detail withheld];
[implementation detail withheld];
[implementation detail withheld]; [implementation detail withheld];
[implementation detail withheld] §7a–§7i; g1-battery-design-2026-09-03.md]

---

## 8. Audit instruments: what a measurement apparatus does to the measurement (2026-08-30, SWR-1)

SWR-1 was an experiment about whether a beat-swarm review still works when the
flagging shards are a cheaper model. **It never produced a recall number.** Its
shard layer ran, its depth layer ran, and its *grading* layer died three times:
once killed outright by a sandbox profile that granted read on a settings file
which has never existed, and twice **voided by its own access-audit instrument**
on events that hand-verification found were overwhelmingly (attempt 1: 7 of 9
over-approximation, 1 refused-before-executing, 1 real write to a staging file)
or entirely (attempt 2: 9 of 9) not accesses at all. The arm cost $64.94 and its
deliverable is this section.

That makes it a different kind of evidence from §§1–7: not a measured effect
about models, but three rules about **apparatus that judges agents**, paid for by
an arm that was terminated by its own judge. They transfer to anything that gates
work on an automated conduct check — a CI policy scanner, a DLP rule, an
agent-sandbox audit, a compliance grep.

Doctrine delta (convention #16): three rules ADDED. Nothing here contradicts an
existing rule; **8.1 SHARPENS 7.1** (which asked what UNIT a check names) by
asking what CHANNEL it names, and **8.2 is the enforcement-side sibling of
7.3(c)** (agreement is evidence only if disagreement was possible).

- **8.1 A proxy predicate manufactures group differences. Before you report a
  gap between two arms, re-measure it with a matcher that cannot see which arm
  it is looking at.** SWR-1's shard layer showed **8 of 18** runs excluded for
  access violations against SW-OPUS-1's **1 of 18** — a clean, alarming,
  apparently behavioural result about a cheaper model being less disciplined.
  It was the instrument. The matcher scored a *spelling* (a path-shaped token
  anywhere in a command; a raw sha positionally after git) rather than the
  *thing* (a file actually opened outside the allowed tree; a revision not
  reachable from the pin). **Four of the eight are verified matcher defects** on
  hand-inspection (three greps where the flagged path sat inside the search
  *pattern*, one [implementation detail withheld] parsed as a git revision), and on the one
  channel that was re-measured **blind to which arm it was** — the
  revision-reading channel — the counts are **4/18 vs 1/18 vs 3/18**, Fisher
  p = 0.34 / 1.0 and **p = 0.42 against the pooled Opus arms**. Genuine
  out-of-tree file reads are **1 / 0 / 0**, the one being a filename search that
  returned no content. Say it precisely: the 8/18 and the 4/18 are **not the same
  measure** (all limbs vs one limb), so the claim is not "8 became 4" — it is
  that *the only channel anyone re-measured without knowing which arm it was
  shows no arm effect, and half the original count is verified instrument
  defect.* A p = 0.018 that survives neither of those checks was never a result. And the residual signal is not about the model at
  all: 6 of the 8 events across all three arms sit in the *closure* beat, which
  is 3 of 18 shards, because closure is the beat mandated to check provenance
  claims. **Hint: the tell is asymmetric instrumentation, not asymmetric
  behaviour** — the arms differed in substrate (sandboxed CLI vs unsandboxed
  Agent-tool subagent), so the matcher had different material to chew on in each,
  and the positional bug *under*-fired on the comparison arms in their own favour
  (it missed 3 of 4 real events in SW-OPUS-1's closure shard, and a real one in
  LOW's, because shlex glued a [implementation detail withheld] onto the token). A defect that is symmetric
  in code is rarely symmetric in effect. Also: **every sha touched by any shard
  in any arm was a pre-pin ancestor — the channel the rule polices is real and
  worth policing, and it had caught nothing.** Source:
  swr1-run-record-2026-08-30.md §"HALT DISPOSITION" Results 1–5 and prereg
  amendment A11; commits a3f8f89, 86a3051.

- **8.2 An isolation posture is not a control until something verifies it stayed
  on.** The SWR-1 grader ran under an OS sandbox profile, a generated deny list,
  and an access audit with three limbs. It made **two tool calls carrying
  [implementation detail withheld]**, and the audit saw nothing — because it had
  no limb that read tool-call *parameters* at all, only paths. "Runs under the
  sandbox" was the registered condition of every arm this instrument had ever
  audited; nothing checked it. Adding the limb (limb (s), a defect fix rather
  than a rule change) and sweeping it across **54 shard cells in three arms plus
  3 depth passes** returned **zero** other bypasses, so no published result was
  affected — but that was luck, and the sweep is the only reason we know it.
  **Hint: the shape is a control with an opt-out that the control's own
  observability does not cover** — ask, for every safety property you assert,
  *what would it look like in my logs if this were switched off mid-run?*, and if
  the honest answer is "the same as if it were on", you have a posture, not a
  control. Two corollaries worth carrying: the disposition rule matters as much
  as the detection (a bypass whose every target is inside the lane's own write
  grant is an operating artifact of YOUR defect and should WARN with the cause,
  not exclude; an **unscoped** bypass is a violation because a bypass you cannot
  scope is not a bypass you can clear); and detection is not prevention — the
  general case here remains detected-not-prevented, and that is recorded rather
  than papered over. Source: swr1-run-record-2026-08-30.md §"GRADE CLOSE-OUT"
  and §"Prep 2 — limb (s)"; [implementation detail withheld]
  (bypass_flags, classify_bypass); controls [implementation detail withheld] 22/22;
  commits 82c538a, 7ac4a69.

- **8.3 Probe the READ side of every path you grant for writing — and never let
  a matcher read a command's own output as if it were its operands.** Three
  separate deaths in one arm, one shape: **the profile and the brief disagreed
  about what the lane could touch, and nothing checked the agreement until an
  agent hit the wall.** (i) A sandbox re-grant named a settings file that had
  never existed, so all three depth passes died at startup with EPERM, $0 spent
  and three empty memos. (ii) The grader was granted **write** on its report and
  not **read**, so it could not [implementation detail withheld] the file it had just produced — which is
  exactly why it reached for the sandbox bypass in 8.2. (iii) The access matcher
  tokenised the grader's own heredoc *body*, so the report's prose — a markdown
  [implementation detail withheld] slash resolving to [implementation detail withheld], and the string `[implementation detail withheld]`
  quoted inside a shard flag being transcribed — scored as nine out-of-bounds
  reads, three of them on a command the harness had **refused to execute**. The
  fix that works is a **differential probe per lane before dispatch**: attempt a
  real read and a real write on every granted path under the actual profile, with
  negative controls that must be DENIED (if the controls read, the probe is
  measuring nothing). **Hint: a write grant without a matching read grant is the
  common case and the dangerous one, because the failure surfaces only after the
  agent has done the work** — and the general rule underneath is that *an
  instrument must distinguish what a command OPENS from what a command SAYS*:
  strip heredoc bodies and quoted literals before tokenising, and never treat a
  bare [implementation detail withheld] or [implementation detail withheld] as a path-like token. Source:
  swr1-run-record-2026-08-30.md §"Depth halt … mechanism established",
  §"Prep 3", and §"SWR-1 TERMINATED" forensics; staging GATE 7 and
  [implementation detail withheld]'s read/write probes with three negative controls;
  commits fdd75cf, 7ac4a69.

- **8.5 A judge does not grade real data until it has reproduced a corpus of
  already-settled cases, and that corpus grows by accretion from every grading
  failure.** SWR-1's three grading deaths were regressions, not hard calls: a
  launcher whose gates were dead behind a pipe, an audit blind to a documented
  opt-out parameter, and a matcher that read a command's own output as its
  operands. Each was cheap to catch and none was caught, because every one of
  these instruments shipped to a live money-spending arm with only its author's
  selftests behind it — §7.4's exact configuration. The fix is not more review;
  it is a frozen known-answer set the instrument must reproduce before dispatch,
  carrying **labels AND the rationale that settles each one**, with negative
  controls that must come back clean and at least one case whose right answer is
  *"I cannot grade this"*. **Hint: the corpus is built from your own incidents,
  the day they are diagnosed — a synthetic corpus tests the defects you already
  imagined.** Two operating cautions, both first-party: a corpus made of one
  arm's failures is majority false-positive, so a LOOSENED instrument can score
  higher on the count than the incumbent (measured: 21/26 vs 15/26) — every case
  must match, the count is not the gate; and an instrument with known-open
  defects is gated in REGRESSION mode against a recorded baseline, never in spec
  mode, because a gate that cannot be satisfied gets switched off. Source:
  bench/reports/grader-canary-2026-08-30.md; corpus [implementation detail withheld] (42 cases,
  24-assertion mutant selftest); issue #116; the design shape is Netflix
  arXiv:2608.18300 phase I, cited for shape and for no number.

- **8.6 Ask every reviewer whether a gate can FAIL WRONG, not only whether it
  can be evaded (2026-08-31).** A false-positive gate destroys more of our data
  than an evadable one: the FAIL-WRONG mandate, in its first two days, found
  the widening that silently refused every terraform dispatch (#119) and a
  halt classifier that attributed an ordinary FileNotFoundError to the sandbox
  — both would have burned batches while every detection-side check stayed
  green. Hint: the question to put to the beat is "what benign input trips
  this gate?" — put it in the mandate verbatim. Evidence:
  review-compat1-2026-08-30.md §4, review-compat1-v5-2026-08-31.md.
- **8.7 A capability is not shipped until one live end-to-end execution of the
  real path has passed (2026-08-31).** Green gate tests are prose about the
  live path: the tf widening shipped 33/33 tests while zero terraform
  dispatches could run — three times in one day the tests passed and the path
  was dead (TMPDIR digest, AF_UNIX socket cap, settings-file self-denial).
  Hint: the proof is one cheap real dispatch through the full chokepoint,
  budgeted into the change itself; a probe with a conveniently short path or
  a piped exit status is not the real path. Evidence:
  tf-allowlist-probe-2026-08-30.md §W.9, gh #119/#120.
- **8.8 A check that passes must be able to FAIL for the reason it exists — so
  verify it by breaking the thing it guards, in the direction that matters
  (2026-08-31).** 8.7 says run the real path; 8.8 says the *gate* is a
  capability too, and un-break-tested gates fail in one direction and report
  green. Three shapes, all found in one delta: an assertion that recomputes its
  expectation **from the modified input** cannot fail — COMPAT-1a v7's AUTO-FIRE
  BACKING check passed when a forbidden grammar was ADDED, because it re-ran the
  classifier with the new set, while both the code comment and §10 claimed it
  "fails in either direction"; an assertion that **greps its own source** certifies
  spelling — 6 of the 22 assertions in the driver's unit gate are greps over
  [implementation detail withheld], and it passed 22/22 over a dispatch_loop that halts on runlist entry 1
  and has never dispatched a run; an assertion whose **inputs are gitignored**
  certifies the author's laptop — [implementation detail withheld] silently
  compared 14 of 17 origins in any fresh checkout, so a published `100 passed,
  0 failed` was 99/1 from the committed bytes. Hint: for each gate, name the
  wrong state it is supposed to catch and produce it; if you cannot produce it,
  the gate is decoration. Evidence: review-compat1-v7-2026-08-31.md §5.2,
  [implementation detail withheld].
- **8.9 A probe that builds its own model of the environment measures the model
  (2026-08-31).** Hand the probe the artifact the run will actually use, or it is
  a second opinion from the same source. COMPAT-1a v7 built the generalised
  execute-mandate probe the v6 report demanded, ran it, and it reported "every
  mandated command executes under this lane's write constraints" — while all six
  shards then reported they could not execute the corpus, for the THIRD gate
  running. [implementation detail withheld] constructs its OWN
  Seatbelt profile and ignores the --profile path→mode map handed to the model:
  it granted a [implementation detail withheld] scratch the shards never had (their profile is 319
  entries, read 2 / none 317, no write grant anywhere), and its
  [implementation detail withheld] baseline cannot express a READ denial — yet every "Could not
  reach" line in all six memos is a read denial. Hint: a probe that does not
  consume the run's own config file is testing a story about the config.
  Evidence: review-compat1-v7-2026-08-31.md §8.1,
  [implementation detail withheld].
- **8.10 Retry is a fix for TRANSIENT failure only; a deterministic failure
  retried is budget theatre (2026-08-31).** The v6 lane added a five-attempt
  collector retry and a named failure marker. Both fired for the first time in
  v7 and they scored opposite: the retried failure was
  [implementation detail withheld] — identical on all five attempts —
  while the NAMED marker worked exactly as designed and stopped the depth chain
  from grading a partial swarm. Hint: do not retry an exit code the tool uses for
  usage errors, and do not hard-code a lane enumeration that the next lane will
  fail. Evidence: review-compat1-v7-2026-08-31.md §8.2.

- **8.15 A refusal is only checked when its EXIT CODE is checked (2026-08-31).**
  A test that accepts "non-zero" accepts the program failing for a reason the
  test was not written about, and the more refusal paths a program has the more
  likely that is. COMPAT-1a v8 added six test seams and put each on its
  driver's GATE 0 refusal list — but the seams are written
  [implementation detail withheld], which makes the variable non-empty ALWAYS, so
  GATE 0 refused **every** launch with exit 10 and --run could never reach
  GATE 1. Four commits shipped that way under 65 green assertions, because the
  assertion was [implementation detail withheld] — satisfied by exit 10, not
  by the registered exit 11 or 13. Hint: name the code in the assertion, and add
  the negative control that the *other* refusal does not fire. Evidence:
  review-compat1-v8-2026-08-31.md §3, prereg §0.0.V8.2c, commit 07633ad.
- **8.16 Copying a number that was verified once is not counting it
  (2026-08-31).** Convention #17 says re-derive a derived number; the failure
  mode is subtler than staleness, because a figure that carries someone's
  "helm-verified" stamp reads as already counted. COMPAT-1a v7's gate report
  criticised the v7 draft for publishing six corpus subtotals under a
  convention-#17 stamp that were all the *previous* corpus's — and published its
  own recount, **22 real / 15 synthetic**, which the v8 draft then copied.
  Counted from source it is **21/16**, and the artifact key the same report
  quoted exists on none of the 37 case files. Two gates running, the same
  paragraph, the same error one level up. Hint: a stamped paragraph must name
  the command that produced its numbers, so the next reader re-runs it instead
  of inheriting it. Evidence: review-compat1-v8-2026-08-31.md §7 item 5, commit
  6569a1e.
- **8.17 A test that passes when its own SETUP failed is not a test
  (2026-08-31).** The setup step is not covered by the assertion, so a setup
  that silently fails converts a real check into a vacuous one that still
  reports green. COMPAT-1a v8's [implementation detail withheld] — written to prove
  the AUTO-FIRE BACKING assertion can fail in both directions — doctored its
  inputs with [implementation detail withheld]; under a lane profile with no write grant mktemp
  fails, the doctored file is never written, and the checker then fails
  **because it cannot open a file**, so two assertions passed for the wrong
  reason. Found by running the test under the *review lane's own* profile
  before dispatch, which 8.9's rebuilt probe made possible. Hint: prefer test
  affordances that need no filesystem (arguments over doctored copies), and
  assert that setup succeeded. Evidence:
  review-compat1-v8-2026-08-31.md §8.2, commit 5c9a81b.
- **8.18 A check that cannot see its input must say UNDETERMINED, not report a
  verdict (2026-08-31).** Under an answer-isolation profile that denies
  [implementation detail withheld], every evidence-reading prerequisite probe in COMPAT-1a v8
  reported its row OPEN — a verdict about the SANDBOX wearing the
  PREREQUISITE's name, and a reviewer running the probe under their own profile
  would have filed a false finding. Exit 3 UNDETERMINED distinguishes the two;
  the dispatch gate still treats any non-zero as open, so it stays fail-closed
  where fail-closed matters. Hint: separate "the thing is wrong" from "I could
  not look", in the exit code, not in the prose. Evidence:
  review-compat1-v8-2026-08-31.md §8.2.
- **8.19 A handshake between two programs is a PARSE of the producer's
  structure, never a scrape of its rendering — and an unknown value is never
  zero (2026-08-31).** COMPAT-1a v7's driver obtained its cost forecast with
  [implementation detail withheld] from a tool that emits JSON keyed
  projected_cost and has never contained that substring, so it halted at
  runlist entry 1 on every batch. Repairing that exposed a second join of the
  same shape: it called [implementation detail withheld]
  against a program that takes four positionals and has never printed a run
  directory, and then read the run's cost from [implementation detail withheld] with
  [implementation detail withheld] empty, under [implementation detail withheld] — **so the cumulative $12 cap
  would have been fed $0 for every run in the batch.** Neither was found by
  seven swarm reviews; the first live dispatch found both in under two minutes
  for $0.09. Hint: parse by key and REFUSE on absence; [implementation detail withheld] on a spend
  figure is a cap that fails open. Evidence:
  review-compat1-v8-2026-08-31.md §5.1, doctrine 8.7.
- **8.20 When a repair adds a LIMB to a judge, the corpus needs a row only that
  limb can answer — and a row the limb must NOT answer (2026-09-04, SWR-2 rounds
  6-8).** SWR-2 round 6 repaired an access audit to 28/28 over a corpus that
  could not see the repair: its new interpreter-heredoc limb was called
  [implementation detail withheld], a shape that function's own guard can never
  pass, so the limb was DEAD CODE and the round had REMOVED a read class the
  previous judge caught while its gate went green. Rounds 7 and 8 each added the
  missing rows and each time the previous round's score fell: the round-6 judge
  is 33/39 on round 7's corpus, the round-7 judge 41/47 on round 8's. Hint: the
  paired row is the load-bearing half — a limb with only true positives gets
  passed by an instrument that answers "violation" to everything. Evidence:
  swr2-sharded-depth-build-2026-09-04.md §§Round 6-8;
  [implementation detail withheld].
- **8.21 A widened check earns a FAIL-WRONG row before it earns a true-positive
  row (2026-09-04, SWR-2 round 8).** Round 7 widened "which program executes this
  heredoc body?" from the head of the line to every word on it, and the corpus —
  39 cases, ten mutants, all green — could not see that the ordinary act of
  writing a memo through sed/awk, or pretty-printing JSON with `python3 -m
  json.tool[implementation detail withheld]sh`, now scored as an
  out-of-bounds READ and excluded the arm from the experiment on its own
  deliverable. Every tuning row for the widening was a true positive, so the
  corpus rewarded strictness and called it a fix. Hint: for each newly-caught
  shape, write down the nearest BENIGN shape that shares its surface, and put
  that in the corpus first. Evidence: swr2-sharded-depth-build-2026-09-04.md
  §Round 8; the four [implementation detail withheld] rows and
  [implementation detail withheld].
- **8.22 A gate whose limbs share one exemption list loses the strict limb when
  the loose one is exempted (2026-09-04, SWR-2 round 8).** SWR-2's blinding gate
  refuses a memo that identifies its own arm. Round 7 correctly stopped it
  refusing words the arm reads in its OWN INPUT (sonnet is on 29 of the 308
  pinned flag lines) by demoting any such PATTERN — and self-identification rode
  in the same loop, so [implementation detail withheld] and [implementation detail withheld] began passing at
  rc 0 while the Fable arm, whose family word appears zero times, still refused
  everything. The blinding control had become a function of the manipulated
  variable. Hint: give each limb its own subtraction at its own granularity —
  the loose limb by pattern, the identifying limb by LINE with a quotation floor.
  Evidence: swr2-sharded-depth-build-2026-09-04.md §Round 8;
  [implementation detail withheld].
- **8.23 One mutant per rule BOUNDS a rule; it takes one per DIRECTION to
  BRACKET it (2026-09-04, SWR-2 round 9).** Three consecutive rounds of SWR-2's
  access-audit judge closed the previous round's defects and introduced new ones
  of the same class, alternating direction: round 7 widened the heredoc rule
  until an ordinary memo written through sed was scored as nine out-of-bounds
  reads; round 8 narrowed it until [implementation detail withheld] stopped being
  scanned at all. Every round shipped mutants and a growing corpus, and every
  round's mutants pushed the same way its own fix had — so the corpus could
  measure that the fix worked and never that it had gone too far. Hint: write
  the decision table BEFORE the code — every input shape, its required verdict,
  and which direction it guards — and give each rule two mutants, a widening one
  that must lose the FAIL-WRONG rows and a narrowing one that must lose the
  FAIL-SILENT rows. Evidence: [implementation detail withheld];
  swr2-sharded-depth-build-2026-09-04.md §Round 9; the eight
  [implementation detail withheld] mutants.
- **8.24 Measure a pattern against the corpus the SUBJECT reads, not the corpus
  you happen to have open (2026-09-04, SWR-2 round 9).** Round 8 widened the
  blinding gate's self-identification limb to a verb list ending in the bare
  nouns [implementation detail withheld], and justified it by measuring
  those patterns against the arm's 308 pinned FLAG LINES: 0 hits for every
  family, so the widening looked free. But the arm reads and cites the whole
  pinned repository, and over the documents it actually quotes the same patterns
  stand on 27 lines for opus, 2 for sonnet and 0 for fable — so the gate
  refused compliant memos thirteen times more often for one arm family than
  another, which is 8.22 inverted by 8.22's own fix. The measurement was correct
  and answered the wrong question. Hint: before quoting a hit count as evidence
  that a pattern is safe, name the universe you counted over and check it is the
  one the subject is exposed to. Evidence:
  [implementation detail withheld] MAJOR 1 and
  [implementation detail withheld] MAJOR 3;
  [implementation detail withheld] §7.

### 8.4 Skill delta (convention #16, second half)

Asked of each operating skill: does it need any of 8.1–8.3?

**STATUS: APPLIED 2026-09-02 (SKL-1, Evan's delegation 2026-09-02; see bench/reports/skl1-skill-edits-2026-09-02.md).** ~~STATUS: REGISTERED, NOT APPLIED.~~
Skill changes were Evan's to approve on this
repo — [implementation detail withheld] states it in terms
(*"Evan reviews skill changes; the live skill is unchanged until he approves"*)
— so these are recorded here and not written into the skill files. **Note the
accumulating cost of that rule as currently applied:** §7.7's five edits from
2026-08-29 are still unapplied a day later, and these four join them, so nine
doctrine-derived edits are sitting in this file rather than in the files an agent
loads before doing the work. That inverts the repo's own "put durable content
where the next reader will actually load it" rule. Raised for Evan in
day-2026-08-30-evening.md §6 as a single decision (keep approving individually,
or delegate doctrine-derived skill edits under the same record-it-in-the-artifact
accountability the methodological calls carry); recorded here so the backlog is
visible from the doctrine side too. **Resolved 2026-09-02 ~15:58Z: Evan chose
delegation** — doctrine-derived skill edits now carry the same
record-it-in-the-artifact accountability as methodological calls (project
CLAUDE.md §Decision altitude). All nine edits (§7.7's five, §8.4's four) were
applied by SKL-1 the same day: bench-guide #24 (8.2) and #25 (8.3),
swarm-review's 8.1 line beside ground_truth_status in the wild-ledger
section, and overnight-lab's 8.3 line in [implementation detail withheld].

- **swarm-review — YES, one edit.** 8.1 belongs beside the wild ledger's
  ground_truth_status guidance: **a cross-arm difference in audit/exclusion
  rates is not a result until the matcher has been run position-independently
  over every arm.** The ledger already collects per-beat yields across arms and
  is exactly where someone will be tempted to read an exclusion-rate gap as a
  finding. 8.2 and 8.3 are lane-infrastructure, not review-shape, and belong in
  bench-guide.
- **bench-guide — YES, two edits.** Add 8.2 (verify the isolation posture stayed
  on; audit tool-call parameters, not only paths) and 8.3 (probe read AND write
  on every granted path per lane, with negative controls, as a pre-dispatch
  gate) as numbered conventions alongside #22/#23 from §7.7. Both are
  rig-operating rules an experimenter must follow before dispatch, which is what
  that convention list is for.
- **overnight-lab — YES, one line in [implementation detail withheld].** From 8.3: **an
  unattended chain must fail closed on a permission mismatch *before* it spends,
  and the gate that does that is a differential syscall probe, not an assertion
  in a brief.** All three SWR-1 deaths happened on detached chains; two cost real
  money after the mismatch was already true on disk and checkable for free.
- **codex-sol — NO.** Nothing here is about cross-lineage routing.

**Bound on all three.** One arm, one repo, n=1 per incident, and the arm they
come from produced no measured result — these are apparatus-discipline rules,
not effects, and none carries a registry finding id. They earn their place the
same way §7's did: each was paid for by a wrong answer that a green check had
already certified, and 8.1 was paid for by a *p = 0.018* that did not survive either of the two
checks anyone finally ran on it.

## 9. Strategy selection on bulk edits: the run cost is chosen in the first few turns (2026-09-04, FABLE-EXT + STRAT-TFXL)

Evidence file: bench/reports/fable-ext-results-2026-09-04.md (prereg prereg-fable-ext-2026-09-04.md, P-E1..6, P-S1..2).
Two tasks (tf-bulkedit-xl; docs-bulkedit, since shelved as not work-applicable), 29 new rows, $54, current CLI 2.1.260.

### 9.1 Classify the STRATEGY before reading a cost ratio as a model property
On tree-wide uniform edits the tool-call histogram is bimodal: a scripted run (~25 Bash calls, then verify) and a by-hand
run (100+ Edit/Write calls) pass the same oracle at a 4–6× cost difference. Low effort scripted 18/18 (Opus 5, Fable 5.1);
Opus 5 medium hand-edited 9/10. The intake's "Fable turn-efficiency on long tasks" was this effect (erratum in the intake
report). Rule: **hold effort fixed AND classify each run's strategy (Bash-led vs Edit/Write-led) before a cross-model cost
claim; report strategy mix beside cost.** Bound: two tasks, one ticket class, n=3–6 per cell; the July rows that hand-edited
at low effort are #72-contaminated and on an older CLI, so the CLI's prompt/tool surface is part of what selects the strategy.

### 9.2 For a uniform-edit ticket, ONE standing sentence buys the effort dial's saving without the effort dial
Arm opus5-solo-med-scriptit (Opus 5 medium + appended system prompt "When a change must be applied uniformly across many
files, write and run a script to apply it rather than editing files one at a time; then verify the result") scripted 3/3 and
passed 3/3 on tf-bulkedit-xl at $1.94 vs $9.81 for the same model and effort without the sentence (P-S2 HOLDS, 0.20×).
Rule: **for uniform tree-wide edit tickets, put the one sentence in the standing prompt rather than lowering effort; the
edit must truly be uniform and the acceptance check an end-state check.** Bound: one task, n=3, one wording.

### 9.3 Low effort is not a free lever below the strong tier
Sonnet 5 at low effort took the scripted path 3/3 and failed 3/3 on tf-bulkedit-xl (same missed resources each time);
Sonnet 5 at medium hand-edited and passed 8/9 on the same task. For the weaker tier the effort was buying correctness.
Rule: **an effort cut is a cost lever only where the strategy it selects is one the model executes correctly; verify pass
rate at the lower rung on the task class before adopting it.** Bound: one task, n=3 at low, current CLI.

### 9.4 Skill delta (convention #16, second half)
- **bench-guide — YES, two lines** beside the effort-pinning table: 9.1 (classify strategy from the tool histogram before a
  cross-model cost claim) and 9.2/9.3 (the standing-sentence lever and its bound; low effort must be pass-rate-verified per
  tier). Applied same day, tagged §9.
- **swarm-review, overnight-lab, codex-sol — NO.** Nothing here is about review shape, unattended chains, or routing.
