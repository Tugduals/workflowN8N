---
name: hostile-review
description: Performs an adversarial, exhaustive review of a project against its interview specification, fixes clear defects, reruns relevant checks, and saves a Markdown review report.
metadata:
  short-description: Exhaustive project review and fixes
---

# Hostile Review

Review the completed project as if you are actively trying to find how it could fail, violate its requirements, expose data, mislead users, or create unsafe outcomes. Be rigorous toward the work, never hostile toward the people who made it. Findings must be specific, evidence-based, and useful.

The intended project sequence is **interview → doubt-driver-dev → hostile-review**. When an `interview` specification and `doubt-driver-dev` handoff are available, treat them as the source of truth for intended behavior, acceptance criteria, boundaries, and test expectations. Never silently rewrite requirements to make the implementation appear correct.

## Review scope

Review the whole delivered project against the specification and acceptance criteria, including every project-owned file. Inventory the project first. Do not silently exclude files because they are hidden, generated, ignored by Git, vendored, or unfamiliar. Inspect source, tests, configuration, documentation, scripts, workflow exports, assets, and other files using a suitable method. For binary, very large, or otherwise unreadable files, use appropriate metadata or scanning tools where possible and record any inspection limit in the report.

Follow important data flows and dependencies across files. Check that the project is complete, that files agree with each other, and that the delivered result matches both explicit requirements and the intended user outcome. If no specification was supplied, establish the stated intent from the task and mark any scope uncertainty.

Prioritize:

1. Incorrect behavior, missing requirements, broken acceptance criteria, and contradictions.
2. Security, privacy, permissions, unsafe data handling, secrets, and consequential side effects.
3. Reliability, error paths, edge cases, retries, recoverability, and operational gaps.
4. Performance or usability defects that materially affect intended use.
5. Clarity and maintainability issues when they conceal or create substantive risks.

Do not pad the report with style preferences or speculative concerns without a plausible impact.

## Review and repair process

1. **Establish expected behavior.** Read the interview spec, development handoff, user request, and relevant project instructions. Resolve conflicts by reporting them; do not change the intended behavior without user direction.
2. **Inventory all files.** List the project's files and choose a suitable inspection method for each. Do not treat a passing build or a few changed files as proof of a complete review.
3. **Inspect and challenge.** Trace requirements through implementation, data flow, dependencies, tests, and operational documentation. Consider realistic malformed inputs, boundary conditions, partial failures, retries, concurrency, permissions, misuse, and misleading output.
4. **Verify important claims.** Reproduce defects and run appropriate tests, linters, security checks, builds, or document/workflow validation when available and relevant. Use current authoritative sources for claims that may have changed. Distinguish reproduced facts from reasoned risks and unverified assumptions.
5. **Fix clear defects.** Make focused fixes when intended behavior is unambiguous and the change is within the agreed scope. Preserve conventions and avoid broad rewrites. For ambiguous behavior or changes with material product, security, data, cost, or operational consequences, document the issue and ask for a decision. Continue with other independent findings.
6. **Recheck all changes.** Inspect the diff and rerun relevant checks after fixes. Do not weaken or remove tests merely to make them pass. State any check that could not run and what remains unverified. Never deploy, publish, send messages, run a live workflow, or mutate production as part of review unless explicitly authorized.
7. **Save the report.** Always create or update a Markdown report alongside the project. Follow the project's review/report convention; if none exists, use `reviews/hostile-review.md`. Include review scope, the complete file inventory or its saved location, unresolved findings, fixes made, checks and results, and inspection limitations. Do not overwrite unrelated reports.
8. **Summarize in chat.** Lead with unresolved findings, highest severity first. Link to the report and summarize the clearest fixes and verification results. If no defects were found, say what was checked and disclose any limits; never claim proof of perfection.

## Finding quality

Use consistent severity levels:

- **Critical:** imminent severe impact or broad compromise.
- **High:** major impact or likely exploitable failure.
- **Medium:** meaningful but limited impact.
- **Low:** minor impact.
- **Info:** useful observation without a demonstrated defect.

For each unresolved finding, identify the concrete condition, evidence, location, plausible impact, and practical remediation. Separate confirmed defects from risks dependent on assumptions. Group symptoms with a shared root cause. A concern is not a defect merely because evidence is missing; explain what evidence is absent and why it matters. Move fixed defects to the report's “Fixes made” section and include their verification status.
