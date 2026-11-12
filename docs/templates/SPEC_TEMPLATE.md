# Infinite Ventures — SPEC Template

**Specification ID:** SPEC-XX
**Title:** [Specification title]
**Project Phase:** [Phase number and name]
**Status:** Draft / In Review / Approved / In Progress / Validated / Accepted / Rejected
**Version:** 1.0

---

# 1. Objective

Describe precisely what this specification intends to implement.

The objective must be clear, limited and independently understandable.

# 2. Business and Technical Value

Explain the value delivered by this specification.

Identify the functionality, technical capability or quality improvement it provides.

# 3. Context and References

Describe the minimum context necessary to understand the requested work.

References may include:

- Official Game Design Document (GDD).
- Project Context.
- Architecture document.
- Approved Architecture Decision Records (ADR).
- Previous accepted specifications.

Include specific document sections when relevant.

A specification must contain sufficient context to be implemented without requiring the agent to independently reconstruct the entire project design.

# 4. Dependencies

List all dependencies required before implementation.

For each dependency, identify:

- Dependency ID.
- Description.
- Current status.
- Why it is required.

If there are no dependencies, explicitly state:

**Dependencies: None.**

Dependencies must be justified. Avoid unnecessary coupling between specifications.

# 5. Scope

## 5.1. Included

List exactly what this specification must deliver.

Each item must describe an identifiable result.

## 5.2. Excluded

List functionality, improvements or architectural changes explicitly outside this specification.

The agent must not implement excluded functionality even if it identifies opportunities to do so.

# 6. Requirements

## 6.1. Functional Requirements

Use unique identifiers:

- FR-01
- FR-02
- FR-03

Each requirement must describe an observable system behavior.

## 6.2. Technical Requirements

Use unique identifiers:

- TR-01
- TR-02
- TR-03

Describe technical constraints, integration requirements and architectural expectations.

Do not prescribe implementation details unless they are necessary to preserve an approved architectural decision.

# 7. Acceptance Criteria

Define objective conditions that must be satisfied before the specification can be accepted.

Use unique identifiers:

- AC-01
- AC-02
- AC-03

Acceptance criteria must be:

- Specific.
- Observable.
- Unambiguous.
- Reproducible.
- Verifiable.

Where appropriate, use Given / When / Then.

Do not use vague statements such as:

- Works correctly.
- Looks good.
- Is optimized.
- Has no problems.

Replace them with measurable or observable conditions.

# 8. Authorized Files

Explicitly identify the files that may be created, modified or deleted.

| File | Operation | Reason |
|---|---|---|
| [path] | Create / Modify / Delete | [Justification] |

Rules:

- No modifications outside the authorized list.
- New files must be explicitly authorized or covered by an authorized directory allowance.
- Do not delete existing files without explicit authorization.
- Report any necessary additional file changes before performing them.

# 9. Implementation Constraints

List restrictions relevant to this specification.

Examples:

- Preserve existing public interfaces.
- Maintain compatibility with the approved architecture.
- Avoid unnecessary dependencies.
- Do not duplicate existing functionality.
- Do not introduce unrelated refactoring.
- Do not use inline styles.
- Keep gameplay logic separate from UI rendering.

Only include constraints relevant to the current scope.

# 10. Validation Strategy

Define exactly how each acceptance criterion will be verified.

| Validation ID | Acceptance Criteria | Method | Expected Result |
|---|---|---|---|
| VAL-01 | AC-01 | [Test or inspection] | [Expected result] |
| VAL-02 | AC-02 | [Test or inspection] | [Expected result] |

## 10.1. Validation Scope

Specify the exact files, modules, behaviors or scenarios to validate.

## 10.2. Validation Tools

Identify the available tools required for validation.

Do not install additional tools unless explicitly authorized.

## 10.3. Stopping Conditions

Validation must stop when:

- All required acceptance criteria have passed.
- All authorized validation methods have been executed.
- No unresolved blocking defect remains within the specification scope.

If a required validation method cannot be executed, report it as unverified.

Do not replace unavailable validation with repeated attempts using unrelated tools.

# 11. Definition of Done

This specification is considered complete only when:

- All included requirements are implemented.
- All acceptance criteria are verified.
- The authorized file scope has been respected.
- No unrelated modifications have been introduced.
- Relevant technical documentation has been updated when required.
- Validation results have been reported.
- Remaining limitations or known issues have been documented.

Completion of implementation alone does not mean acceptance.

# 12. Expected Deliverables

List the concrete outputs expected from this specification.

Examples:

- New functionality.
- Modified modules.
- Configuration definitions.
- Tests.
- Technical documentation.

# 13. Risks and Open Questions

Identify known risks, unresolved questions and assumptions.

Each open question must have an owner or require explicit resolution before implementation.

Do not silently turn assumptions into product requirements.

# 14. INVEST Evaluation

Evaluate all six INVEST principles before approval.

| Principle | Evaluation | Justification |
|---|---|---|
| Independent | Pass / Review / Fail | [Explanation] |
| Negotiable | Pass / Review / Fail | [Explanation] |
| Valuable | Pass / Review / Fail | [Explanation] |
| Estimable | Pass / Review / Fail | [Explanation] |
| Small | Pass / Review / Fail | [Explanation] |
| Testable | Pass / Review / Fail | [Explanation] |

## INVEST Approval Rules

- **Pass:** The principle is adequately satisfied.
- **Review:** More clarification is needed.
- **Fail:** The specification does not satisfy the principle.

A specification cannot be approved while any principle remains in Review or Fail.

If the specification is too large, divide it into smaller specifications.

If dependencies are excessive, reconsider its boundaries.

If acceptance criteria cannot be objectively verified, rewrite them before approval.

# 15. Execution Report

This section must be completed by the implementation agent after execution.

## 15.1. Implementation Summary

Describe the changes performed.

## 15.2. Files Changed

List every created, modified or deleted file.

## 15.3. Validation Results

| Validation ID | Result | Evidence |
|---|---|---|
| VAL-01 | Pass / Fail / Unverified | [Evidence] |

## 15.4. Deviations

Report any deviation from the approved specification.

If none occurred, state:

**No deviations.**

## 15.5. Remaining Issues

List unresolved issues or limitations.

If none remain, state:

**No known outstanding issues within this specification scope.**

## 15.6. Final Status

Implementation agent recommendation:

- Ready for review.
- Blocked.
- Incomplete.

Final acceptance must be granted by the project owner.

---

**End of specification template.**