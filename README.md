# MATACS AI Proposal Triage Design

**Candidate:** Muhammad Awais  
**Assessment Reference:** MATACS-TH-2026-02  
**Time Spent:** [Enter your actual time spent]

## Overview

This repository contains a design for an AI-assisted contractor proposal triage system. The design combines AI-based information extraction, deterministic evaluation rules, weighted scoring, human review, and audit logging.

## Deliverables

- [System Design and Written Answers](WRITEUP.md)
- [AI Extraction Prompt](PROMPTS.md)
- [Expected Proposal Ranking](ranking.json)
- [Process Flow Diagram](diagram/process-flow.png)

## Design Principles

- AI extracts information from contractor proposals.
- Deterministic rules handle mandatory checks and weighted scoring.
- Missing or conflicting information is flagged for review.
- Every score should be supported by evidence.
- A human reviewer makes the final award decision.
- Criteria changes are versioned for traceability.

## AI Tool Usage

[Describe your actual use of AI tools in 2–3 sentences. Include at least one example where you disagreed with or corrected an AI suggestion and explain why.]

## Limitations

The ranking scores are illustrative until the scoring formula is fully defined and applied consistently to all proposals. This repository contains a design, not a deployed application.
