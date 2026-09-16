# Findings register — public snapshot

> Curated public snapshot, exported 2026-09-16. Historical statements retain their original dates; later corrections may supersede them. Identifiers, code, and fixture/answer-key details are withheld. See [README](../../README.md) for scope and limitations.

Regenerated from the scrubbed findings.json; original source last-updated field: 2026-08-30.

## Status definitions

- **registered**: Prediction recorded before measurement.
- **measured**: Directly observed in a gated experiment, without an independent-instance replication claim.
- **replicated**: Repeated on an independently gated instance or decontaminated replication.
- **directional**: Observed signal with small n or another material uncertainty that limits magnitude claims.
- **derived**: Arithmetic consequence of measured inputs rather than a directly randomized condition.
- **modeled**: Scenario estimate dependent on stated assumptions.
- **retracted**: Former claim invalidated by contamination, correction, or stronger evidence.

## Findings

### Prompt caching dominates the tested routing gains

- ID: prompt-cache-leverage
- Status: **measured**

**claim**

The benchmark's representative median agentic run was about 5x more expensive when cache reads were repriced as ordinary input at the same Sonnet 5 promotional table.

**scope**

Claude Code benchmark usage, API-list conversion, Sonnet 5 promotional price view.

**caveats**

- This is not a direct measurement of the marginal saving on the [organization withheld] Vertex endpoint.
- The reconciled workplace ledger shows caching was active and one-hour writes were already present for part of the historical window.
- The standard post-promotion view is a separate price table and must not be mixed into the 5x figure.

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

anthropic-list-2026-07-12-sonnet5-promo

**recommendation eligible**

true

### Unique-message accounting substantially reconciles the workplace ledger

- ID: work-ledger-dedup-reconciliation
- Status: **directional**

**claim**

The user-transferred unique-message ledger estimated $133.85 for the aligned window versus an approximately $150 observed bill, while the matching client aggregate estimated $318.43.

**scope**

Historical workplace Claude Code window; aggregate summaries transferred by the user, without source records leaving the work boundary.

**caveats**

- The personal-machine review could not reproduce the calculation from source records.
- Unique message ID is a proxy for billable request identity, not an invoice key.
- The remaining 10.77% difference may include window, price, model-mix, or record-coverage mismatch.

**evidence**

- bench/reports/workplace-cache-audit-addendum-2026-07-14.md

**price table id**

null

**recommendation eligible**

false

### One-hour cache writes were already present in the workplace ledger

- ID: workplace-one-hour-cache-adoption
- Status: **directional**

**claim**

The deduplicated mixed historical window reported 91.24% five-minute and 8.76% one-hour cache-write tokens, disproving the earlier zero-adoption claim.

**scope**

Historical workplace Claude Code write tokens in the user-transferred aggregate summary.

**caveats**

- The window mixes sessions from before and after the setting change.
- Write-token share does not measure prefix reuse or realized savings.
- Post-enable coverage and contract-specific break-even remain unmeasured.

**evidence**

- bench/reports/workplace-cache-audit-addendum-2026-07-14.md

**price table id**

null

**recommendation eligible**

false

### Warm follow-up turns amortize initialization cost

- ID: warm-same-model-batching
- Status: **derived**

**claim**

On the small dialogue workload, a $0.082 cold start and $0.013 warm follow-up imply approximately 56%, 68%, and 76% savings when batching 3, 5, and 10 small related tasks.

**scope**

Small Q&A-scale resumed dialogues; same-model warm sessions.

**caveats**

- The batching percentages are derived, not directly randomized batch treatments.
- Large agentic tasks have a smaller initialization share.

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

anthropic-list-2026-07-12-sonnet5-promo

**recommendation eligible**

true

### Low effort and terse output reduce routine-work overhead

- ID: capable-low-terse-default
- Status: **measured**

**claim**

Sonnet low effort retained quality on the tested incident and sweep cells while reducing latency; terse plus low effort reduced dialogue output by 59% and short-dialogue cost by 11% with the load-bearing facts intact.

**scope**

Selected Sonnet task shapes and scripted multi-turn dialogues.

**caveats**

- Low effort is primarily a latency and attention lever in short sessions.
- The result does not establish quality parity on every task family.

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

anthropic-list-2026-07-12-sonnet5-promo

**recommendation eligible**

true

### Cheap-first routing needs a reliable shape-specific gate

- ID: shape-gated-cheap-first
- Status: **measured**

**claim**

Cheap-first saved cost on bounded format work but lost cost and latency on sweep and judgment work where cheap-tier failure was frequent.

**scope**

Format, Terraform sweep, and Azure incident cascade cells using benchmark oracles as escalation gates.

**caveats**

- The format saving magnitude used a small strong-model baseline.
- Production gates are not free or perfect.

**evidence**

- bench/reports/batchD-cascade-economics.md
- bench/reports/synthesis-2026-07-11.md

**price table id**

anthropic-list-2026-07-12-sonnet5-promo

**recommendation eligible**

true

### External verification is more reliable than self-report

- ID: external-verification-required
- Status: **measured**

**claim**

Haiku never self-escalated in 16 canary runs, while a separate Haiku reviewer caught every parseable real failure; production must treat an unparseable reviewer response as escalation.

**scope**

Canary tasks and archived bulk-tag workdirs.

**caveats**

- Raw detector recall was 73% when unparseable outputs were counted as misses.
- The 100% operational recall requires fail-closed wiring.

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

null

**recommendation eligible**

true

### Naive natural-language delegation loses task-defining information

- ID: avoid-naive-delegation
- Status: **measured**

**claim**

Across the tested IaC scales and delegation variants, delegation never saved money per correct result; at XL the parent handoff systematically omitted taggable-but-untagged resources.

**scope**

Synthetic Terraform authoring and repository-wide migration tasks through XL.

**caveats**

- Most variants share one generated repository family.
- The result does not prohibit additive fan-out with independently verifiable outputs.

**evidence**

- bench/reports/xl-delegation-dive-2026-07-11.md
- bench/reports/synthesis-2026-07-11.md

**price table id**

anthropic-list-2026-07-12-sonnet5-promo

**recommendation eligible**

true

### A mandated closing census can rescue a cheap sweep

- ID: checked-haiku-sweep-rescue
- Status: **measured**

**claim**

One explicit self-check instruction reduced the canonical Haiku bulk-tag failure rate from 69% to 12.5% in the first-run-per-repetition analysis.

**scope**

One Terraform tag-standardization instance.

**caveats**

- This is a prompt variant on one instance, not an independent-family replication.
- At promotional prices its cost per correct was near Sonnet rather than clearly cheaper.
- The tool-side analogue was later measured on the same task family: a runnable checker took Haiku to 6 of 6 with verified checker consumption (live-checker-rescue-tf-sweep).

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

anthropic-list-2026-07-12-sonnet5-promo

**recommendation eligible**

false

### Readable symptom probe rescues the incident knowledge cliff

- ID: readable-probe-knowledge-rescue
- Status: **retracted**

**claim**

The original Batch K analysis attributed a 100% to 33% failure reduction to iterative symptom feedback.

**scope**

Private-endpoint incident Batch K only.

**caveats**

- The agent could inspect mechanism-bearing checker source through shell commands.
- 2026-07-24 census: the original 'rescue' occurred with zero probe executions, so it was entirely checker-source leakage; its superseding finding sealed-feedback-knowledge-cliff was itself retracted 2026-07-24 (probe never executable). See erratum-environment-2026-07-24.md.

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

null

**recommendation eligible**

false

**superseded by**

sealed-feedback-knowledge-cliff

### Symptom-only iteration does not supply missing Azure knowledge

- ID: sealed-feedback-knowledge-cliff
- Status: **retracted**

**claim**

RETRACTED 2026-07-24: the claim asserted Haiku failed 5 of 6 incident runs 'despite repeatedly executing the symptom checker'; a paired per-call census shows the sealed probe was executed ZERO times in any K/K2 run — every execution attempt (26/26 across pe fb/fb2) was auto-denied by the tested-run permission settings. Symptom-feedback iteration was never actually tested.

**scope**

Private-endpoint DNS mechanism, baseline plus decontaminated K2 replication.

**caveats**

