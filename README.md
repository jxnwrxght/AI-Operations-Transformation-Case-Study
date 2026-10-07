# Northstar Advisory — AI-Assisted Renewal Intake Pilot

> **Portfolio case study:** Northstar Advisory Group is a simulated company created to demonstrate AI operations, workflow design, and implementation thinking. The business context, stakeholders, and baseline figures in this repository are simulated for the case study.

## Overview

Northstar Advisory's renewal intake process relies heavily on manual document review. As renewal volume increases, Account Coordinators spend more time opening submissions, identifying document types, checking whether required documents are present, and following up on incomplete packages.

For this case study, I mapped the current workflow, identified the biggest sources of repetitive work, and designed a focused AI pilot to reduce manual intake effort without trying to automate the entire process at once.

## The Problem

I identified five main opportunities for improvement:

- Manual document intake
- Manual data extraction
- BrokerCore reconciliation
- Exception identification
- Administrative follow-up

Rather than trying to automate all five areas immediately, I selected **document classification and completeness detection** as Pilot 01.

The goal was to start with a contained use case where AI could handle repetitive first-pass work while keeping a human involved in validation.

## Current-State Workflow

The current-state map shows the existing renewal intake process, including manual handoffs, decision points, and the five main operational bottlenecks identified during the analysis.

![Northstar Advisory current-state renewal intake workflow](./assets/current-state-workflow.jpg)

## Pilot 01

When renewal documents arrive, the AI system:

**Classifies each document → checks classification confidence → compares the package against the required-document checklist → identifies whether the submission is complete or missing documents.**

Low-confidence classifications are sent to the Account Coordinator for review.

During the pilot, the Account Coordinator also validates every AI-generated intake result. Any incorrect classifications or completeness decisions are corrected and logged.

This allows the team to measure the system's accuracy before deciding whether high-confidence cases should eventually move forward without manual review.

## Future-State Workflow

The proposed future-state workflow introduces AI-assisted document classification and completeness detection while keeping the Account Coordinator in the loop for validation and exception handling during the pilot.

![Northstar Advisory future-state renewal intake workflow](./assets/future-state-workflow.jpg)

## Measuring Success

Before the pilot, baseline measurements would include:

- Coordinator handling time per renewal
- Human touches per renewal
- Incomplete submissions
- Total intake cycle time

Pilot performance would be measured using:

- Document classification accuracy
- Completeness-check accuracy
- Low-confidence / exception rate
- False positive / false negative rate
- Coordinator handling time vs. baseline

The goal is not simply to prove that AI can perform the task. It is to determine **where AI is reliable enough to reduce manual work and where human judgment should remain part of the process.**

## Next Steps

If Pilot 01 performs well, high-confidence routine submissions could gradually move toward straight-through processing while uncertain or unusual cases continue to receive human review.

Additional opportunities could then be evaluated, including automated data extraction, BrokerCore reconciliation, exception detection, and administrative follow-up.

## Project Artifacts

- [Business Brief](./01-business-brief.md)
- [Stakeholder Discovery](./02-stakeholder-discovery.md)
- [Current-State Workflow](./assets/current-state-workflow.jpg)
- [Future-State Workflow](./assets/future-state-workflow.jpg)
- n8n Prototype — coming next
- Loom Demo — coming next
