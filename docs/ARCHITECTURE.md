# Infinite Ventures — Architecture

**Document version:** 1.0
**Status:** Initial architectural guidelines
**Project:** Infinite Ventures
**Development methodology:** Spec-Driven Development (SDD)

---

# 1. Architectural Vision

Infinite Ventures must be designed as a modular, extensible and maintainable browser game.

The architecture must support incremental development without requiring large-scale rewrites when new gameplay systems or expansion stages are introduced.

The initial implementation will use HTML, CSS and JavaScript, without mandatory external services.

The architecture must prioritize:

- Separation of concerns.
- Explicit module responsibilities.
- Low coupling.
- High cohesion.
- Testability.
- Data-driven configuration.
- Predictable state transitions.
- Controlled dependency management.
- Incremental extensibility.

This document defines architectural principles and logical boundaries. It does not prescribe a final physical file structure before the relevant specifications are approved.

# 2. Architectural Principles

## 2.1. Separation of concerns

Gameplay logic, application state, persistence and user interface must have clearly defined responsibilities.

The user interface must not become the owner of economic calculations or progression rules.

## 2.2. Single source of truth

The game must maintain a consistent central representation of its current state.

Individual modules must not maintain conflicting copies of authoritative gameplay data.

## 2.3. Data-driven design

Business definitions, prices, production values, upgrades, milestones and expansion stages should be configurable independently from the systems that process them.

Adding new businesses or expansion stages should primarily involve adding or updating configuration data rather than rewriting core logic.

## 2.4. Explicit dependencies

Modules must depend only on the interfaces and responsibilities they actually require.

Avoid circular dependencies and hidden global coupling.

## 2.5. Incremental architecture

Architecture must evolve alongside approved specifications.

Do not implement abstractions, frameworks or systems solely because they might be useful in a hypothetical future scenario.

## 2.6. Testability

Core gameplay rules must be testable independently from visual presentation and browser interaction whenever reasonably possible.

# 3. Logical System Boundaries

The following systems define the conceptual architecture.

Their physical implementation and module boundaries will be established through approved specifications.

## 3.1. Core

Responsibilities:

- Application initialization.
- System coordination.
- Lifecycle management.
- Controlled startup and shutdown behavior.

Core must not absorb the responsibilities of specialized gameplay systems.

## 3.2. Configuration

Responsibilities:

- Business definitions.
- Expansion stage definitions.
- Upgrade definitions.
- Milestone definitions.
- Economy parameters.
- Global gameplay settings.

Configuration data should be separated from execution logic.

## 3.3. Game State

Responsibilities:

- Represent the current game state.
- Maintain consistent gameplay information.
- Coordinate state transitions.
- Expose controlled state updates.

The state model must distinguish between ordinary progression and permanent prestige progression.

## 3.4. Economy

Responsibilities:

- Corporate Credits management.
- Business purchase calculations.
- Production calculations.
- Income generation.
- Cost calculations.
- Economic multipliers.
- Large-number representation and formatting.

The economy system must avoid unsafe numeric operations as values grow.

## 3.5. Business Management

Responsibilities:

- Business availability.
- Business ownership.
- Owned quantities.
- Production configuration.
- Business-specific progression.
- Business automation status.

Business definitions must remain independent of the rendering layer.

## 3.6. Managers

Responsibilities:

- Manager availability.
- Hiring costs.
- Permanent business automation.
- Manager-related bonuses.

Hiring a manager must permanently automate the associated business.

Automation status must survive saving, loading and prestige rules where applicable.

## 3.7. Upgrades

Responsibilities:

- Upgrade availability.
- Purchase requirements.
- Upgrade costs.
- Production bonuses.
- Multipliers.
- Upgrade ownership.

Upgrades must have explicit effects and must not introduce undocumented modifications to the economy.

## 3.8. Milestones

Responsibilities:

- Progression requirements.
- Milestone completion.
- Rewards.
- Expansion unlock conditions.
- Progression notifications.

Milestones must support different requirement types without embedding stage-specific logic into the core progression engine.

## 3.9. Expansion

Responsibilities:

- Expansion stage definitions.
- Map or sector availability.
- Stage unlock requirements.
- Active sector selection.
- Business availability by stage.
- Sector-specific progression.

Previously unlocked sectors must remain part of the player's empire.

Their production must continue according to their automation and operational conditions.

## 3.10. Persistence

Responsibilities:

- Saving the game.
- Loading saved games.
- Data validation.
- Save format versioning.
- Migration between supported save versions.
- Recovery from invalid or incomplete data when possible.

Persistence must not depend on the user interface.

## 3.11. Offline Progress

Responsibilities:

- Recording the previous session timestamp.
- Calculating elapsed time.
- Enforcing the 12-hour accumulation limit.
- Calculating eligible offline production.
- Applying offline rewards exactly once.
- Preventing duplicate reward calculations.

Offline calculations must use deterministic and testable rules.

## 3.12. Prestige

Responsibilities:

- Prestige eligibility.
- Complete ordinary progression reset.
- Prestige reward calculation.
- Prestige Shares.
- Permanent bonuses.
- Preservation of permanent progression.

Prestige must explicitly distinguish between resettable and persistent state.

The system must not accidentally erase permanent progression.