- The knowledge-cliff question is OPEN, not answered; replacement experiment is the pe live-probe replication (roadmap section 0, R4) under settings.tested.checker.json.
- The raw 5/6 fail rate survives only as a no-feedback measurement (probe unavailable in practice).
- Successor experiment complete: R4b (2026-07-25) ran the live probe with the decode channel closed and returned 3 of 6. The strong form of the cliff thesis is dead — half the runs passed — but rescue is not established either. See pe-live-probe-indeterminate.

**evidence**

- bench/reports/erratum-environment-2026-07-24.md
- bench/reports/correction-k2-checker-2026-07-24.md
- bench/reports/synthesis-2026-07-11.md

**price table id**

null

**recommendation eligible**

false

**superseded by**

pe-live-probe-indeterminate

### A live symptom probe leaves the private-endpoint knowledge cliff unresolved

- ID: pe-live-probe-indeterminate
- Status: **measured**

**claim**

Batch R4b ran Haiku on the sealed private-endpoint incident with the symptom probe genuinely executable and the decode channel closed: 3 of 6 scored runs passed (r22, r24, r26) on 19 verified probe executions with zero probe-only denials. The registered prediction P-R4b-1 (at most 2 of 6 — the knowledge cliff holds) is FALSIFIED, while 3 of 6 sits inside the registered indeterminate band, so rescue is not established either. Cost per correct was $0.79 billed ($2.36 over the six scored runs, $2.96 including the pilot, against a $5 cap).

**scope**

One private-endpoint DNS incident instance (pe-incident-fb2, private-endpoint-dns-inc-4821), Haiku, n=6 scored plus an unscored pilot, under settings.tested.checker.pe2.json.

**caveats**

- 3 of 6 is the registered indeterminate band: the frozen rule needed at most 2 of 6 to confirm the cliff and at least 4 of 6 to falsify it, so neither branch resolved and no successor finding claims a cliff.
- The registered consequence is binding: the next pe spend goes to instance breadth (independent incident mechanisms), not more reps on this fixture; roadmap section 5 may no longer be motivated by an absolute cliff.
- Iteration count did not predict success — the passing runs used 5, 2 and 2 probe executions, while the hardest-iterating run (r27: 6 executions, 10 attempts, 1029 s, $0.65) failed and was the most expensive in the batch.
- Cross-environment comparisons only: the R4-era dead-probe 0 of 3 and the historical sealed baseline are not contemporaneous controls, and the prereg's attribution clause was struck because R4b ran no control arm.
- Registered-scope deviation: the plan-phase terraform guard did not yet exist, so two scored runs (r23, r27) and the pilot (r21) attempted terraform apply against the real Azure subscription and had live cloud feedback available; r21, r23 and r27 each left orphaned resource groups. All three passing runs made zero apply attempts, so the live channel manufactured no pass. See erratum-plan-phase-apply-2026-07-25.md.
- All six scored runs plus the pilot audited CLEAN on the decode channel (zero undenied decode utilities, zero terraform-transitive channels, zero decoded-payload tokens), re-derived from transcripts on 2026-07-25; the earlier R4 attempt was unscoreable with 4 of 6 runs contaminated.

**evidence**

- bench/reports/batch-r4b-2026-07-25.md
- bench/reports/prereg-batch-r4-pe-live-probe-2026-07-24.md
- bench/reports/sol-review-batch-r4b-prereg-2026-07-25.md
- bench/reports/batch-night-2026-07-25.md
- bench/reports/erratum-plan-phase-apply-2026-07-25.md

**price table id**

null

**recommendation eligible**

false

### A live, verified checker loop lifts a cheap model to ceiling on the tag sweep

- ID: live-checker-rescue-tf-sweep
- Status: **measured**

**claim**

With the checker actually executable, Haiku passed 6 of 6 scored runs on tf-bulk-tags-fb2 (7 of 7 including the pilot) at about $0.34 billed per run, and the mechanism-payload cell t-L5 passed 3 of 3. Checker consumption was verified from tool results: 21 successful executions across the live cells with zero denials, against 0 executions and 12 denials in the dead-checker control. The pooled dead control (t-L0d r61-r69, including the C1 bump) passed 3 of 9, a +67pp differential. Registered prediction P-3b-1 (at least 4 of 6) held, reversing the direction of the retracted K2 headline.

**scope**

One Terraform tag-standardization instance (tf-bulk-tags-fb2), Haiku, n=6 live scored plus n=9 pooled dead control, under settings.tested.checker.json.

**caveats**

- Single instance, and the reps share one byte-frozen fixture: replication depth, not breadth. No family-level claim.
- The absolute result (ceiling with verified checker consumption) is far stronger than the differential. Controls are staggered across eras rather than contemporaneous, and within the common late era the contrast was t-L0 5/5 versus t-L0d 2/2 — 0pp on tiny n. The C1 bump killed the drift theory (the six newest controls went 1 of 6, matching the K2-era rate), but a contemporaneous ABAB design (C2) remains the gold-standard closure.
- P-C1-1 (pooled dead control at least 7 of 9), registered as a bet against our own headline, was falsified.
- The checker is oracle-adjacent, so this is an upper bound on what a partial real test suite would deliver. CORRECTED 2026-08-21: the R7 checker-quality variations are no longer unrun — they ran on 2026-07-25 and 12 scored verdicts sit in bench/results/verdicts/. Counted from the verdict files: t-Lb (bare PASS/FAIL verdict) 6 of 6 oracle-pass at $0.40 mean billed, t-Lw (deliberately incomplete checker) 6 of 6 at $0.34. They did not discriminate checker quality: t-L0, t-Lb and t-Lw all sit at 6 of 6, so this fixture is at ceiling for all three arms and cannot separate them, and the registered false-green rate came back zero only on a task cheap models already clear. 1 of 6 t-Lw runs read the checker source — the contamination channel the realism audit flagged for exactly this measurement — and excluding it leaves 5 of 5 and moves nothing.
- This settles only the sweep half of the loop question; the incident-diagnosis half is pe-live-probe-indeterminate, which did not resolve.

**evidence**

- bench/reports/batch-t3b-2026-07-24.md
- bench/reports/batch-night-2026-07-25.md
- bench/reports/prereg-batch-t3b-2026-07-24.md
- bench/reports/sol-review-batch-t3b-results-2026-07-24.md
- bench/reports/correction-k2-checker-2026-07-24.md
- bench/reports/batch-night2-2026-07-26.md

**price table id**

null

**recommendation eligible**

false

### A bare "your previous attempt failed" bit is the load-bearing feedback grade

- ID: bare-fail-bit-feedback-grade
- Status: **measured**

**claim**

On the tf-bulk-tags retry cells the bare fail-bit arm t-F1 passed 4 of 4 against pooled controls of 5 of 8 (pristine retry t-F0 2 of 4, seeded no-payload t-F0n 3 of 4) — a 37.5pp gap that FALSIFIED the registered gradient-null prediction P-3b-4 (at most 25pp). The richer location-list payload t-F3 also passed 4 of 4, adding nothing measurable over the bare bit.

**scope**

One Terraform tag-standardization instance (tf-bulk-tags), Haiku retry cells, n=4 per arm across two cohorts (2026-07-18 and 2026-07-24).

**caveats**

- n=4 per arm. The F1 effect is cohort-stable (2 of 2 in both cohorts) but the control base drifted upward between them (2 of 4, then 3 of 4).
- Single instance; no family-level claim.
- We registered that phase 3's F1 2 of 2 was noise. It was not — the prediction is on the record as falsified.
- One control run (t-F0n r33) was lost to infra error and is archived, not counted; the cell was re-run to n=4.

**evidence**

- bench/reports/batch-t3b-2026-07-24.md
- bench/reports/prereg-batch-t3b-2026-07-24.md
- bench/reports/sol-review-batch-t3b-results-2026-07-24.md

**price table id**

null

**recommendation eligible**

false

### A strong closing verifier rescued every XL sandwich run

- ID: strong-closing-verifier-xl
- Status: **measured**

**claim**

The XL sandwich passed 4 of 4 runs only after the strong verifier repaired all four failed cheap-executor end states, at roughly 1.2x solo billed cost.

**scope**

One XL generated Terraform repository instance.

**caveats**

- This was a reliability purchase, not a token saving.
- All four cheap executor legs failed.

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

null

**recommendation eligible**

false

### Staging crossed over at XXL when solo hit the wall-clock boundary

- ID: sandwich-xxl-crossover
- Status: **directional**

**claim**

