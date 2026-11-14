
# Infinite Ventures — Agent Directives

## 1. Project Authority

- Follow `docs/PROJECT_CONTEXT.md` as the authoritative source for project-wide technical constraints and development rules.
- The GitHub Wiki is the authoritative source for game design and functional requirements:
  https://github.com/marternium/infinite-venture/wiki
- Never invent, reinterpret, or independently change approved product decisions.

## 2. Documentation

- Read `docs/ARCHITECTURE.md` when architecture or module boundaries are relevant.
- Read `docs/ROADMAP.md` when phase planning or project progression is relevant.
- Use `docs/templates/SPEC_TEMPLATE.md` when preparing a SPEC.
- Use `docs/templates/INVEST_CHECKLIST.md` when evaluating a SPEC.
- Do not duplicate the full content of these documents in this file.

## 3. Spec-Driven Development

Follow this workflow:

1. Understand the project context.
2. Analyze the authorized GitHub Issue.
3. Draft the corresponding SPEC.
4. Evaluate all six INVEST principles.
5. Submit the SPEC for Project Owner review.
6. Wait for explicit approval.
7. Implement only the approved scope.
8. Validate against the acceptance criteria.
9. Report results and wait for Project Owner acceptance.

An approved SPEC does not authorize work outside its scope.

## 4. Scope and Authorization

- Never implement without an approved SPEC and explicit implementation authorization.
- Modify only files explicitly authorized by the current SPEC.
- Do not create, modify, delete, rename, or format unrelated files.
- Do not silently expand scope or proceed to another SPEC.
- Do not install dependencies, tools, or services without justification and authorization.
- Do not modify GitHub Issues, Projects, Milestones, or Wiki content unless explicitly authorized.

## 5. Specification Integrity

- Evaluate all six INVEST principles independently.
- Never approve your own SPEC.
- Report ambiguities, dependencies, risks, and blockers.
- Do not invent acceptance criteria or requirements.
- Preserve approved documentation and project decisions.

## 6. Game Design Research

- Consult the GitHub Wiki whenever a task depends on game design, gameplay, progression, economy, businesses, upgrades, or other functional requirements.
- Use the available web-fetching capability to consult the relevant Wiki pages.
- Base conclusions on the actual source content, not assumptions or previous summaries.
- If the Wiki cannot be accessed, report the blocker and do not invent missing requirements.
- Distinguish verified information from assumptions and unresolved questions.

## 7. Validation and Reporting

- Execute only the validation activities defined in the approved SPEC.
- Do not claim a check passed unless it was actually executed and its result observed.
- Stop when the approved validation conditions are satisfied.
- Report:
  - Files created or modified.
  - Commands and checks executed.
  - Acceptance criteria results.
  - Deviations, risks, and unresolved issues.
- Clearly distinguish PASS, FAIL, and UNVERIFIED.

## 8. Project Integrity

- Work only within the existing repository.
- Never create a duplicate project root.
- Preserve the existing provider and model configuration.
- Do not introduce unapproved frameworks, backend services, external APIs, or infrastructure.
- Prefer minimal, maintainable changes over unnecessary rewrites.

## 9. Project Owner Authority

The Project Owner is the only authority who can approve SPECs, authorize implementation, accept deliverables, or approve changes to project decisions.

When authorization is unclear, stop and ask.