## 3.13. User Interface

Responsibilities:

- Displaying game information.
- Rendering businesses and maps.
- Presenting available actions.
- Receiving player interactions.
- Communicating state changes.
- Displaying feedback and notifications.

The UI must consume gameplay state and request actions through controlled interfaces.

It must not independently implement economic or progression rules.

# 4. State Architecture

The game state must distinguish at least two conceptual categories.

## 4.1. Ordinary progression state

Contains information that belongs to the current empire run.

Examples:

- Corporate Credits.
- Owned businesses.
- Business quantities.
- Manager ownership.
- Purchased upgrades.
- Completed milestones.
- Unlocked expansion stages.
- Current active map.

This state is subject to the complete prestige reset.

## 4.2. Permanent progression state

Contains information that survives prestige.

Examples:

- Prestige Shares.
- Purchased permanent bonuses.
- Total prestige history.
- Other explicitly designated permanent progression data.

The prestige system must reset ordinary progression without destroying permanent progression.

## 4.3. State integrity

State modifications must be controlled and predictable.

Systems must avoid directly modifying unrelated state properties.

Invalid or impossible values must be rejected or safely handled.

# 5. Economic Architecture

The economy uses one universal currency:

**Corporate Credits (CC).**

All expansion stages use the same currency.

Economic calculations must be independent of visual formatting.

The architecture must support:

- Business-specific costs.
- Configurable price scaling.
- Production per business.
- Production intervals.
- Production multipliers.
- Global bonuses.
- Large values.
- Consistent rounding and precision rules.

The numerical representation strategy must be selected and validated before implementing the complete economy.

JavaScript floating-point limitations must be considered.

# 6. Production and Automation

Production must be represented through explicit business rules.

The system must distinguish between:

- Business ownership.
- Business production capability.
- Manual interaction requirements.
- Manager-based automation.
- Production modifiers.

Managers provide permanent automation after hiring.

Production calculations must be independent from how frequently the interface refreshes.

The visual refresh rate must never determine the actual economic result.

# 7. Expansion Architecture

Expansion is organized into six progressively unlocked stages.

Each stage provides a new map or sector.

Expansion definitions must be data-driven.

The architecture must support:

- Independent stage definitions.
- Stage-specific business catalogs.
- Stage-specific visual identities.
- Unlock requirements.
- Persistent access to previously unlocked sectors.
- Continued production across unlocked sectors.

Adding a seventh stage in the future must not require rewriting the existing progression engine.

# 8. Offline Progress Architecture

Offline progress is limited to 12 hours.

The system must:

1. Record a reliable timestamp when the game is saved.
2. Calculate the elapsed time when the game resumes.
3. Clamp eligible time to the configured maximum.
4. Calculate production for eligible automated businesses.
5. Apply the resulting rewards once.
6. Persist the updated state.

The design must account for:

- Browser closure.
- Browser refresh.
- Device clock changes.
- Invalid timestamps.
- Repeated loading.
- Save corruption.

Offline calculations must not produce duplicate rewards.

# 9. Persistence Architecture

Initial persistence will use browser local storage.

The persistence layer must:

- Serialize the necessary game state.
- Validate loaded data.
- Include a save schema version.
- Support future migrations.
- Handle missing or invalid data safely.
- Preserve permanent progression.

Game systems must not independently write arbitrary portions of the save data without a defined persistence contract.

# 10. Prestige Architecture

Prestige is a complete reset of ordinary progression in exchange for permanent bonuses.

The architecture must separate:

- Eligibility evaluation.
- Reward calculation.
- Reset execution.
- Permanent reward application.
- State persistence.

Prestige must be an explicit and controlled state transition.

The reset operation must be atomic from the perspective of the game state: the player must never be left with a partially reset empire.

# 11. User Interface Architecture

The UI must remain separate from business logic.

It should support:

- Multiple expansion maps.
- Dynamic business catalogs.
- Resource and production displays.
- Upgrade interfaces.
- Manager interfaces.
- Milestone notifications.
- Offline reward summaries.
- Prestige interactions.

UI rendering must reflect authoritative game state.

Repeated rendering must not accidentally trigger purchases, production rewards or other gameplay actions.

# 12. Technical Constraints

Initial implementation constraints:

- HTML.
- CSS.
- JavaScript.
- Browser-based execution.
- Local persistence.
- No mandatory external APIs.
- No mandatory backend.
- No mandatory user accounts.
- No unnecessary frameworks or dependencies.

Any deviation from these constraints must be justified in an approved SPEC or architectural decision record.

# 13. Architecture Decision Records

Significant architectural decisions must be recorded as ADR documents.

Each ADR should contain:

- Identifier.
- Title.
- Status.
- Context.
- Decision.
- Consequences.
- Alternatives considered when relevant.

An approved ADR becomes part of the project's technical reference.

Superseded decisions must remain documented for historical traceability.

# 14. Architectural Evolution

This document is an initial architectural baseline.

It may evolve through approved specifications and ADRs.

Changes must be explicit and must not silently contradict accepted requirements.

The implementation must prioritize the smallest architecture that correctly supports the approved functionality.

**Guiding principle: Build only what the current approved scope requires, while preserving the ability to extend the game without unnecessary rewrites.**