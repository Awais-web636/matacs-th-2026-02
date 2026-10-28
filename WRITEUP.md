# AI Proposal Triage Design

## 1. AI vs. Rules

I would use AI to extract information from uploaded proposals because PDF documents may have different layouts and wording. The AI would extract fields such as price, relevant experience, completion timeline, warranties, licences, insurance, and team details into a structured JSON format. It would also provide evidence from the proposal for each extracted field.

I would use normal code for data validation, mandatory pass/fail checks, weighted score calculation, ranking, and audit logging. These operations require consistent and predictable results. AI would not decide the final winner or invent missing information.

## 2. Consistency and Explainability

I would define a fixed scoring formula for every weighted criterion. The administrator would configure the criteria and weights, and the system would validate that the weights total 100%.

For each proposal, the system would store the extracted values, supporting evidence, criterion-level scores, and final score. Identical inputs evaluated under the same criteria version and scoring rules would produce the same ranking.

The reviewer would see the total score, individual criterion scores, extracted evidence, missing information, and a short explanation of the proposal's position. AI-generated explanations would be based on verified extracted data rather than unsupported claims.

## 3. Human in the Loop

A reviewer would confirm the selected category and inspect the extracted information. Proposals with missing, conflicting, or uncertain mandatory information would be flagged for review.

The reviewer could request clarification, correct extraction errors, or override the proposed ranking with a recorded reason. The final award decision would always remain with the human reviewer.

The audit log would record the proposal identifier, original document reference, extracted data, evidence, criteria version, scoring formula version, individual scores, total score, flags, reviewer actions, overrides, timestamps, and final decision.

## 4. Changing Criteria

Every criteria configuration would have a version number. When an administrator changes a criterion or weight, the system would create a new version rather than overwrite the previous configuration.

Previously scored proposals would retain their original scores and criteria version for audit purposes. If the administrator wants to evaluate existing proposals under the updated criteria, the system would recalculate their scores using the new version and clearly label the updated results.

The system would validate mandatory fields, weight totals, and scoring rules before activating a new criteria version.

## 5. Risks and Safeguards

**Incorrect extraction:** The AI may extract an incorrect price, warranty, or licence number. I would validate data types and ranges, retain source evidence, and require human verification for uncertain or important fields.

**Hallucination:** The AI may invent information that is not present in a proposal. Missing information would be recorded as unknown, not assumed. Scores would not be awarded for unsupported claims.

**Prompt injection:** A proposal may contain instructions telling an AI system to change its ranking. I would treat uploaded documents as untrusted data, ignore instructions contained within them, and use a fixed extraction prompt. Scoring would be performed separately by deterministic code.

**Bias and inconsistent scoring:** I would use the same criteria and scoring rules for every proposal. Criterion-level scores and evidence would be available for review.

**Cost and performance:** I would process proposals in controlled batches, limit unnecessary AI calls, validate structured outputs, and retry only recoverable failures.

**Missing or conflicting information:** The system would flag affected proposals instead of silently making assumptions. A human reviewer would resolve the issue before a final decision.

Overall, the tool would support procurement decisions through consistent scoring, transparent evidence, human oversight, and an auditable process.
