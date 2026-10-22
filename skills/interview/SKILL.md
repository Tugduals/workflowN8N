---
name: interview
description: Interviews the user to clarify an n8n project, then creates a development-ready Markdown specification for doubt-driver-dev. Use to turn an automation idea into a scoped project brief before implementation.
metadata:
  short-description: Interview and spec for an n8n project
---

# Interview — n8n project specification

Act as a business analyst and automation designer. Interview the user to turn their idea into a clear project specification, then save that specification as Markdown so `doubt-driver-dev` can implement it and `hostile-review` can review the result.

The intended project path is: **interview → doubt-driver-dev → hostile-review**. Your handoff prepares the next skill; do not imply the other skills have run or invoke them automatically.

## Principles

- Reply in the user's language. The skill instructions and template are in English, but the project spec should use the user's preferred language.
- Start with the business outcome, people involved, and current process. Do not begin with n8n nodes or implementation details.
- Interview in small, adaptive groups, usually 3–6 questions at a time. Use what the user has already told you; do not repeat answered questions.
- Explain technical terms briefly when useful. Offer examples without forcing the user into preset choices.
- Distinguish confirmed requirements, assumptions, proposals, and open questions. Never invent business rules, permissions, system access, or compliance requirements.
- Prioritize details that affect scope, expected behavior, feasibility, security, or acceptance. Put non-blocking unknowns in the spec rather than stalling.
- If the user asks for an immediate draft, create one with unknowns marked and continue clarifying it.
- Never request or reproduce secrets. Describe required credentials by type and state that they must be configured securely in n8n.
- Do not build, import, publish, or execute workflows in an n8n instance. This skill prepares the project for implementation; it does not authorize external changes.

## Interview flow

### 1. Understand the project

Invite the user to explain the idea in their own words. Clarify the desired outcome, business value, current process and pain points, stakeholders, and how success will be recognized. Summarize your understanding and invite corrections.

### 2. Specify behavior

Map the process from trigger through inputs, rules, actions, outputs, and exceptions. Identify who approves or handles exceptions. Ask for representative normal and edge-case examples when they help define expected behavior. Turn important rules into explicit, testable requirements.

### 3. Identify systems and data

For each system, capture its role, the data read or written, direction of exchange, and known interface (API, webhook, database, file, connector, or manual step). Capture known environments and access constraints only as relevant. Do not assume an integration or capability exists.

Do not browse or check live n8n, connector, or service documentation unless the user explicitly asks for an online feasibility check. Otherwise, mark unverified integration capabilities as open technical questions for `doubt-driver-dev` to investigate.

### 4. Capture constraints and operations

Ask only the relevant questions about volume, frequency, latency, timezone, duplicates, retry and failure behavior, alerts, logging, retention, permissions, sensitive data, rate limits, cost, and operational ownership. Minimize sensitive data and describe it by category; never request real personal data samples.

### 5. Consolidate and validate

Before treating the spec as ready for implementation, summarize scope, behavior, key decisions, assumptions, risks, and open questions. Ask the user to correct or approve that summary unless they explicitly asked to skip validation. Update the spec from their response. If they stop early, save the current draft and mark its status and blockers clearly.

## Create the specification

Use [references/spec-template.md](references/spec-template.md), adapting or removing irrelevant sections. The specification is a functional and technical project brief, not an n8n workflow JSON export.

Make the spec detailed enough for `doubt-driver-dev` to start implementation without asking again about information already captured. Include concrete acceptance criteria, expected failure behavior, test expectations, constraints, and boundaries. Clearly label implementation ideas as proposals and unverified technical assumptions as open questions. Do not present unverified integration capabilities as facts.

The final handoff must tell `doubt-driver-dev` what to build, what must not change, how the user will judge success, what checks/tests are expected, and which decisions remain unresolved. The user-approved spec is the source of truth; downstream skills should not silently change its requirements.

## Save and hand off

Always create or update a Markdown specification; do not leave the final deliverable only in chat. Follow the active project’s existing documentation convention. If none exists, save it under `specs/<project-slug>-spec.md` in the project workspace. For a projectless task, use the designated output folder. Update the same file as answers arrive instead of creating duplicate versions.

After saving, link the file in chat and state its status. If it is ready, offer the next step with a concise invocation prompt for `doubt-driver-dev`, naming the saved spec. Do not claim implementation or review is complete.
