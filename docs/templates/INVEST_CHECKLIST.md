# Infinite Ventures — INVEST Checklist

**Document version:** 1.0
**Methodology:** Spec-Driven Development
**Applies to:** All project specifications
**Approval authority:** Project Owner

---

# 1. Purpose

This checklist establishes the mandatory quality criteria for approving specifications in Infinite Ventures.

Every SPEC must be evaluated against the six INVEST principles before implementation.

The purpose is to ensure that specifications are sufficiently independent, understandable, valuable, estimable, small and testable.

A SPEC must not be approved solely because its requirements appear technically achievable.

---

# 2. Evaluation Rules

Each INVEST principle must receive one of three evaluations:

- **PASS:** The principle is adequately satisfied.
- **REVIEW:** Additional clarification or refinement is required.
- **FAIL:** The principle is not satisfied.

A SPEC can only be approved when all six principles receive PASS.

REVIEW and FAIL evaluations must be resolved before implementation.

The evaluator must provide a concrete justification for every result.

---

# 3. Independent

**Question:** Can this specification be implemented with minimal and explicitly controlled dependencies?

Checklist:

- [ ] The specification has a clearly defined boundary.
- [ ] Dependencies are explicitly identified.
- [ ] Each dependency is justified.
- [ ] The specification does not require unrelated functionality.
- [ ] Its implementation does not unnecessarily modify other systems.
- [ ] It can be implemented without waiting for unrelated work.

Evaluation:

- PASS: Dependencies are minimal, available or explicitly controlled.
- REVIEW: Dependencies need clarification.
- FAIL: The specification is unnecessarily coupled to unrelated work.

Important:

Independence does not prohibit legitimate technical dependencies.

For example, a business purchasing system may depend on an established game state and economy interface.

The objective is to minimize unnecessary coordination and coupling.

---

# 4. Negotiable

**Question:** Does the specification define the required outcome without unnecessarily restricting implementation decisions?

Checklist:

- [ ] Requirements describe expected behavior.
- [ ] The specification distinguishes requirements from implementation suggestions.
- [ ] Technical restrictions are justified.
- [ ] No unnecessary implementation details are imposed.
- [ ] Ambiguities and assumptions are explicitly documented.
- [ ] Product decisions are consistent with the official GDD.

Evaluation:

- PASS: Requirements are clear while allowing reasonable implementation decisions.
- REVIEW: Some requirements need clarification.
- FAIL: The specification imposes unjustified implementation restrictions or contains unresolved contradictions.

Important:

Approved architectural decisions and technical constraints are not negotiable within an individual implementation task unless explicitly revised.

---

# 5. Valuable

**Question:** Does this specification provide identifiable value to the project?

Checklist:

- [ ] The objective is explicit.
- [ ] The expected result is identifiable.
- [ ] The business or technical value is explained.
- [ ] The functionality supports the project vision or an approved technical objective.
- [ ] Deliverables are relevant to the current project phase.
- [ ] The result can be evaluated after implementation.

Evaluation:

- PASS: The specification provides identifiable and justified value.
- REVIEW: Its value needs further explanation.
- FAIL: The specification has no clear purpose or meaningful deliverable.

Important:

Technical foundations, refactoring and infrastructure improvements may provide value even when they do not directly introduce visible gameplay functionality.

---

# 6. Estimable

**Question:** Is the scope sufficiently understood to estimate implementation effort and identify risks?

Checklist:

- [ ] The objective is unambiguous.
- [ ] Included functionality is explicitly listed.
- [ ] Excluded functionality is explicitly listed.
- [ ] Requirements are sufficiently detailed.
- [ ] Dependencies are understood.
- [ ] Acceptance criteria are defined.
- [ ] Technical unknowns are identified.
- [ ] The implementation scope is sufficiently predictable.

Evaluation:

- PASS: The scope and implementation expectations are sufficiently understood.
- REVIEW: Important details or risks remain unclear.
- FAIL: The specification is too ambiguous or complex to estimate.

