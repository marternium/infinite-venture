# SPEC-002 — OpenCode Configuration and Agent Directives

**Status:** Approved
**Version:** 1.0.0
**Related Issue:** #04 — Configure OpenCode and Establish Agent Directives
**Milestone:** Phase 01 — Foundations and Architecture
**OpenCode Version:** 2.2.7

## 1. Objective

Establish a minimal, maintainable OpenCode project configuration that automatically loads the essential Infinite Ventures project rules and provides explicit operational directives to the agent.

The configuration must preserve existing project documentation as the authoritative source of project rules and ensure that the agent follows the approved Spec-Driven Development (SDD) workflow.

## 2. Business and Technical Value

- Reduce reliance on manually reminding the agent to read project documentation.
- Establish consistent project instructions across OpenCode sessions.
- Reduce contradictory or duplicated instructions.
- Improve compliance with SDD, INVEST, scope restrictions, and approval requirements.
- Establish reproducible verification of instruction loading and agent behavior.

## 3. Context and References

Authoritative references:

- `docs/PROJECT_CONTEXT.md`
- `docs/ARCHITECTURE.md`
- `docs/ROADMAP.md`
- `docs/templates/SPEC_TEMPLATE.md`
- `docs/templates/INVEST_CHECKLIST.md`
- GitHub Wiki — authoritative Game Design Document.
- OpenCode 2.2.7 official documentation and supported configuration schema.

The GitHub Wiki remains the functional game design authority.

Existing project documentation must not be replaced or independently reinterpreted by agent instructions.

## 4. Dependencies

- Issue #01 — Initial technical documentation.
- Issue #02 — Repository initialization and version control.
- Issue #03 — GitHub Projects and work management.
- Issue #05 — Technology stack and modular architecture documentation.
- OpenCode 2.2.7 installed and operational.
- Existing local provider and model configuration.

All dependencies are considered completed.

## 5. Scope

### Included

1. Create a root-level `AGENTS.md` containing concise operational directives.
2. Create a root-level `opencode.jsonc` using the supported OpenCode configuration schema.
3. Configure automatic loading of `docs/PROJECT_CONTEXT.md` through the `instructions` property.
4. Establish explicit document consultation rules for architecture, roadmap, SPEC preparation, and INVEST evaluation.
5. Establish instructions for consulting the GitHub Wiki when functional game design decisions are relevant.
6. Preserve existing provider and model configuration.
7. Define verification procedures for automatic instruction loading and agent behavior.
8. Document the resulting configuration and verification evidence.

### Excluded

- Game functionality or application implementation.
- Changes to the approved architecture.
- Changes to existing project methodology or SDD rules.
- Rewriting `PROJECT_CONTEXT.md` or other existing documentation.
- Installing dependencies, providers, models, or external services.
- GitHub MCP integration.
- Global OpenCode configuration changes.
- Automatic SPEC approval or implementation.
- Automatic GitHub Issue or Project modifications.
- Changes to GitHub Wiki content.

## 6. Requirements

### Functional Requirements

**FR-01 — Automatic Project Instructions**

OpenCode must automatically discover and load the root `AGENTS.md` when starting a session from the project workspace.

**FR-02 — Project Context Loading**

The project configuration must use the supported `instructions` property to load `docs/PROJECT_CONTEXT.md`.

**FR-03 — Single Source of Truth**

`PROJECT_CONTEXT.md` must remain the authoritative source for complete project rules. `AGENTS.md` must not duplicate those rules.

**FR-04 — Contextual Documentation**

The agent must be explicitly instructed to consult the relevant technical documentation before performing work that depends on it.

**FR-05 — Game Design Authority**

When functional game design information is required, the agent must consult the GitHub Wiki rather than inventing or independently defining product requirements.

**FR-06 — SDD Enforcement**

The agent must follow the approved workflow:

Context → Issue Analysis → SPEC Draft → INVEST Evaluation → Owner Approval → Implementation → Validation → Owner Acceptance.

