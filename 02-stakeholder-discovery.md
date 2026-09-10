# Stakeholder Discovery

## Purpose

Before proposing an AI or automation solution, stakeholder discovery was conducted to understand the renewal document workflow from business, user, operational-risk, and technical perspectives.

Four simulated stakeholders were interviewed:

- Michael Chen — Chief Operating Officer
- Sarah — Account Coordinator
- David — Senior Account Manager
- Marcus Patel — IT Manager

The objective was to identify the underlying business problem, understand how the process operates today, document pain points and constraints, and establish requirements that should guide any future process redesign.

No AI solution was selected prior to completing discovery.

---

# 1. Chief Operating Officer

## Stakeholder
**Michael Chen — COO**

## Perspective
Business performance, operational scalability, staffing, capacity, cost, and continued company growth.

## Key Findings

Northstar's client base is growing, but the operational workload associated with servicing those clients is increasing alongside it.

The renewal process is a particular concern because significant employee time is spent processing incoming client documents before higher-value renewal work can begin.

Leadership is concerned that continued growth under the current operating model may require additional operations headcount simply to maintain existing service levels.

## Primary Needs

- Increase operational capacity
- Support client growth without proportional headcount growth
- Reduce repetitive administrative work
- Maintain service quality as volume increases
- Improve consistency and turnaround time
- Avoid introducing operational risk in pursuit of efficiency

## Business Requirement

Any redesigned process should create operational leverage:

**Client volume should be able to increase without requiring an equivalent increase in administrative workload.**

---

# 2. Account Coordinator

## Stakeholder
**Sarah — Account Coordinator**

## Perspective
Day-to-day user responsible for processing incoming renewal documents.

## Current Responsibilities

During renewal intake, the coordinator must:

1. Receive client emails and attachments
2. Determine which client and renewal the documents belong to
3. Open and identify submitted documents
4. Determine whether required documents are missing
5. Extract relevant information
6. Compare new information against existing client records
7. Identify discrepancies or unusual information
8. Update internal systems
9. Escalate cases requiring additional judgment
10. Prepare or support client follow-up communication

## Key Pain Points

The workflow contains substantial repetitive manual work.

Document names and formats are not always consistent, requiring employees to inspect documents individually.

Information must frequently be transferred manually between documents and internal systems.

Employees must also determine whether information is missing, inconsistent, or significant enough to require escalation.

This creates opportunities for:

- Slow processing
- Manual data-entry errors
- Missed information
- Rework
- Inconsistent turnaround
- Employee time being consumed by repetitive administrative tasks

## User Requirement

Any redesigned process should reduce repetitive work without making the coordinator responsible for blindly trusting automated outputs.

The coordinator should be able to understand what the system found, identify where information came from, and review uncertain or higher-risk cases.

---

# 3. Senior Account Manager

## Stakeholder
**David — Senior Account Manager**

## Perspective
Insurance expertise, exception handling, client risk, and decisions requiring professional judgment.

## Key Findings

Not every part of renewal processing is purely administrative.

Certain discrepancies, changes, or unusual circumstances require contextual judgment from experienced account staff.

Examples may include:

- Significant changes in client information
- Material claims activity
- Conflicting information
- Missing documentation
- Unusual coverage-related circumstances
- Situations where available information is insufficient to make a reliable determination

Automating administrative work may be valuable, but automation should not be treated as a substitute for professional judgment.

## Primary Needs

- Preserve human review for consequential decisions
- Clearly distinguish routine cases from exceptions
- Surface relevant discrepancies rather than hide them
- Avoid confident automated decisions when information is incomplete
- Make escalations easier for account managers to review

## Operational Requirement

A redesigned workflow should distinguish between:

**Routine processing that can potentially be automated**

and

**Judgment-intensive decisions that should remain human-controlled.**

---

# 4. IT Manager

## Stakeholder
**Marcus Patel — IT Manager**

## Perspective
Systems, integrations, data security, permissions, reliability, technical feasibility, and auditability.

## Existing Systems

### Microsoft 365
Client renewal documents generally enter the organization through email.

### SharePoint
Client documents are stored within controlled client folders.

### BrokerCore
Northstar's brokerage management platform and primary system of record for client and policy information.

BrokerCore provides limited API access. Some information can be programmatically retrieved or updated, while other parts of the renewal workflow still require direct human interaction with the platform.

