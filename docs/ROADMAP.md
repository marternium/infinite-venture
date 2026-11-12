# Infinite Ventures — Development Roadmap

**Project:** Infinite Ventures
**Repository:** `marternium/infinite-venture`
**Document type:** Development Roadmap
**Status:** Proposed
**Version:** 1.0

---

## 1. Purpose

This roadmap defines the high-level development phases for Infinite Ventures.

It establishes the implementation sequence, objectives, expected outcomes, and completion criteria for each phase.

The roadmap is a planning document, not an implementation specification. Individual implementation tasks must be defined through independent SPEC documents and evaluated against the INVEST principles before approval.

## 2. Development principles

Development will follow these principles:

- **Spec-Driven Development (SDD):** Every implementation task must be defined by an approved SPEC.
- **INVEST compliance:** Every SPEC must pass all six INVEST criteria before implementation.
- **Incremental delivery:** Each phase must produce a functional and verifiable result.
- **Architectural consistency:** Implementation must respect the decisions documented in `ARCHITECTURE.md`.
- **Design consistency:** Game mechanics and product decisions must remain aligned with the official Game Design Document (GDD) in the GitHub Wiki.
- **Controlled scope:** No unapproved features, dependencies, or architectural changes.
- **Continuous validation:** Every implementation must include bounded and reproducible validation.

## 3. Development phases

### Phase 01 — Foundations and Architecture

**Objective:** Establish the technical foundation and project structure required for incremental development.

**Expected outcomes:**
- Defined project structure and conventions.
- Established application entry points.
- Modular architecture and separation of responsibilities.
- Centralized game configuration and state foundations.
- Defined technical validation strategy.

**Completion criteria:**
- The project can be initialized and executed locally.
- The architecture is documented and consistently applied.
- Core modules have clear responsibilities.
- No unnecessary dependencies have been introduced.

### Phase 02 — Visual Identity and Interface

**Objective:** Build the visual foundation and user interface of Infinite Ventures.

**Expected outcomes:**
- Main game layout.
- Visual identity and design system.
- Corporate Credits display.
- Business cards and production indicators.
- Expansion and progression interface foundations.
- Responsive interface behavior.

**Completion criteria:**
- The main interface renders correctly.
- Visual components follow the approved design direction.
- Interface elements are structured independently from game logic.
- Layout remains usable across supported screen sizes.

### Phase 03 — Economy Engine

**Objective:** Implement the fundamental economic simulation.

**Expected outcomes:**
- Corporate Credits management.
- Business purchasing.
- Production calculations.
- Income generation.
- Production intervals.
- Cost scaling.
- Safe handling of large numerical values.

**Completion criteria:**
- Businesses generate credits according to their configuration.
- Purchases correctly update ownership and balances.
- Production calculations are independent of interface refresh frequency.
- Economic calculations produce consistent and testable results.

### Phase 04 — Managers, Upgrades and Automation

**Objective:** Introduce permanent business automation and production improvements.

**Expected outcomes:**
- Manager hiring system.
- Permanent automation after manager recruitment.
- Business upgrades.
- Production multipliers and improvements.
- Clear automation and upgrade states.

**Completion criteria:**
- Hiring a manager permanently automates the associated business.
- Automated production operates without user interaction.
- Upgrades correctly affect production.
- Automation and upgrade states remain consistent with the game state.

### Phase 05 — Expansion and Progression

**Objective:** Implement the progression system that allows the corporation to expand through increasingly ambitious stages.

**Expected outcomes:**
- Expansion unlock conditions.
- Six expansion stages.
- New maps or sectors for each stage.
- Stage-specific business availability.
- Milestone system.
- Continued operation of previously unlocked sectors.

**Completion criteria:**
- Expansion requirements are evaluated correctly.
- Unlocking a stage makes its associated content available.
- Previously unlocked sectors remain part of the empire.
- Milestones reflect meaningful progression beyond accumulated currency alone.

### Phase 06 — Persistence and Offline Progress