At XXL the sandwich passed 2 of 2 while solo passed 1 of 2, making the staged expected cost per correct lower under the observed outcomes. CORRECTED 2026-08-21: do not quote this as a live directional crossover. The solo leg's single failure was a wall-clock kill under a 2700s cap, and the uncapped rerun completed — Opus 5 solo finished the same XXL migration with an oracle pass on 2026-08-01 ($172.74 billed, 1080 turns, 82 minutes). The 1-of-2 solo denominator is a cap artifact, not a capability limit.

**scope**

One generated XXL Terraform repository, n=2 per architecture.

**caveats**

- The direction is clean but the sample is too small for a stable magnitude.
- The solo failure was a wall-clock kill under a fixed cap.
- 2026-07-25 (Evan's wall-clock challenge): the solo 'crack' is CAP-RELATIVE — the killed run exceeded a 2700s harness guard rail chosen for chain throughput and hang detection, not a measured inability to complete; under a parallel-fleet operating model where latency is costless, completion beyond the cap is simply unmeasured. Only 2 of 509 scored runs have ever been wall-clock-killed (recounted from verdicts 2026-07-25). Any O5-d rerun must use a generous cap and record time-to-completion so the crossover can be tested cap-independent.

**evidence**

- bench/reports/synthesis-2026-07-11.md
- bench/reports/day-note-2026-08-01.md

**price table id**

null

**recommendation eligible**

false

**correction**

CORRECTED 2026-08-21 (findings-recon-2026-08-21.md): the solo leg is void as evidence of a capability crossover. xxl-solo-uncapped-completion ran the same XXL instance under the registered O5-d generous-cap design change and Opus 5 solo completed with an oracle pass — $172.74 billed, 1080 turns, 82 minutes, 2026-08-01, verified from bench/results/verdicts/tf-bulkedit-xxl__opus5-solo-med__r2__20260801-040633.json. This is a PARTIAL correction, not a supersession, so no superseded_by is set: the staging leg (2 of 2) is untouched and the staged-versus-solo comparison at uncapped settings is still unrun. At the smaller XL scale the crossover was measured and ran the other way (opus5-xl-solo-cheapest-per-correct: solo $9.81 per correct vs the staged pipeline's $12.68). Whether this entry should be demoted from directional to retracted needs judgment beyond what a file on disk settles and is left to the daytime session.

### At a 25-minute gap, 1-hour cache TTL beat cold rewrite and pings

- ID: cache-gap-25m-ordering
- Status: **measured**

**claim**

The measured event cost ordered 1-hour TTL at $0.137, cold rewrite at $0.172, and keep-alive pings at $0.286.

**scope**

One account, one 25-minute API gap condition.

**caveats**

- Single-duration, low-n measurement; not measured on [organization withheld] Vertex.
- Do not generalize the exact dollar amounts across context sizes.

**evidence**

- bench/reports/synthesis-2026-07-11.md
- bench/results/cachegap

**price table id**

null

**recommendation eligible**

false

### Higher effort can hurt exact repository cleanliness

- ID: higher-effort-exactness-risk
- Status: **directional**

**claim**

Sonnet high failed all four strict docs-bulkedit runs, commonly by leaving helper scripts in the tree, while effort did not improve the task's content reliability.

**scope**

One byte-exact documentation bulk-edit instance.

**caveats**

- The strict extra-file rule magnifies a real but task-specific workstyle failure.
- n=4 for the high-effort arm.
- The failure mode has a cheap prompt-side guard: a one-sentence no-extra-files constraint put the low-effort arm at 5 of 6 (docs-exactness-constraint-guard).

**evidence**

- bench/reports/synthesis-2026-07-11.md

**price table id**

null

**recommendation eligible**

false

### A one-sentence no-extra-files constraint guards byte-exact repository work

- ID: docs-exactness-constraint-guard
- Status: **measured**

**claim**

Adding a single appended system-prompt sentence stating the no-extra-files constraint (arm t-Gg) put Sonnet 5 low at 5 of 6 on the strict docs-bulkedit task at $4.75 billed per run, against 4 of 6 for the otherwise identical unguarded arm. The competing remediation guard (t-Gc, an end-of-run file census plus cleanup) passed only 1 of 4 and falsified P-T3-9.

**scope**

One byte-exact documentation bulk-edit instance (docs-bulkedit, confluence-space-migration-v1), Sonnet 5 low, n=6 guarded and n=4 census.

**caveats**

- The matched pristine control (arm sonnet-low: identical model, effort and tool policy, no appended sentence) is a 2026-07-12 pre-manifest cell recording no instance id, so the contrast is +17pp across a 12-day gap, not a contemporaneous randomization. The batch report's own headline instead compared against the seeded t-Dp arm at 1 of 4.
- r5 is the guard's first failure; the arm was 4 of 4 before it. Single instance, and adoption was registered as pending replication on a second docs instance.
- The prevention-beats-remediation split is partly structural: the tested environment can create files but never delete them (rm is denied), so the census arm detected its own droppings and had no way to remove them.
- The guard redirects rather than suppresses the scratch impulse — the r1 transcript shows the agent writing its fixup script to /tmp, outside the oracle's field of view.

**evidence**

- bench/reports/batch-t3-2026-07-24.md
- bench/reports/batch-t3b-2026-07-24.md
- bench/reports/prereg-batch-t3-2026-07-18.md
- bench/reports/erratum-environment-2026-07-24.md

**price table id**

null

**recommendation eligible**

false

### Opus 5 lowers frontier-tier cost per correct at unchanged token price

- ID: opus5-frontier-cost-per-correct
- Status: **directional**

**claim**

On the first three anchor cells (n=3 each, billed subscription cost) Opus 5 passed 3 of 3 on tf-bulk-tags at $1.14 per correct, 2 of 3 on pe-incident at $0.83 per correct, and 3 of 3 on the strict docs-bulkedit task at $4.93 per correct — cheaper per correct result than the Sonnet 5 low docs anchor ($7.13 per correct, 4 of 6) and the Opus 4.8 low docs anchor ($5.99 per correct, 4 of 4), at a list token price identical to Opus 4.8's. Registered predictions P-O5-1, P-O5-2 and P-O5-3 all held.

**scope**

Three task families, one instance each, solo arms, n=3 per cell, billed CLI costs; the docs anchors are 2026-07-12 rows compared against 2026-07-24 runs.

**caveats**

- n=3 per cell, one instance per family, solo arms only; no Fable comparison, and no cache-economics claim (pricing.json's Opus 5 cache multipliers are an assumption pending verification against the API docs).
- The night report's cache-neutral standard-table figures ($32.01 per correct for Opus 5 low docs versus $33.63 Sonnet low and $40.56 Opus 4.8 low) cannot currently be re-derived: aggregate.py raises PricingError on exactly these rows, and all nine Opus 5 verdicts carry usage_by_model cache_write_1h greater than cache_write while the 2026-07-12 Sonnet and Opus 4.8 docs anchors do not. Until the field-authority question is settled, only the billed figures above are safe to quote.
- The docs anchors were run 12 days earlier, before the manifest era, and record no instance id; they are anchors, not contemporaneous controls.
- An earlier draft's claim that Opus 5 was the cheapest correct route across the pe incident was withdrawn: Sonnet low is, at $0.47 per correct billed (5 of 6). The pe failure is specific to the Haiku solo arm (0 of 11 scored runs on pe-incident; the commonly quoted "0 of 13" counts two rate-limit rows that the pre-registered exit-reason taxonomy excludes), not to cheap models generally — Haiku's canary and high-effort arms each passed 1 of 6, and Haiku on the feedback variants pe-incident-fb/fb2 passed 5 of 12.
- CORRECTED 2026-08-21: O5-d is no longer unrun. The XL solo cell ran 4 of 4 oracle-pass at $9.81 mean billed (tf-bulkedit-xl opus5-solo-med r411-r414, 2026-08-08/09, counted from verdicts) and is registered as opus5-xl-solo-cheapest-per-correct, which measured the solo-versus-staging crossover directly and refuted the crossover predictions P-O5-2 and P-O5-3; the XXL leg completed uncapped on 2026-08-01 at $172.74 billed, 1080 turns, 82 minutes (xxl-solo-uncapped-completion). What survives is only the narrower statement: this entry's own three anchor cells are n=3, one instance per family, and do not themselves speak to the crossover — cite the two entries named above for that, not this one.

**evidence**

- bench/reports/batch-night-2026-07-25.md
- bench/reports/prereg-night-2026-07-24.md
- bench/reports/sol-review-night-results-2026-07-25.md
- bench/reports/roadmap.md
- bench/reports/batch-o5xl-2026-08-09.md

**price table id**

null

**recommendation eligible**

false

### Judgment-shaped decommission work separates model tiers categorically

- ID: judgment-family-tier-separation
- Status: **replicated**

**claim**

Under the frozen n=6 pre-registration across three independent landmine mechanisms (storage-backend kv, NSG-subnet net, key-vault), Haiku passed 1 of 19 (including the upheld r105), while Sonnet passed 18 of 18 (after the r106 sentinel-dialect correction) and Opus 5 passed 18 of 18. Haiku's failures are the catastrophic kind: confidently deleting the load-bearing resource. The three-instance family rule is met; the family GRADUATED 2026-08-01.

**scope**

decommission-judgment family, three gated instances, Claude tiers, frozen prereg n=6 per cell.

**caveats**

- The strong tier is at ceiling (sonnet = opus5 = 18/18), so the family cannot discriminate WITHIN the strong tier; separating Sonnet from Opus/Fable needs 17h adversarial instances.
- A one-line 'check dependencies' prompt moved Haiku only 0/3 to 2/6 — not significant at these n (Wilson CIs overlap); you cannot cheap-prompt seniority with one line.
- The 17g 2x2 later separated the mechanism: strong-tier wins combine hazard DETECTION and a conservative action disposition (see judgment-detection-vs-disposition-2x2).

**evidence**

- bench/reports/consolidated-assessment-2026-08-01.md
- bench/reports/day-note-2026-08-01.md
- bench/reports/batch-17g-2x2-2026-08-01.md

**price table id**

null

**recommendation eligible**

true

### Cheap tiers lack hazard detection; strong Claude adds a caution disposition; the vendor split is clean

- ID: judgment-detection-vs-disposition-2x2
- Status: **measured**

**claim**

The 17g construct-validity 2x2 (72 runs, v2 fixtures, zero infra losses) separated the axes: Haiku never flags the landmine even at tag-stakes (FN 0/6, names none), Luna is intermediate (3/6) — detection, not deletion-aversion, is what cheap tiers lack. On the sound-instruction delete cell (SD), sonnet and opus5 declined the decoy deletion pending confirmation in 12 of 12 runs while Luna and Haiku deleted without a verified record. Evan ruled CONFIRM-FIRST (2026-08-01): under the revised hold-decoy-and-ask key, sonnet 6/6, opus5 6/6, haiku 0/6, luna 0/6. Zero of 30 SD runs across four models produced the original key's verify-cite-delete behavior.

**scope**

decommission-judgment-tag / -sound / control instances; haiku, sonnet, opus5 (Claude) and Luna (codex, tokens-only); n=6 per cell.

**caveats**

- AMENDED 2026-08-01 night (verdict-amendment-sd-2026-08-01.md): revised-key scores are formally amended on the END-STATE dimension only (sonnet 6/6, opus5 6/6, haiku 0/9, luna 0/6, doubly replayed); the record dimension is explicitly UNSCORED — two regex implementations failed cross-lineage review in opposite directions (round 2: ~9/10 fresh genuine phrasings rejected, 4/5 gaming attempts accepted), so scoring it awaits Evan's mechanism decision. SD runs HELD.
- 4 of 6 Haiku SD runs wrote a 'Verified' line citing the WRONG resource; the SD-v3 review (2026-08-01 night) found 5 of 12 STRONG-tier runs did the same to satisfy the fixture README's mandated Verified: slot — the wrong-resource lines are substantially template-forced, so this observation no longer independently supports the decorative-prose reading and the fixture template is being fixed in v3.
- The 0/30 verify-cite-delete observation is either an over-demanding key or real verify-then-act headroom above every tested tier — registered as a 17h candidate (does Fable verify-and-delete?).

**evidence**

- bench/reports/batch-17g-2x2-2026-08-01.md
- bench/reports/design-17g-2x2-2026-07-31.md

**price table id**

null

**recommendation eligible**

false

### Luna (cheap GPT-5.6) genuinely deletes the production vault and effort does not rescue it

- ID: luna-vault-deletion
- Status: **measured**

**claim**

Under the frozen GPT-day prereg, Luna deleted the load-bearing vault in 11 of 12 judgment runs across reasoning-effort settings; high effort does not rescue it. Luna is simultaneously competent at bounded bulk mechanical edits (5/6) and its docs weakness is specific to omission-DETECTION, not editing. It is not a Haiku upgrade for judgment work; Haiku's SD behavior (delete-without-verifying) matches Luna, not Luna's strong-tier siblings.

**scope**

Codex-dispatched GPT-5.6 Luna arms on offline judgment and docs instances; tokens+meter accounting only.

**caveats**

- Codex scaffold and host configuration ride along in every GPT number (runner-v2 configuration isolation is unbuilt — issue #41).
- Subscription billing: no USD comparability with Max-billed Claude rows (convention #5/#15).
- All judgment passes were protocol-screened via the codex command_execution evidence path.
- 2026-07-30 API price cut (Luna to $0.20/$1.20 per Mtok list) strengthens the bulk-edit economics but changes nothing about the judgment routing verdict.

**evidence**

- bench/reports/consolidated-assessment-2026-08-01.md
- bench/reports/day-note-2026-08-01.md
- bench/results/protocol_screens_gpt_2026-08-01.jsonl

**price table id**

null

**recommendation eligible**

true

### Our own verifiers failed twice by being calibrated on Claude phrasing

- ID: verifier-dialect-calibration-failures
- Status: **measured**

**claim**

Two independent scoring failures were found and corrected with audit trails on 2026-08-01: the r106 sentinel missed a legitimate Sonnet command shape (dialect gap), and the kv/net evidence-token lists scored a semantically correct GPT (Sol) agent 0/6 — 6/6 after the Evan-approved v2 token lists and 10-row adjudication. A false vendor-separation headline (Sol below strong Claude on judgment) was retracted within two hours on Evan's skepticism.

**scope**

Judgment-family sentinels and kv/net verifiers; corrections re-gated before adoption.

**caveats**

- Generalizable law (mirrors the program's forward finding): a check that cannot distinguish a real solution from a differently-phrased one silently mis-routes trust.
- Consequence is structural, not one-off: cross-dialect oracle gates are now required (bench-guide #14/#15), and any judgment pass under codex needs the protocol screen because Claude-format sentinels cannot parse codex transcripts.

**evidence**

- bench/reports/correction-kv-dialect-2026-08-01.md
- bench/reports/day-note-2026-08-01.md
- bench/reports/consolidated-assessment-2026-08-01.md

**price table id**

null

**recommendation eligible**

false

### Given room, Opus 5 solo completes the XXL migration

- ID: xxl-solo-uncapped-completion
- Status: **measured**

**claim**

With a generous cap per the registered O5-d design change, Opus 5 solo completed the repo-wide XXL migration with an oracle pass: $172.74 billed, 82 minutes, 1080 turns (2026-08-01, sixth attempt across three days; prior attempts died to rate-limit walls, not capability). The old 'solo cracks at XXL' reading was cap-relative; one strong context holds the whole problem when allowed to finish.

**scope**

One generated XXL Terraform repository, Opus 5 solo, n=1 completed run.

**caveats**

- n=1; the optional $173 confirmation rep (r3) is PARKED per Evan.
- This does not price the crossover — it removes the cap artifact from sandwich-xxl-crossover's solo leg; the staging comparison at uncapped settings is unrun.
- Session economics, not ideas, were the binding constraint (six attempts to land one run) — the standing argument for the section-14 cloud runner.

**evidence**

- bench/reports/day-note-2026-08-01.md
- bench/reports/consolidated-assessment-2026-08-01.md

**price table id**

null

**recommendation eligible**

false

### Haiku does not seek reference information through any channel

- ID: cheap-tier-information-seeking-absent
- Status: **measured**

**claim**

Across a four-cell pre-registered ladder on the pe-incident knowledge task (n=6 per cell, contemporaneous, 24 runs, $4.04): haiku scored 0/6 in every cell and the mechanism censuses show it never attempted a whitelisted Microsoft Learn fetch when available (0 attempts), never attempted one when explicitly told the channel exists (0 attempts), and never opened the relevant documentation page saved as a file in its own working directory (present in all 6 workdirs; zero reads). It attacks tasks directly from parametric knowledge. Sixth consecutive prompt/affordance intervention with a null behavioral effect on haiku.

**scope**

pe-incident instance, haiku-4.5, four registered cells (no-docs control, fetch-available, fetch-nudged, docs-as-workdir-file); censuses verified from tool-result channels.

**caveats**

- One task instance and one cheap model; the ladder should be spot-checked on a second knowledge-shaped instance before family-level phrasing.
- Says nothing about strong tiers - whether docs access lifts sonnet on hard knowledge work is open, blocked on a task with strong-tier headroom (17h).
- The knowledge-application question (P-DOCS-7) remains unengaged: it cannot be tested in a model that never ingests the reference; push-into-loop delivery (prompt-embedded or checker-delivered) is the remaining untested channel.
- Contrast finding, same program: sonnet followed a one-sentence budget instruction to a 49% cost reduction (batch-a2-softbudget-2026-08-02.md) - instruction-following and information-seeking are tier-graded capabilities, not configuration.

**evidence**

- bench/reports/batch-docs1-2026-08-02.md
- bench/reports/prereg-docs1-pe-v2-2026-08-02.md
- bench/runner/GATE-docs-settings-2026-08-02.md

**price table id**

null

**recommendation eligible**

true

### Exhaustive-census weakness is a cheap-tier trait, not a GPT-family trait; the effort dial does not rescue it

- ID: census-weakness-cheap-tier-not-family
- Status: **measured**

**claim**

On docs-omissions (find every disagreement between a RASIC matrix and its narrative, under a strict output schema), Sol (GPT-5.6 large tier) scored 6/6 where Luna (GPT-5.6 cheap tier) scored 1/6 the prior night - the census weakness does not run in the vendor family. The mechanical-sweep control (docs-bulkedit, floor task) shows Luna 5/6: the cheap tier can SWEEP exhaustively; what it cannot do is judgment-shaped exhaustiveness. Raising Luna's reasoning effort to high on the judgment landmines spent 1.3-1.9x the tokens and 4-5x the reasoning tokens of Sol-medium to score worse (net 1/6, kv 0/6 frozen), and in 10 of 12 failing runs it confidently deleted the load-bearing resource - effort is not a substitute for hazard detection.

**scope**

GPT-5.6 tiers via codex CLI, r20x stratum 2026-08-01, n=6/cell; codex host config not isolated (registered limitation); kv/net frozen scores carry the dialect-correction dual reading (correction-kv-dialect-2026-08-01.md).

**caveats**

- One vendor pair; the Claude-side analogue (haiku vs sonnet on docs-omissions) is partially measured (haiku 2/4) and not under the same prereg.
- Token comparison is within-vendor only; no USD is computed for codex runs (convention #5/#15).
- n=6 per cell: only near-total separations (1/6 vs 6/6) carry weight here, per convention #12.

**evidence**

- bench/reports/batch-gpt-day-2026-08-07.md
- bench/reports/prereg-gpt-day-2026-08-01.md
- bench/reports/correction-kv-dialect-2026-08-01.md

**price table id**

null

**recommendation eligible**

true

### The soft budget sentence is a shape-specific lever, not a universal one

- ID: soft-budget-prompt-scope-limited
- Status: **measured**

**claim**

One appended system-prompt sentence asking sonnet to aim for ~25 turns cut billed cost 49% among passes on the XL repo-wide Terraform edit (n=3v4, 2026-08-02) but only 6.6% on docs-bulkedit (1/3 vs 2/3 pass, n=3v3) and 10.2% on tf-bulk-tags (3/3 both) in fresh interleaved replications (2026-08-07). Registered family rule (>=2 of 3 instances at >=15%) NOT met: no family claim. Mechanism per turn counts: the sentence removes redundant re-reading/re-verification turns; where a task has no such fat (compact runs, exactness-dominated runs), it does roughly nothing.

**scope**

sonnet-5 medium effort, three task instances, promo-era billed prices, 3v3 or 3v4 per cell; strata never pooled.

**caveats**

- Small n per cell; only the XL effect size is outside small-n noise.
- docs-bulkedit control passed 1/3 today vs 7/8 in the July stratum - environment drift possible, flagged not interpreted.
- Turn-count mediation is inferred from totals, not from transcript-level classification of removed turns.
- price_table_id schema fix 2026-08-16: figures are cost_usd_billed (CLI-billed, convention #5), not a report-time price table; field nulled, basis recorded here.

**evidence**

- bench/reports/batch-burnday-2026-08-07.md
- bench/reports/batch-a2-softbudget-2026-08-02.md
- bench/reports/prereg-burnday-2026-08-07.md

**price table id**

null

**recommendation eligible**

true

### At XL scale, Opus 5 solo beat both Sonnet solo and the staged pipeline on cost-per-correct

- ID: opus5-xl-solo-cheapest-per-correct
- Status: **retracted**

**claim**

tf-bulkedit-xl opus5-solo-med went 4/4 oracle-pass at mean $9.81 billed per correct (reps 411-414, 2026-08-08/09, serial detached chains), beating sonnet-solo's $11.86 (3/3; corrected 2026-08-21 — the published $12.35 (3/4) priced an infra-error row in, convention #4, met1-sensitivity-retro) and the staged pipeline's $12.68 (corrected 2026-08-17 from the erroneous $11.58). P-O5-1 confirmed; P-O5-2 and P-O5-3 (crossover) refuted as preregistered in prereg-o5-2026-08-07.md. The prior ~$16/pass belief from n=2 July runs was a small-sample artifact.

**scope**

One XL task instance, n=4, opus5 medium effort, promo-era billed prices, BENCH_PER_RUN_MAX=200; 6 rate-limit rows archived per convention #4. Strata 2026-08 reps only; never pool with July rows (convention #18).

**caveats**

- Single task instance; family claim requires tf-migrate-xl-sparse-1 (draft-ungated) or another XL instance.
- Wilson 95% CI on 4/4 is [0.51, 1.00] - pass-rate itself is directional.
- Comparator baselines may shift under list-price recomputation (registered threat in the prereg).
- Scope boundary measured 2026-08-09: the advantage does NOT extend down-scale — on docs-omissions (easy docs task) opus5-solo-med passed 3/3 at $0.28/correct but July sonnet-solo passes 6/6 at $0.21; pay the O5 premium for hard/XL work only (batch-docsomissions-o5-2026-08-09.md, cross-date strata caveat).
- Evidence-list schema fix 2026-08-16: non-path items moved here: ['verdicts tf-bulkedit-xl__opus5-solo-med__r411-r414']
- Scope annotation (2026-08-22 night, requires-settings-census-2026-08-21.md §4): rows r411-r414 ran with the task-declared requires_settings capability DENIED (auto-denied under settings.tested.json). Result left standing; whether the denial affects the cheapest-per-correct comparison is a daytime review item.
- HOLD RESOLVED -> ORDERING RETRACTED (2026-08-30, hygiene92-c5-2026-08-30.md, issue #92 item 2). The 2026-08-22 HOLD asked for an independent daytime recomputation of the V3 asymmetry. Done, from verdict JSONs on disk, without importing the script under test: the symmetric V3 arithmetic reproduces to the cent. Opus's own-window hidden spend is $7.1265 and its aborted 2026-08-07 XL campaign (8 dispatches, ZERO scored rows) is $38.8705; charging it as V3 already charges the pipeline's aborted 2026-07-11 campaign ($22.6790) gives Opus $85.2184/4 = $21.30/correct against Sonnet $12.35 and the pipeline $19.12. THE ORDERING FLIPS TO Sonnet < pipeline < Opus, exactly as the census predicted. Under V1 ($9.81/$11.86/$12.68) and V2 ($11.59/$12.35/$13.46) it is Opus < Sonnet < pipeline. The ordering is therefore an artifact of an accounting choice, not a measured separation, and is retracted. Two further facts make the retraction unconditional rather than accounting-dependent: (a) tf-bulkedit-xl has carried scoring_class: regression-check -- explicitly excluded from tier-separation scoring -- since 2026-07-31, and C1/C2 are tier-separation claims computed on it (met1-rawcheck-2026-08-30.md s7a); (b) the two arms did not see identical task text (prompt.md gained the offline az replica on 2026-08-02, between the Sonnet 07-10/11 window and the Opus 08-08/09 window; s7b). Doctrine 3.2's 2026-08-30 erratum already says quote NO XL tier ordering in either direction; this registry entry is now aligned with it. The 4/4 pass rate at mean $9.81 billed is untouched and still stands.
- SECOND MECHANISM, ADJUDICATED 2026-08-30 (hygiene92-c5-2026-08-30.md s3): N23's dedup/PASS-conditioned mechanism PARTLY reproduces and its headline direction does NOT. Reproduces exactly: the pooled all-rows median of $4.78 for tf-bulkedit-xl/opus5-solo-med (20 rows on disk), and the point that 9 of the 14 canonical rows are rate-limit crashes. Does NOT reproduce: the deduped median (recount gives $9.04 over 14 canonical rows, not $8.60), and the PASS-conditioned comparison -- recounted, Opus's PASS median is $10.73 (n=5) against sonnet-solo's $14.54 (n=5), i.e. Opus CHEAPER, not dearer. N23's '$11.15 vs $10.74' appears to compare Opus's PASS median against a differently-constructed Sonnet figure (the pooled sonnet-solo median is $10.64 and the sonnet-solo + sonnet-solo-budget PASS median is $10.69) -- i.e. it is an instance of the arm-mismatch confound it names. Its '46% vs 71%' is a production-effective rate (passes over ALL canonical rows, censored included); recounted that is 5/14 = 36% for Opus against 5/7 = 71% for Sonnet, and the convention-#4 scored pass rates are Opus 5/5 and Sonnet 5/6. So: the response-rate asymmetry is real and large; the cost-direction claim is not supported. The retraction above rests on mechanism 1 and on the regression-check exclusion, NOT on this one.

**evidence**

- bench/reports/batch-o5xl-2026-08-09.md
- bench/reports/prereg-o5-2026-08-07.md

**date**

2026-08-09

**correction**

RETRACTED 2026-08-30 (bench/reports/hygiene92-c5-2026-08-30.md, issue #92 item 2). The ORDERING claim in the title -- Opus 5 solo beat both Sonnet solo and the staged pipeline on cost-per-correct at XL -- does not carry. It reverses to Sonnet < pipeline < Opus under symmetric censoring-inclusive accounting (V3 applied to both arms rather than one), and the task it is computed on, tf-bulkedit-xl, has been scoring_class: regression-check -- excluded from tier-separation scoring -- since 2026-07-31. What survives, and is NOT retracted: opus5-solo-med went 4/4 oracle-pass on tf-bulkedit-xl r411-r414 (2026-08-08/09) at mean $9.81 billed. Quote that; do not quote any XL tier ordering in either direction until a live separator task exists.

### Graph-retrieval pilot: the savings appeared where the graph returned nothing

- ID: graph-pilot-savings-dissociated-from-graph-utility
- Status: **measured**

**date**

2026-08-09

**claim**

At 5-28 file scale, a mandated graph-orientation bundle cut pooled tokens 25.2% and cost 9.5% vs control at equal 9/9 pass rate, but the entire win sits in the 28-file exhaustive-edit task where 2 of 3 treatment runs got ZERO graph hits, while the task where the graph delivered 15 hits/run showed no advantage; with 0.5-1.9KB query payloads, the effect is behavioral (forced orientation interrupting Sonnet's enumerate-everything opening), not information delivery.

**scope**

Sonnet 5, 3 small IaC tasks, n=3/cell, single day, bundle attribution only (Amendment 2b).

**caveats**

- Neither frozen kill nor advance rule fired (cost 9.5% vs 10% advance bar; tokens 25.2% vs 15% futility bar).
- One supporting cell; sham control RUN 2026-08-09 and CONFIRMED the behavioral mechanism (see evidence) -- caveat updated 2026-08-11, single-fixture scope still limits acting on this at work.
- Both the memo prior and the cross-lineage reviewer predicted the wrong positive cell (P-GR-4 refuted).
- decommission T,C adjacency broken ~20min by the Amendment 6 rep-collision remedy.
- Evidence-list schema fix 2026-08-16 (was prose): original text preserved here: bench/reports/batch-graphpilot-2026-08-09.md; prereg-graph-pilot-2026-08-08.md Amendments 1-6 | sham control 2026-08-09 (batch-sham-2026-08-09.md): informationless bench-graph (hits=0 always, byte-identical mandate) reproduced the cut -- sham 3,163,258 tok/$2.167 vs interleaved control 4,281,358/$2.422, -26.1% tok, 6/6 pass; sham pooled footprint matches the real treatment's (3,163,591/$2.163). P-SH-1/2/3 all confirmed.

**evidence**

- bench/reports/batch-graphpilot-2026-08-09.md
- bench/reports/prereg-graph-pilot-2026-08-08.md

### Offered != used: Sonnet never voluntarily touched a documented retrieval tool

- ID: offered-tool-adoption-null-sonnet
- Status: **measured**

**date**

2026-08-09

**claim**

Across 3 smokes plus a soft mandate, Sonnet 5 used a documented, allowlisted bench-graph CLI exactly zero times (0 transcript mentions); only a hard audited protocol requirement with an explicit counting rule produced clean compliance, initially as compound-wrapped queries (the #52 batching habit).

**scope**

Sonnet 5, prompt-delivered tool affordance; delivery verified via manifest sha + haiku probe.

**caveats**

- Single model, single affordance channel (appended system prompt); #55 tests skill/MCP channels.
- Evidence-list schema fix 2026-08-16 (was prose): original text preserved here: prereg-graph-pilot-2026-08-08.md Amendments 3-4; batch-graphpilot-2026-08-09.md secondary finding; issue #55

**evidence**

- bench/reports/prereg-graph-pilot-2026-08-08.md
- bench/reports/batch-graphpilot-2026-08-09.md

### A correctness review is not a calibration review — and the split gate caught a broken construct before spend

- ID: calibration-gate-catches-preSpend
- Status: **measured**

**date**

2026-08-09

**claim**

tf-migrate-xl-sparse-1 survived six cross-lineage CORRECTNESS rounds (final: 1,514 adversarial constructions, zero false passes) and then FAILED the separate difficulty/leakage/headroom review: one prompt-derived grep covered 19/20 answer sites, wrapper READMEs documented the alias chain in prose, and the graph treatment had strictly negative headroom vs grep on the fixture; the conditional XL cell was killed at $0 scored spend.

**scope**

Second instance of designed-hard != hard (after tf-state-reconcile, which cost a burned batch); first instance of the explicit calibration gate running BEFORE dispatch.

**caveats**

- The task's ORACLE is sound and reusable; the fixture is what failed (localization collapses to a 30-candidate set).
- The selftest's own anti-shortcut gate used 'at least one miss' where the review threshold is <90% coverage — an executable gate can encode a weaker criterion than the standard it claims to enforce; tighten before reuse.
- Evidence-list schema fix 2026-08-16 (was a prose string): rounds 4-7 of the build report are the operative sections; Sol's calibration memo is archived at [local path withheld] (outside the repo).
- Scope note (PRUNE-1 rev3, 2026-08-22, prune1-retirement-criteria-2026-08-22.md): tf-state-reconcile, cited in scope as the prior designed-hard-!=-hard instance, is now status:retired on validity — saturated at every tier boundary (haiku 3/3, sonnet 4/4, opus 3/3) with a documented CHANGELOG prose leak. Status of this finding is UNCHANGED: it cites the task as a historical lesson, not as a dispatchable cell, and all its verdict rows are retained.

**evidence**

- bench/reports/build-xlsparse-2026-08-08.md
- bench/reports/prereg-graph-pilot-2026-08-08.md

### Worktree-deletion ablation over a git-carrying fixture is not ablation

- ID: ablation-arms-git-history-void
- Status: **measured**

**claim**

The suite-wide line-level leakage sweep (43 tasks) found the three tf-state-reconcile-v2 --ablate arms delete the target document from the worktree while fixture/.git retains it one [implementation detail withheld] away, with [implementation detail withheld] advertising the deletion — the ablation treatment is void for any git-capable agent. Existing data impact (CORRECTED 2026-08-21): the original 'git never touched' execution screen was WRONG — the content-token audit found 8 of 9 scored rows recovered the ablated document via git show/log -p and every oracle pass sat on a recovered row; the tf-state ablate cells are VOID as ablation evidence [ablate-porosity-audit-2026-08-21]. The sweep also independently re-detected the known tf-state-reconcile CHANGELOG ordering leak (tool false-negative check passed). (Sweep date 2026-08-16.)

**scope**

Main suite, 43 auditable tasks; 2 class-(c) leads affecting 4 task dirs; 7 tasks not auditable (layouts listed in report).

**caveats**

- Class-(a)/(b) hits are artifacts of the per-file baseline method, not leads; only class-(c) counts.
- The 15 decommission-family ablate rows are unaffected (fixtures carry no git history).
- Pass-A alone was blind to the prose-ordering leak class; the C-prime probe exists because of that — future sweeps must run all passes.
- Scope note (PRUNE-1 rev3, 2026-08-22, prune1-retirement-criteria-2026-08-22.md): tf-state-reconcile, whose CHANGELOG ordering leak this sweep independently re-detected, is now status:retired on that basis. Status UNCHANGED; the tf-state-reconcile-v2 --ablate arms this finding is actually about remain active.

**evidence**

- bench/reports/leak-sweep-2026-08-16.md
- bench/runner/tools/suite_leakaudit.py
- bench/runner/leakage_ablation.py

**price table id**

null

**recommendation eligible**

false

**correction**

CORRECTED 2026-08-21: the 'capability-not-exercised (git never touched)' execution screen was wrong — the content-token audit (ablate-porosity-audit-2026-08-21, commit 867f391) found 8 of 9 scored rows recovered the ablated document via git show/log -p (rewrite detector fired on all 8) and the ninth attempted; every oracle pass in those cells sat on a recovered row. The cells are VOID as ablation evidence (recovered-excluded n=1). The structural claim (git-carrying fixture => ablation void) stands and is strengthened.

### In attribution labeling, rule application binds — not vocabulary coverage

- ID: annotation-calibration-rule-walks
- Status: **measured**

**date**

2026-08-16

**claim**

Across two pre-registered MH-1 calibration rounds (two blinded Opus annotators, 40 packets each, frozen codebook), the 46-value mechanism vocabulary produced zero other:* escape-hatch uses in 2/2 rounds, while edge-level agreement was bound by rule APPLICATION: round 1 failed Jaccard 0.508 vs 0.60 with tie-break application as the dominant adjudicated cause (16/26 golds); after the registered fix (mandatory tie-break walk + granularity rule in the brief, nothing added to the vocabulary), round 2 passed at 0.780 and the tie-break cause collapsed to 2/17. Round-2's only failing gate (known-answer 15/22) decomposed into gold-pool defects, impeached by blind three-way convergence.

**scope**

MH-1 stage-2 calibration, 40-row stratified subsets of the 1110-row corpus frame; claude-opus-5 annotator pairs; single-instrument (one codebook).

**caveats**

- Two rounds, same model family for gated annotators; cross-model telemetry (Sonnet) agreement on the hardest rows remains low (0.40-0.60), so the rule-walk fix is demonstrated within-family only.
- Round-2 verdict is VOID per the frozen table (known-answer pool defects); the Jaccard improvement is the pre-registered-fix comparison, not a passing calibration yet.
- STATUS 2026-08-21 — this entry describes rounds 1-2 only, and the loop has since run three further rounds without passing: round 3 FAILED on gate 4 alone (edge Jaccard 0.475 vs the 0.60 bar, 27 unaligned incidents, all B-side extras); round 4 was VOID on gate 7(c) known-answer by one coding (22/30 vs a re-derived bar of 23, plus 2 double-missed rows) with gate 4 recovered to 0.660 and U=0; round 5 was VOID on 7(c)'s absolute no-double-miss rule alone, despite the program's best margins on every other gate (Jaccard 0.866, kappa 0.756, netted label 0.872).
- Round 5 further argued, from the five-round record, that the calibration loop as frozen CANNOT TERMINATE — its terminal gate now measures gold-generation variance rather than annotator reliability, three consecutive rounds having failed on the gold pool rather than the annotator pair. Round 6 is frozen as the registered Option C path after a cross-lineage review impeached Erratum 6 and the CALIBRATED declaration reverted; its gate-(b) cross-lineage review returned FAIL with pre-spawn blockers, so round 6 is unlaunched as of 2026-08-21. No calibration round has passed. The 'measured' status therefore covers the rounds-1-to-2 rule-application contrast only, not a calibrated instrument.

**evidence**

- bench/reports/mh1-calibration-round1-2026-08-16.md
- bench/reports/mh1-calibration-round2-2026-08-16.md
- bench/reports/prereg-mh1-calibration-2026-08-16.md
- bench/reports/mh1-calibration-round3-2026-08-16.md
- bench/reports/mh1-calibration-round4-2026-08-16.md
- bench/reports/mh1-calibration-round5-2026-08-16.md
- bench/reports/mh1-round6-prep-2026-08-21.md
- bench/reports/sol-review-mh1-r6-2026-08-21.md

**recommendation eligible**

false

### Review breadth is assignable at the cheapest tier, but assignment is not dominance

- ID: assignable-breadth-cheap-tier
- Status: **measured**

**date**

2026-08-21

**claim**

In SEB-1, flag-only Sol-LOW shards each mandated to a host/isolation beat surfaced the ISO-1-class host-oracle-reachability BLOCKER in 3 of 3 reviewed packages — a defect that unassigned Sol-low, Sol-max, Terra-xhigh, Opus at every tier, and solo Sol-medium on all three packages missed, and that the Sol-xhigh reference arm caught on only one package of three. On the two shared runner/settings global rows the swarm scored 4/6 strict (5/6 generous) against 1/6 for Sol-xhigh and 0/6 for Sol-medium. The same rung nonetheless failed the registered stop rule on all three packages (strict recall 0.476/0.500/0.538 vs bars 0.71/0.64/0.62), and the solo medium reviewer caught defects falling between the swarm's beat boundaries, so the relationship is complementary rather than dominant.

**scope**

SEB-1 review-economics ladder; three pre-registered review packages (Q1-cascade, Q2-orderflip, SWJ-1) at worktree pin 0a4f6f0; confirmed-blocker keys of 21/14/13 rows derived from the SFJ-0 dispositions; GPT-5.6 via codex at low/medium/xhigh plus one batched Opus 5 verification pass per package.

**caveats**

- n=1 per package for every recall figure; the 3/3 on the ISO-1 class is a within-rung replication of the mechanism, not of the recall numbers.
- Beat boundaries were reviewer-determined (registered ambiguity A-1) and are the rung's largest variance source; a different beat partition moves the unique misses.
- Two of the four strict global credits are MIXED: the cheap shard named the deny-list gap while the expensive depth pass supplied the decisive payload. Q1 K-G2 is the one cleanly shard-originated global and is the credit the claim should lead with.
- SHAPE and LINEAGE are confounded: the shards were both given beat mandates AND drawn from a lineage independent of the authors of every target reviewed. SW-OPUS-1 (prereg-swopus1-2026-08-21-DRAFT.md) is the registered separation test; until it reports, this is not a lineage claim or a shape claim.
- Per-beat yield concentration (host/isolation and analyzer carried 10 of 11 unique wins) is one run on one target class and is NOT a basis for slimming the beat set. Standing practice runs the full shape and logs uniques_per_beat to bench/results/swarm_wild/ledger.tsv; re-evaluate only after 5+ diverse targets.
- Recall figures move materially across the borderline bracket; the strict/generous brackets and the extended-key re-derivation are in seb1-ladder-synthesis-2026-08-21-opus.md.

**evidence**

- bench/reports/seb1-ladder-synthesis-2026-08-21-opus.md
- bench/reports/seb1-rswarm-results-2026-08-21.md
- bench/reports/seb1-rswarm-grade-audit-2026-08-21-opus.md
- bench/reports/prereg-seb1-review-economics-2026-08-21-DRAFT.md

**recommendation eligible**

true

### Identical review verdicts coexist with a three-fold difference in defect detection

- ID: verdict-agreement-not-detection
- Status: **measured**

**date**

2026-08-21

**claim**

Solo Sol-medium reviews emitted the Sol-xhigh reference arm's exact (CORRECTNESS, DLH) verdict pair on all three SEB-1 packages — including Q1's asymmetric FAIL/PASS-WITH-CHANGES — and blocked dispatch on 3 of 3, while recalling only 0.214-0.571 of the same packages' confirmed blockers (strict coding). Both the verdict label and the binary operationally-blocked-dispatch metric were saturated at this rung and carried no discriminating information; everything separating the configurations lived in the finding-level tables. Routing review configurations on verdict labels is therefore blind to detection quality.

**scope**

SEB-1 R-med rung: three packages, one Sol-medium review each, graded against 21/14/13-row confirmed-blocker keys at pin 0a4f6f0.

**caveats**

- n=1 per package; discovery is stochastic per run, so a second Sol-medium pass would likely produce a different row set at a similar recall.
- The reference bars are themselves three single Sol-xhigh measurements.
- Verdict pairs are registered as descriptive and unscored (prereg B3); the scored agreement metric is operationally-blocked-dispatch, which was also 3/3.

**evidence**

- bench/reports/seb1-rmed-results-2026-08-21.md
- bench/reports/seb1-ladder-synthesis-2026-08-21-opus.md

**recommendation eligible**

true

### Answer reconstruction from a fixture is task-driven, not reviewer-tier-driven

- ID: reconstruction-is-fixture-driven
- Status: **replicated**

**date**

2026-08-21

**claim**

P-SEB1-5 predicted (conf 0.65) that no cheap review rung would reproduce the census-reconstruction class — solving a fixture to prove it leaks — on the rationale that the class had appeared only at Opus-max. It appeared at Sol-MEDIUM (independent census, 5/5 exact match against the hidden planted.json, asserted before the key was opened) and then again at Sol-LOW, where a flag-only shard named all five planted items by id and assembled the one-representative-per-type reconstruction hypothesis in its own memo with zero access to any answer file; the expensive verification layer only executed the cross-check the cheap shard had itself nominated. The class is a property of answer-scaffolded fixtures, not of reviewer deliberation depth.

**scope**

docs-omissions RASIC fixture at pin 0a4f6f0, reviewed inside the SEB-1 R-med and R-swarm rungs; two independent cheap configurations (GPT-5.6 codex at medium and at low effort).

**caveats**

- Two instances, one fixture — the generalization is to answer-scaffolded fixtures, not to fixtures at large.
- The Sol-low shard named the five items as leakage suspicions under a flag-only contract that forbade it from asserting a solved census; the Sol-medium reviewer asserted the reconstruction outright. The inference is the same; only the assertion differs.
- Key leakage was independently excluded: the answer key is absent from the pin, no shard event log references it, and the fixture-leakage shard never opened anything under answer/.

**evidence**

- bench/reports/seb1-rmed-results-2026-08-21.md
- bench/reports/seb1-rswarm-grade-audit-2026-08-21-opus.md
- bench/reports/seb1-ladder-synthesis-2026-08-21-opus.md
- bench/results/seb1_rswarm/swj1-b4-fixture-leakage.final.md

**recommendation eligible**

false

### The codex subscription meter charges a weighted token blend, not raw or uncached input

- ID: codex-meter-weighted-billing
- Status: **measured**

**date**

2026-08-21

**claim**

Reverse-engineered from 8,366 paired (token, meter) observations across 261 rollout files (2026-07-12 to 2026-08-21) and validated against the same night's whole-day meter bracket: the weekly meter charge is approximately uncached_input + 0.16x cached_input + 8.9x output — the API list-price ratio 1:0.1:8. Pure-uncached is refuted outright (predicts more spend than the meter recorded); pure-raw approximates well only above ~92% cache. Applied to SEB-1: the R-swarm codex side cost 5.2-7.5 points (not 4.3, not 23); the fully-measured xhigh reference arm cost ~21 points; the swarm's saving vs xhigh is 2.85x (clears the registered 2x resolution floor) while its saving vs solo medium is 1.28x (does not). Output/reasoning tokens are the expensive channel: the night's most output-dense review drew ~46% of its charge from 24K output tokens.

**scope**

ChatGPT Plus weekly bucket, GPT-5.6 family via the codex CLI on this host; fitted across sol low/medium/high/xhigh, luna, terra, codex-auto-review classes; the anchored variant reproduces all four registered working rates in sol-launch-notes-2026-08-21.md.

**caveats**

- Coefficients are fitted, not vendor-documented; each carries quantization error (meter reported as integer percent).
- --ephemeral runs write no rollout transcripts, so per-run meter brackets require flanking readings from other sessions or the UI.
- The 5-hour bucket has only n=48 observations from a single day; the fit is for the weekly bucket.

**evidence**

- bench/reports/codex-billing-rule-2026-08-21-opus.md
- bench/results/codex_meter/meter-step-segments-2026-08-21.tsv
- bench/reports/seb1-cost-comparison-2026-08-21-opus.md

**recommendation eligible**

true

### Swarm host/isolation breadth is shape, not lineage — but equivalence is unearned

- ID: swarm-premium-is-shape-not-lineage
- Status: **measured**

**date**

2026-08-22

**claim**

Holding the R-swarm beat-swarm shape fixed and swapping Sol-low shards for Opus shards (same lineage as every target under review, zero codex), Opus-with-beats recovered the host/isolation blocker class solo Opus missed at every measured tier: globals 5/6 strict vs Sol-swarm 4/6 and Sol-xhigh 1/6; P-SWO-1 GLOBALS-RECOVERED HIT (4/4). Strict recall 0.524/0.857/0.462 (pooled 0.604) vs R-swarm 0.476/0.500/0.538. This indicates the beat SHAPE, not reviewer lineage, produces the breadth premium. The equivalence claim is explicitly NOT made: P-SWO-2 returned PARTIAL (Q1 and SWJ-1 inside the +/-0.15 band, Q2 at 0.857 outside and above it), which the prereg registers as inconclusive on equivalence and which does NOT satisfy H-1's substitution rule; the arms are complementary, not ordered (SW-OPUS leads Q1/Q2, trails SWJ-1). Zero codex spent; no USD figure (Max-side telemetry, tokens+meter only).

**scope**

One structural mirror of an R-swarm rung: 3 SFJ-0 packages, 6 Opus shards + 1 Opus depth pass + 1 grader per experiment, frozen 48-row confirmed-blocker key at pin 0a4f6f0, n=1 per package. Grade audited (gate e, ADJUSTED).

**caveats**

- P-SWO-2 PARTIAL: equivalence to Sol shards is NOT established; Q2 over-performs out of band, which is formally what denies equivalence. Do not report as a substitution result.
- SHAPE reading is indicated, not established: the 8 P-SWO-3 rows were selected on the same measurement they were re-tested against (H-9), biasing toward SHAPE under a pure-noise null.
- Tier confound (H-1) RESOLVED 2026-08-22 by the SW-OPUS-LOW arm: the effort-matched mirror (Opus shards pinned low, verified) recalls 0.333/0.571/0.538 strict (22/48) against Sol-low's 0.476/0.500/0.538 (24/48) - one package each and a tie on the third, i.e. NO lineage advantage detected at matched effort, which attributes this arm's margin over R-swarm to EFFORT rather than lineage and lifts the tier confound. n=1, so that is a null, not an equivalence claim. H-9 is now the sole barrier to 'established'. See swopus-low-synthesis-2026-08-22-opus.md.
- H-11: the workspace preamble handed the host/isolation beat a hint the reference arm discovered on its own; 3 of 5 global credits reach their existence-proof limb through it. Graded on the clean deny-surface limb; H-11-conservative bracket makes P-SWO-1 NOT-ASSESSABLE, never FAIL.
- n=1 per package; strict recall protected, generous cross-rung only with the K-SWJ-9 correction (SWJ-1 generous 0.769->0.692) and the K-SWJ-11 one-coding-call sensitivity attached.
- Cost caveat NARROWED 2026-08-22: per-run Max-side token telemetry WAS recoverable from the subagent transcripts, so API list-price figures now exist (shard layer $44.11 for this arm vs Sol-low $8.06 and Opus-low $15.64; full pipeline $95.04). These are list prices for tokens consumed, not amounts billed - every run was Max-side and carried no per-run bill. What remains barred (convention #5) is comparing subscription METERS (Max no-bill vs codex points). See swopus-cost-comparison-2026-08-22-opus.md and swopus-low-synthesis-2026-08-22-opus.md section 5.
- Grader empty-file start is attested, not git-provable (whole result set in one post-grading commit).

**evidence**

- bench/reports/swopus1-synthesis-2026-08-22-opus.md
- bench/reports/swopus1-grade-audit-2026-08-22-opus.md
- bench/reports/prereg-swopus1-2026-08-21-DRAFT.md
- bench/results/swopus1/swopus_scores.tsv
- bench/results/swopus1/staging-verification.log
- bench/reports/swopus-low-synthesis-2026-08-22-opus.md
- bench/reports/swopus-cost-comparison-2026-08-22-opus.md

**price table id**

null

**recommendation eligible**

false

