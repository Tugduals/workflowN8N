# Project Specification — [Project name]

- **Status:** Draft / Needs user review / Approved for implementation
- **Version:** [date or number]
- **Business owner:** [name or role, if known]
- **Last updated:** [date]
- **Specification language:** [language]

## 1. Project summary

[Problem, intended solution, and expected outcome in a few sentences.]

## 2. Context, goals, and boundaries

- **Current process:**
- **Problem or opportunity:**
- **Measurable goals:**
- **In scope:**
- **Out of scope:**
- **Users and stakeholders:**

## 3. Functional requirements

| ID | Requirement | Priority | Source / status |
|---|---|---|---|
| FR-01 | | Must / Should / Could | Confirmed / assumption / proposal |

## 4. User and system flows

### Trigger and inputs
[What starts the process, required input, source, frequency, and conditions.]

### Main path
1. [Step]
2. [Step]
3. [Expected outcome]

### Business rules and branches
| ID | Condition | Expected behavior | Source / status |
|---|---|---|---|
| BR-01 | | | Confirmed / assumption / to confirm |

### Exceptions and human actions
| Scenario | Required behavior | Owner / notification |
|---|---|---|
| | | |

## 5. Systems and data

| System | Purpose | Data read / written | Known interface | Environment / access constraints |
|---|---|---|---|---|
| | | | | |

- **Personal or sensitive data:** categories, purpose, minimization, and known retention.
- **Data that must not be collected, transmitted, or stored:**
- **Credentials required:** names/types only; configure securely in n8n, never include secret values.
- **Integration capabilities not yet verified:**

## 6. Non-functional requirements and constraints

- **Volume / frequency:**
- **Latency / availability:**
- **Timezone / execution windows:**
- **Duplicate handling / idempotency:**
- **Retry and recovery behavior:**
- **Logging, monitoring, and alerts:**
- **Permissions / security:**
- **Retention / deletion:**
- **Rate, payload, cost, or hosting constraints:**
- **n8n version / hosting mode, if known:**

## 7. Proposed implementation direction

> Treat this section as a proposal. `doubt-driver-dev` should verify technical feasibility before implementation.

- **Candidate workflow boundaries:**
- **Trigger and major steps:**
- **Branches / sub-workflows / human approvals:**
- **External services or dependencies:**
- **Technical assumptions to investigate:**

## 8. Acceptance criteria and test expectations

| ID | Given… | When… | Then… | Priority |
|---|---|---|---|---|
| AC-01 | | | | Must |
| AC-02 | | | | Must |
| AC-03 | An important failure occurs | | The agreed error behavior is observable | Must |

- **Normal-path examples:**
- **Edge cases to cover:**
- **Failure cases to cover:**
- **Test data/environment constraints:**

## 9. Implementation boundaries

- **Must preserve:** [existing behavior, interfaces, data, or design constraints]
- **Must not change:**
- **Dependencies / prerequisites:**
- **Definition of done:**

## 10. Decisions, assumptions, and open questions

| Item | Detail | Status | Owner / next action |
|---|---|---|---|
| | | Confirmed / assumption / open | |

## 11. Risks

| Risk | Likelihood / impact | Mitigation or investigation |
|---|---|---|
| | | |

## 12. Handoff to doubt-driver-dev

**Build:** [concise implementation objective]

**Source of truth:** This approved specification and any linked project requirements.

**First steps:** Inspect the relevant project and verify the listed technical assumptions before choosing an implementation.

**Required checks:** Implement and run the tests needed to demonstrate the acceptance criteria; report anything that could not be verified.

**Do not:** Change out-of-scope behavior, invent unresolved business rules, expose credentials, or deploy/run against production without explicit authorization.

**Open decisions that block implementation:** [list, or “None known”]

## 13. User validation

- **Reviewer:**
- **Decision:** Pending / Approved for implementation / Changes requested
- **Date and comments:**