---

## Technical Findings

Microsoft 365 and SharePoint provide relatively strong integration opportunities through existing APIs.

BrokerCore presents more limitations because API access does not expose every function required by the renewal workflow.

Reliable client identification is also a challenge.

Incoming documents may:

- Use inconsistent filenames
- Reference clients differently from internal records
- Be forwarded by other individuals
- Contain information relating to multiple policies
- Be incomplete or difficult to read

The system therefore cannot assume that every incoming document can be reliably matched and processed automatically.

---

## Security Requirements

Client documents may contain sensitive business and employee information, including:

- Payroll information
- Employee information
- Claims history
- Property information
- Insurance and policy information

Before approving an external AI provider, IT would need visibility into the complete data path.

This includes understanding:

- What information leaves Northstar's environment
- Which provider receives the information
- Whether information is retained
- How long it is retained
- Whether information is used for model training
- How information is encrypted
- How applications authenticate
- What permissions automated systems receive
- What activity is logged

Automated systems should follow least-privilege principles and receive only the access required to perform their intended function.

---

## Auditability Requirement

Actions performed or recommended by an automated system should be traceable.

For relevant outputs, Northstar should be able to determine:

- Which source document produced the information
- What information the AI extracted or generated
- What recommendation was made
- What subsequent action occurred
- Whether a human reviewed the output
- Who approved consequential actions

---

## Failure-Handling Requirement

The system should fail safely rather than make unsupported assumptions.

Potential failure conditions include:

- Low-confidence outputs
- Unreadable documents
- Client-matching uncertainty
- Conflicting information
- Missing information
- API failures
- Unexpected document formats

When these situations occur, the workflow should stop or route the case for human review rather than continue autonomously.

---

# Cross-Stakeholder Synthesis

Stakeholder discovery revealed that the renewal workflow is not simply a document-processing problem.

It is a scalability problem involving competing requirements across efficiency, user experience, professional judgment, security, and operational risk.

## Areas of Alignment

All stakeholders would benefit from reducing repetitive administrative work.

However, the interviews also established that increased automation cannot come at the expense of:

- Accuracy
- Human judgment
- Data security
- Traceability
- Client service
- Safe exception handling

---

# Initial Requirements

Based on stakeholder discovery, any proposed future-state workflow should:

1. Reduce repetitive document-processing work
2. Improve processing speed and operational capacity
3. Maintain or improve accuracy
4. Preserve human oversight for consequential decisions
5. Detect and escalate uncertain or exceptional cases
6. Avoid unsupported assumptions when information is incomplete
7. Protect confidential client information
8. Restrict system access using appropriate permissions
9. Maintain an audit trail of system activity and human approvals
10. Integrate with existing systems where technically feasible
11. Allow employees to understand and verify automated outputs
12. Demonstrate measurable improvement before receiving greater autonomy

---

# Pilot Constraints

The initial pilot should be deliberately limited.

A potential pilot would:

- Use approximately 50–100 controlled renewal cases
- Begin with a limited account team or workflow
- Maintain the existing process as the official process during testing
- Operate primarily in read-and-recommend mode
- Require human review before consequential actions
- Prevent autonomous client communication
- Prevent autonomous updates to the primary system of record during initial testing
- Log system outputs, exceptions, and human approvals
- Define success metrics before testing begins

Greater autonomy should only be considered after the system demonstrates sufficient reliability and business value.

---

# Success Criteria

The future solution should ultimately be evaluated against the original business problem.

Key measures should include:

- Processing time per renewal package
- Overall processing capacity
- Extraction/classification accuracy
- Error and rework rate
- Human intervention rate
- Initial turnaround time
- Cost per processed package
- Frequency and quality of escalations

The objective is not maximum automation.

The objective is to determine the appropriate combination of **human judgment, deterministic automation, and AI** that allows Northstar to process greater renewal volume safely and efficiently.

---

# Next Step

With stakeholder discovery complete, the next phase is to document the current-state renewal workflow in detail.

The current-state process map will identify:

- Process steps
- Systems involved
- Human handoffs
- Decision points
- Bottlenecks
- Repetitive work
- Sources of delay
- Sources of error and rework

AI opportunities will be evaluated only after the existing workflow has been mapped and understood.