Important:

Estimable does not mean that implementation time must be predicted with perfect accuracy.

It means the work is sufficiently understood to make a reasonable assessment.

---

# 7. Small

**Question:** Is the specification sufficiently limited to be implemented and validated as one controlled unit of work?

Checklist:

- [ ] The specification has one primary objective.
- [ ] The included requirements are closely related.
- [ ] The number of affected systems is justified.
- [ ] The authorized file scope is limited.
- [ ] Validation can be completed within a controlled scope.
- [ ] The specification does not combine unrelated features.
- [ ] The implementation can be completed without broad architectural rewrites.

Evaluation:

- PASS: The specification has a focused and manageable scope.
- REVIEW: Its scope may need reduction.
- FAIL: The specification combines multiple independent objectives or requires excessive changes.

Important:

There is no universal maximum number of requirements or files.

Smallness is determined by complexity, cohesion, dependencies and validation effort, not merely by counting tasks.

If a SPEC contains multiple independently valuable deliverables, consider splitting it.

---

# 8. Testable

**Question:** Can the implementation be objectively verified against defined acceptance criteria?

Checklist:

- [ ] Every functional requirement has a verification method.
- [ ] Acceptance criteria are explicit.
- [ ] Expected results are observable.
- [ ] Validation methods are reproducible.
- [ ] Positive scenarios are considered.
- [ ] Relevant negative or boundary scenarios are considered.
- [ ] Expected results are not subjective.
- [ ] Validation does not depend on unavailable tools.
- [ ] Completion conditions are explicit.

Evaluation:

- PASS: All required behavior can be objectively verified.
- REVIEW: Some criteria or validation methods need clarification.
- FAIL: The specification cannot be reliably verified.

Important:

A requirement that cannot be tested must be rewritten, clarified or removed.

Examples of insufficient criteria:

- The interface should look good.
- The game should be fast.
- The economy should work correctly.

Examples of acceptable criteria:

- The displayed balance increases by the calculated production amount.
- A business cannot be purchased when the player has insufficient credits.
- Offline production never exceeds 12 hours of eligible accumulation.

---

# 9. Overall INVEST Evaluation

Use this table for every SPEC.

| Principle | Result | Justification |
|---|---|---|
| Independent | PASS / REVIEW / FAIL | [Explanation] |
| Negotiable | PASS / REVIEW / FAIL | [Explanation] |
| Valuable | PASS / REVIEW / FAIL | [Explanation] |
| Estimable | PASS / REVIEW / FAIL | [Explanation] |
| Small | PASS / REVIEW / FAIL | [Explanation] |
| Testable | PASS / REVIEW / FAIL | [Explanation] |

Overall result:

- APPROVED: All six principles are PASS.
- NEEDS REVISION: At least one principle is REVIEW.
- REJECTED: At least one principle is FAIL.

A revised specification must be evaluated again.

---

# 10. Approval Workflow

1. Draft the SPEC.
2. Review its objective and scope.
3. Evaluate all six INVEST principles.
4. Resolve REVIEW and FAIL results.
5. Repeat the evaluation when necessary.
6. Submit the specification for project owner approval.
7. Mark it APPROVED only after explicit authorization.
8. Deliver the approved specification to the implementation agent.

The implementation agent must never approve its own specification.

The project owner retains final approval authority.

---

# 11. Post-Implementation Review

INVEST evaluates specification quality before implementation.

After implementation, a separate review must evaluate:

- Compliance with the approved scope.
- Satisfaction of acceptance criteria.
- Validation evidence.
- Unauthorized modifications.
- Deviations from the specification.
- Remaining issues.

A specification that passed INVEST does not automatically mean its implementation is correct.

Implementation validation and final acceptance remain mandatory.

---

# 12. Guiding Principle

**No specification enters implementation without passing INVEST.**

Small, valuable and verifiable units of work are preferable to large specifications that combine unrelated objectives.

The quality of the specification determines the quality of the implementation process.

---

**End of INVEST Checklist.**