**FR-07 — Implementation Authorization**

The agent must not implement changes without an approved SPEC and explicit authorization.

**FR-08 — Scope Enforcement**

The agent must respect the authorized files, implementation constraints, and scope defined by the approved SPEC.

**FR-09 — Approval Independence**

The agent must not approve its own SPEC or claim owner acceptance.

**FR-10 — Existing Model Preservation**

The project configuration must not unintentionally replace the currently selected local provider or model.

### Technical Requirements

**TR-01**

Use the configuration format and schema supported by OpenCode 2.2.7.

**TR-02**

Use project-relative paths for repository instruction files.

**TR-03**

Avoid unsupported configuration properties, experimental mechanisms, and unnecessary plugins.

**TR-04**

The configuration must be version-controlled and reproducible within the repository.

**TR-05**

No credentials, tokens, or machine-specific secrets may be committed.

## 7. Acceptance Criteria

- **AC-01:** OpenCode recognizes the root `AGENTS.md` automatically.
- **AC-02:** The project configuration is valid according to the supported OpenCode schema.
- **AC-03:** `docs/PROJECT_CONTEXT.md` is automatically loaded through the configured instruction mechanism.
- **AC-04:** The agent can correctly identify the GitHub Wiki as the authoritative functional Game Design source and consult it when relevant.
- **AC-05:** The agent follows the documented SDD workflow and recognizes that implementation requires an approved SPEC and explicit authorization.
- **AC-06:** The agent respects authorized files and does not expand SPEC scope without approval.
- **AC-07:** The agent does not self-approve specifications or claim owner acceptance.
- **AC-08:** The existing local provider and model remain unchanged.
- **AC-09:** A controlled read-only verification demonstrates that the agent can identify and apply the project rules.
- **AC-10:** All created configuration files are limited to the approved file list.

## 8. Authorized Files

### Create

- `AGENTS.md`
- `opencode.jsonc`

### Modify

None.

### Delete

None.

Any additional file required during implementation must be reported with its purpose, justification, and impact before modification. Owner approval is required.

## 9. Implementation Constraints

1. Preserve all existing project documentation.
2. Do not duplicate complete project rules in `AGENTS.md`.
3. Use only documented OpenCode 2.2.7 configuration capabilities.
4. Do not use `/init` to generate or overwrite project instructions.
5. Do not change global OpenCode settings.
6. Do not change the provider or selected model.
7. Do not introduce MCP servers or external dependencies.
8. Do not implement game functionality.
9. Do not modify GitHub Issues, Projects, or Wiki.
10. Stop and report any configuration incompatibility or ambiguity.

## 10. Validation Strategy

### Configuration Validation

- Verify that OpenCode recognizes `opencode.jsonc`.
- Verify that the configuration schema accepts the defined properties.
- Verify that root `AGENTS.md` is discovered.
- Verify that `docs/PROJECT_CONTEXT.md` is loaded through `instructions`.
- Verify that no existing provider/model settings are unintentionally overridden.

### Behavioral Validation

Use controlled read-only scenarios to verify:

- Identification of the authoritative Game Design source.
- Recognition of all six INVEST principles.
- Recognition of the requirement for explicit SPEC approval.
- Refusal to modify files outside an authorized scope.
- Refusal to implement without an approved SPEC.
- Recognition that the agent cannot approve its own work.

### Stopping Conditions

Stop validation when all applicable acceptance criteria have passed.

If a behavior cannot be verified, report it as UNVERIFIED. Do not interpret a verbal claim from the model as proof of configuration loading or compliance.

## 11. Definition of Done

- All acceptance criteria have been evaluated.
- The two authorized configuration files have been created.
- OpenCode recognizes the project instructions.
- The project context is automatically loaded.
- Controlled behavioral checks have been executed.
- Existing project documentation remains intact.
- Existing provider and model configuration remains intact.
- No unauthorized files or settings have been changed.
- Verification results are documented.
- The project owner has reviewed and accepted the result.

