# Agent cost benchmark findings

A curated static snapshot of an independent benchmark of AI coding agents on platform-engineering tasks.
The source run ledger contains **1,423 completed runs** at export time, 16 September 2026.
This repository publishes selected findings and methods, not the runnable benchmark.

## What the benchmark studies

The benchmark compares model tiers, reasoning effort, prompts, feedback, review arrangements, and agent harnesses on synthetic infrastructure and documentation work. Tasks include repository-wide edits, incident diagnosis, and decisions about decommissioning resources. It studies both the cost of producing a correct result and the reliability of the checks used to decide whether that result is correct.

The work includes offline tasks and historical runs with live cloud interactions. “1,423 completed runs” is an inventory count from the source ledger, **not** a claim that every run is valid, independent, controlled, or part of a single comparable experiment. Pilots, corrections, contaminated or invalidated conditions, and different accounting regimes require their own treatment. No aggregate leaderboard is implied.

## Start here

| Document | Purpose |
| --- | --- |
| [Findings register](bench/reports/findings.generated.md) | Readable claims, status labels, scope, caveats, and corrections |
| [Structured findings](bench/reports/findings.json) | The same register as JSON data |
| [Doctrine](bench/reports/doctrine.md) | Practical rules and their amendments; interpretation rather than a new experiment |
| [Consolidated assessment, August 1](bench/reports/consolidated-assessment-2026-08-01.md) | Historical synthesis and research-direction assessment |
| [2×2 design, July 31](bench/reports/design-17g-2x2-2026-07-31.md) | Separating hazard detection from caution about destructive actions |
| [2×2 results, August 1](bench/reports/batch-17g-2x2-2026-08-01.md) | Aggregate outcomes, scoring-policy revision, and unresolved record-level scoring |
| [ISO-1 rundown, August 22](bench/reports/iso1-rundown-for-evan-2026-08-22.md) | How answer-key isolation failed and why repairs required independent checks |
| [ISO-1 architecture note, August 22](bench/reports/iso1-architecture-note-2026-08-22.md) | Historical reasoning about tool-level restrictions, OS enforcement, and deny-by-default isolation |

## How to read the evidence

The register retains **39 entries**: 28 measured, 5 directional, 2 replicated, 1 derived, and 3 retracted. The 36 non-retracted entries are not 36 independently validated discoveries. Read each entry's caveats and correction fields; a status label is not an assurance that every sentence remains current.

- **Measured:** observed in the stated experiment; not automatically replicated elsewhere.
- **Replicated:** the source records repetition on an independent gated instance or a decontaminated replication; scope still matters.
- **Directional:** limited sample size or other uncertainty prevents strong magnitude claims.
- **Derived:** arithmetic from measured inputs rather than a randomized treatment.
- **Retracted:** retained visibly so invalidated claims do not disappear from the record.

Many cells have small samples or share a fixture. Model version, harness configuration, task wording, effort, date, and evaluator behavior can confound comparisons. Historical prices and reported usage are not current pricing advice. Subscription usage, token-based list-price estimates, and billed costs must not be pooled as if they were the same measure.

### Corrections worth reading before quoting a result

- **Judgment tasks:** the register reports Haiku 1/19 versus Sonnet and Opus 5 at 18/18 on three task mechanisms. The strong tiers were at ceiling; this does not rank them against each other or establish a universal rule about model families.
- **2×2 scoring:** the revised 6/6 strong-tier results concern the end-state dimension. The accompanying decision-record dimension was explicitly unscored in the amended record. The historical report's broad wording and denominators should not be treated as a clean, final all-dimensions score.
- **XL economics:** the Opus-versus-Sonnet-versus-pipeline cost ordering was retracted. Surviving pass counts do not restore the ordering. Some older cross-references still describe it favorably; the retraction and later doctrine errata take precedence.
- **ISO-1 chronology:** the August 22 notes describe an unresolved freeze at that date. Doctrine section 7 records closure on August 29. Closure of the isolation work does not establish that every earlier run was uncontaminated; no completed retrospective clearance of all pre-freeze results is supplied here.
- **Isolation language:** historical claims that an OS restriction cannot be bypassed describe the mechanism and probes tested then, not a proof of security against every possible attack or configuration. Later architecture entries revise earlier descriptions; read the chronology in order.
- **Interpretation versus measurement:** practical doctrine sometimes states a stronger operating rule than a small experiment alone would establish. Its amendments and limitations are part of the publication, not optional footnotes.

## What is withheld, and why

Only the eight selected report files and this README are included. There are **no transcripts, task fixtures, answer-key files, or executable source files**, and no source-repository Git history.

Exact scoring implementations, fixture-specific solution sections, resource literals, code/configuration snippets, and historical answer-key retrieval instructions have been omitted or replaced with visible markers. The design and result summaries retain the conceptual comparisons needed to interpret the reported outcomes; they do not provide a marking scheme for solving the withheld tasks.

Identifiers, credentials, service URLs, hostnames, local home-directory paths, email addresses, and employer names have been scrubbed. Some anonymous historical workplace aggregates remain in the register, with their original provenance limitations. No underlying workplace records are supplied.

Withholding the fixtures and keys limits contamination of future evaluations. Withholding transcripts, deployment details, and history limits disclosure of private information. It also means this repository alone is **not sufficient to reproduce or independently audit the reported experiments**.

Evidence filenames that do not appear in the table above identify withheld records. They are provenance labels, not promises of available downloads. Issue numbers and short revision labels likewise refer to the private research history, not issues or commits in this repository.

## Export provenance

- Snapshot prepared: 16 September 2026.
- Findings source last-updated field: 30 August 2026; document amendments carry their own dates.
- Static, curated export; no automatic synchronization with the private research repository.
- JSON status labels, numerical results, caveats, corrections, and retraction records retained; identifying strings and implementation details scrubbed.
- Readable findings regenerated from the scrubbed JSON so every exported field is visible, including corrections and recommendation eligibility.
- ISO-1's duplicated internal handoff appendix omitted; exact answer-key and fixture-specific implementation sections omitted from the design and rundown.
- Historical reports preserved as dated records rather than silently rewritten into present-day claims.
- Research reports developed with AI assistance; this export includes AI-assisted curation and a generated readable register.

Contact: [Evan DeLord](https://delord.dev).
