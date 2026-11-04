# Review guide: Regulated Gate Decision Support

Start with the [research account](research-summary.md), inspect a [canonical decision record](../examples/rgds-dec-0006-ai-assisted-conditional-go.json), then compare it with the [schema](../decision-log/decision-log.schema.json) and [semantic rules](../scripts/validate_decision_log.py). The implementation preserves decision context for review. Its institutional benefit remains a prospective research question. [Evaluation plan](../evaluation/evaluation-plan.md).

## Versions and publication

| Artifact | Recorded identity | Citation boundary |
| :--- | :--- | :--- |
| Current implementation | 2.0.1, September 9, 2026. [CFF](../CITATION.cff) | Cite the repository and exact commit used. |
| Historical implementation tag | `v.2.0.0`, with its original spelling. [Provenance](citation-provenance.md) | Preserve the existing tag. |
| Related independent study | v1.4, May 16, 2026, DOI 10.5281/zenodo.20242004. [Provenance](citation-provenance.md) | This DOI identifies the study archive. |

## The six illustrative records

These values describe the committed example files. They are authored cases. They provide no independent evidence of deployed review, approval or research authorship. [Project disclosure](ai-use-disclosure.md).

| Record | Outcome in the file | AI assistance declared |
| :--- | :--- | :--- |
| [0001](../examples/rgds-dec-0001.json) | `conditional_go` | Yes |
| [0002](../examples/rgds-dec-0002-no-go.json) | `no_go` | No |
| [0003](../examples/rgds-dec-0003-defer-required-evidence.json) | `defer_with_required_evidence` | No |
| [0004](../examples/rgds-dec-0004-regulatory-interaction.json) | `conditional_go` | No |
| [0005](../examples/rgds-dec-0005-ind-conditional-go-author-at-risk.json) | `conditional_go` | Yes |
| [0006](../examples/rgds-dec-0006-ai-assisted-conditional-go.json) | `conditional_go` | Yes |

Plain `go` and `defer` are contract values exercised by a derived regression test. They are absent from this six-record canonical set. [Schema](../decision-log/decision-log.schema.json), [regression test](../tests/test_validation.py).

## Known limits

### Current contract and older helpers

The starter template retains earlier fields, including `selected_option` and `risk`, while the current schema requires `risk_assessment` and other updated structures. Use a canonical example to inspect the current contract. A template migration remains separate work. [Template](../decision-log/decision-log.template.yaml), [schema](../decision-log/decision-log.schema.json).

The dashboard extract guides contain field mappings from earlier structures. Their examples require reconciliation before use with current records. The public files provide an illustrative reporting design. [Extract guide](../evaluation/decision-gate-extract.md), [Power BI sample](../evaluation/decision-gate-extract-powerbi-sample.md).

### Validation and human judgment

Validation covers required structure and specified relationships. It leaves substantive risk adequacy, identity and actual review unverified. Selected-option membership and the adequacy of residual-risk statements need separate review. [Requirements traceability matrix](../evaluation/requirements-traceability-matrix.md), [validator](../scripts/validate_decision_log.py).

The consistency-scan and dependency-summary files are illustrative review aids with unchecked items. Follow their actual files when inspecting these materials. [Consistency scan](ai-checks/ind-consistency-scan-0005.md), [dependency summary](ai-checks/ind-dependency-summary-0005.md).

### Evaluation status

The scorecard contains two populated example rows. Treat its times and ratings as illustrative inputs. The prospective plan reports no deployment study, measured time savings or regulatory benefit. [Scorecard](../evaluation/scorecard-template.csv), [evaluation plan](../evaluation/evaluation-plan.md).

Professional accounts informed the research question. A claim about RGDS's performance still needs a defined setting, independent review and observed workflow evidence. [Research origins and limits](research-summary.md).

## AI use and human verification

The AI-assistance policy specifies intended documentation and human responsibilities. The examples show how records could express those requirements. Neither supplies a complete retrospective account of the researcher's AI use or personal source checks. [Policy](ai-assistance-policy.md), [project disclosure](ai-use-disclosure.md).

## Next review decisions

Reviewers can assess record usefulness, contract gaps and the proposed evaluation separately. Any change to the schema, examples or research findings needs its own scoped revision. The [complete prior entry](../README-2026-11-03.md) and all underlying artifacts remain preserved.