## 12. Expected Deliverables

- Root `AGENTS.md`.
- Root `opencode.jsonc`.
- Documented configuration and validation results.
- Evidence for each acceptance criterion.

## 13. Risks and Open Questions

1. The exact runtime behavior of instruction loading must be verified in the installed OpenCode 2.2.7 environment.
2. The availability and reliability of `webfetch` must be verified when consulting the GitHub Wiki.
3. Automatic instruction loading does not guarantee perfect behavioral compliance by the selected model.
4. The project configuration must not unintentionally conflict with global OpenCode settings.
5. The appropriate validation method for proving instruction loading must be established before implementation.

## 14. INVEST Evaluation

| Principle | Verdict | Justification |
|---|---|---|
| Independent | PASS | All required project documentation and setup dependencies are completed. |
| Negotiable | PASS | Configuration details can be adjusted without changing the objective or approved constraints. |
| Valuable | PASS | Improves instruction consistency and SDD compliance. |
| Estimable | PASS | Limited to two configuration files and controlled validation. |
| Small | PASS | No game implementation, architecture changes, or external integrations are included. |
| Testable | PASS | Acceptance criteria define observable configuration and behavioral checks. |

**INVEST Result: 6/6 PASS**

**Approval:** Approved by the Project Owner.

Implementation is authorized only within the scope and constraints defined in this SPEC.

## 15. Execution Report

**Implementation Status:** Completed  
**Validation Status:** Completed  
**Acceptance Status:** Accepted by the Project Owner

### 15.1 Implemented Files

| File | Action | Result |
|---|---|---|
| `AGENTS.md` | Created | PASS |
| `opencode.jsonc` | Created | PASS |

No existing project files were modified or deleted.

### 15.2 Configuration Verification

- OpenCode version: 2.2.7.
- Project configuration recognized through `opencode debug config`.
- The `instructions` property references `docs/PROJECT_CONTEXT.md`.
- Existing global provider and model configuration preserved: `ollama/qwen3.8:27b`.
- Root `AGENTS.md` contents inspected and UTF-8 encoding verified.
- No global configuration changes or external integrations introduced.

### 15.3 Behavioral Verification

- Agent recognizes the project authority hierarchy and documentation rules.
- Agent identifies the six INVEST principles.
- Agent refuses implementation without an approved SPEC and explicit authorization.
- Agent refuses to approve its own SPEC.
- Agent recognizes the GitHub Wiki as the authoritative game design source.
- Two WebFetch operations to the GitHub Wiki were observed.
- Agent respects authorized file boundaries in controlled read-only scenarios.
- Agent recognizes that technical dependencies do not independently authorize scope expansion.

### 15.4 Acceptance Criteria

| Criterion | Result |
|---|---|
| AC-01 | PASS — configuration discovery and agent recognition observed |
| AC-02 | PASS — project configuration recognized |
| AC-03 | PASS — instruction path recognized and project rules identified |
| AC-04 | PASS — Wiki consultation observed |
| AC-05 | PASS |
| AC-06 | PASS |
| AC-07 | PASS |
| AC-08 | PASS |
| AC-09 | PASS |
| AC-10 | PASS |

### 15.5 Verification Limitations

- Automatic instruction loading was evaluated through configuration inspection and agent behavior; the complete internal model context was not independently inspected.
- Wiki access was confirmed through WebFetch execution records; individual design claims were not independently verified against every source passage.
- Behavioral checks demonstrate observed compliance in the tested scenarios, not a guarantee of universal model compliance.

### 15.6 Final Result

The two authorized configuration files were created successfully.

The project configuration was recognized, the existing provider and model were preserved, and the controlled behavioral scenarios produced satisfactory results.

All acceptance criteria were evaluated and accepted by the Project Owner.

**SPEC-002: COMPLETED AND ACCEPTED.**