**Objective:** Preserve game progress and calculate eligible production while the player is away.

**Expected outcomes:**
- Versioned localStorage persistence.
- Save validation and recovery mechanisms.
- Save schema migration foundations.
- Last active timestamp tracking.
- Offline production calculations.
- Maximum offline duration of 12 hours.
- Protection against duplicate offline rewards.

**Completion criteria:**
- Game progress survives browser reloads.
- Invalid or incompatible saves are handled safely.
- Offline production only considers eligible automated businesses.
- Offline rewards are calculated and applied exactly once.
- Offline duration never exceeds the configured limit.

### Phase 07 — Prestige: Corporate Legacy

**Objective:** Introduce the permanent progression system that rewards players for restarting their empire.

**Expected outcomes:**
- Corporate Legacy prestige mechanic.
- Prestige eligibility conditions.
- Complete reset of ordinary progression.
- Prestige Shares currency.
- Permanent bonuses.
- Prestige history and progression records.

**Completion criteria:**
- Prestige can only be activated when its requirements are met.
- Ordinary progression is reset correctly.
- Permanent prestige progression is preserved.
- Prestige bonuses are applied consistently to subsequent runs.

### Phase 08 — QA, Balancing and Stabilization

**Objective:** Validate the complete game experience and prepare the application for a stable release.

**Expected outcomes:**
- Functional regression testing.
- Economic balancing.
- Progression and milestone balancing.
- Persistence and offline progression testing.
- Performance and browser compatibility checks.
- Bug fixes and technical improvements.
- Final documentation updates.

**Completion criteria:**
- Critical gameplay flows work consistently.
- No known critical defects remain unresolved.
- Economic progression is reasonably balanced.
- Save and offline systems behave reliably.
- The application is stable in its supported browser environment.

## 4. Phase dependencies and sequencing

The phases represent the recommended development sequence, not a rigid waterfall process.

| Phase | Depends primarily on |
|---|---|
| 01 — Foundations and Architecture | Project initialization |
| 02 — Visual Identity and Interface | Phase 01 |
| 03 — Economy Engine | Phase 01; interface foundations from Phase 02 |
| 04 — Managers, Upgrades and Automation | Phase 03 |
| 05 — Expansion and Progression | Phases 03 and 04 |
| 06 — Persistence and Offline Progress | Core state and economy systems |
| 07 — Corporate Legacy | Phases 03, 05 and 06 |
| 08 — QA, Balancing and Stabilization | All preceding phases |

Some work may be performed in parallel when dependencies allow it and the relevant SPECs are independently approved.

For example, interface development and economy development may overlap after the initial architecture is established.

Persistence foundations may also be introduced earlier if required by the architecture, while Phase 06 covers the complete persistence and offline progression implementation.

## 5. Phase lifecycle

Each development phase follows this workflow:

1. Review the phase objectives and dependencies.
2. Identify the necessary implementation work.
3. Draft individual SPEC documents.
4. Evaluate every SPEC using `INVEST_CHECKLIST.md`.
5. Obtain project owner approval.
6. Implement one approved SPEC at a time.
7. Execute its defined validation strategy.
8. Review implementation evidence and deviations.
9. Obtain final acceptance from the project owner.
10. Update project documentation and phase progress.

A phase is not considered complete merely because its implementation has finished. Its completion criteria must also be verified.

## 6. Scope management

The roadmap is a high-level planning document and may evolve as the project develops.

Changes to phase objectives, dependencies, or completion criteria must be documented and reviewed.

Individual implementation details belong in SPEC documents, while architectural decisions with long-term impact must be recorded in Architecture Decision Records (ADRs).

The roadmap must not be used to authorize implementation by itself.

## 7. Current project status

**Current phase:** Phase 01 — Foundations and Architecture

**Current activity:** Documentation and technical preparation.

**Implementation status:** Not started.

The first implementation SPECs will be defined and reviewed only after the project documentation has been completed and approved.

---

**Guiding principle:** Build Infinite Ventures one well-defined, independently verifiable piece at a time.