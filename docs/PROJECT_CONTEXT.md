# Infinite Ventures — Project Context

## 1. Project Identity

**Project name:** Infinite Ventures
**Repository:** `marternium/infinite-venture`
**Repository URL:** https://github.com/marternium/infinite-venture
**Project type:** Idle / Incremental Tycoon
**Initial platform:** Web browser
**Primary technologies:** HTML, CSS and JavaScript
**Development approach:** Spec-Driven Development (SDD)
**Specification quality standard:** INVEST

Infinite Ventures is an incremental business management game in which the player grows a small business into a corporation capable of dominating the galaxy and eventually the universe.

The game combines absurd corporate humor, industrial steampunk aesthetics, elegant cyberpunk interfaces and science fiction.

**Tagline:** From humble beginnings to infinite possibilities.

## 2. Product Vision

The player starts with a small and questionable business, generates revenue, acquires additional businesses, hires managers, improves production and expands into increasingly ambitious markets.

The long-term progression includes six expansion stages:

1. Local Entrepreneurship.
2. Industrial Powerhouse.
3. National Dominance.
4. Orbital Expansion.
5. Planetary Empire.
6. Galactic Dominance.

Each expansion stage unlocks a new map or sector with its own businesses, visual identity and progression objectives.

The complete product vision and gameplay rules are documented in the official Game Design Document.

## 3. Official Design Documentation

**Game Design Document (GDD):**

https://github.com/marternium/infinite-venture/wiki/Game-Design-Document-1.0

The GitHub Wiki is the authoritative source for product design decisions, gameplay rules, progression, economy concepts and the overall game vision.

Repository documentation must remain consistent with the approved GDD.

Do not independently redefine gameplay mechanics or contradict documented design decisions.

If a specification reveals ambiguity or a conflict with the GDD, stop and report it instead of inventing a solution.

## 4. Core Design Decisions

The following decisions have already been established and must be respected:

- Currency: Corporate Credits (CC), shared across all expansion stages.
- Offline progression: enabled, with a maximum accumulation period of 12 hours.
- Managers: hiring a manager permanently automates the associated business.
- Expansion: each stage unlocks a new map or sector.
- Prestige: complete reset of ordinary empire progression in exchange for permanent bonuses.
- Prestige system name: Corporate Legacy.
- Prestige permanent currency: Prestige Shares.
- Initial persistence strategy: browser local storage.
- Initial execution model: local browser application without mandatory external services.

These are product-level decisions, not implementation instructions.

## 5. Development Methodology

The project follows Spec-Driven Development (SDD).

All implementation work must be driven by explicit, approved specifications.

The development hierarchy is:

1. Game Design Document: defines the product.
2. Project phases: organize development objectives.
3. Specifications (SPECs): define individual implementation units.
4. Implementation: executes an approved SPEC.
5. Validation: verifies its acceptance criteria.
6. Acceptance: confirms completion and authorizes subsequent work.

**Important distinction:**

Project phases are development stages.

Game expansion stages are progression levels within the game.

They are different concepts and must never be confused.

## 6. INVEST Requirements

Every SPEC must be evaluated against all six INVEST principles:

- **Independent:** minimizes unnecessary dependencies.
- **Negotiable:** defines expected outcomes without prematurely prescribing every implementation detail.
- **Valuable:** provides identifiable product, technical or quality value.
- **Estimable:** has sufficiently clear scope to estimate its effort.
- **Small:** has a limited and manageable implementation scope.
- **Testable:** includes objective and reproducible acceptance criteria.

A SPEC that does not adequately satisfy INVEST must be revised or decomposed before implementation.

Dependencies between specifications are permitted when explicitly documented and justified.

## 7. Specification Execution Rules

The development agent must follow these rules:

1. Never implement work without an approved SPEC.
2. Work exclusively inside the current repository.
3. Never create another project root or duplicate project directory.
4. Respect the scope and authorized file list of each SPEC.
5. Do not modify unrelated files.
6. Avoid unnecessary rewrites of existing files.
7. Do not install dependencies or tools without explicit justification and authorization.
8. Do not introduce external services unless explicitly approved.
9. Do not invent product requirements.
10. Report ambiguities, blockers and deviations explicitly.
11. Do not silently expand the scope of a SPEC.
12. Do not proceed to another SPEC without authorization.

## 8. Validation Rules

Every SPEC must define its own validation strategy before implementation begins.

The agent must:

- Use the validation methods explicitly defined in the SPEC.
- Execute only relevant checks.
- Avoid redundant or equivalent validation attempts.
- Avoid installing additional tools merely to try alternative validation strategies.
- Stop when all acceptance criteria have been verified.
- Report failures honestly.
- Distinguish between verified results and unverified assumptions.

A successful implementation must never be declared without sufficient validation evidence.

## 9. Documentation Rules

The repository contains technical documentation and implementation specifications.

The GitHub Wiki contains the authoritative product design documentation.

The development agent must:

- Keep technical documentation synchronized with accepted implementation changes.
- Record significant architectural decisions in Architecture Decision Records (ADR).
- Avoid duplicating the entire GDD inside the repository.
- Reference the official Wiki when product context is required.
- Never modify product-level decisions without explicit approval.

## 10. Current Project Status

**Project stage:** Pre-implementation.

The GitHub repository has been created and cloned locally.

The official GDD is available in the GitHub Wiki.

No application implementation has been started.

The initial objective is to establish the technical documentation, architecture principles, reusable SPEC template and INVEST evaluation process.

Implementation will begin only after the initial documentation and first specifications have been reviewed and approved.

## 11. Guiding Principle

Build Infinite Ventures incrementally, with controlled scope, explicit decisions and verifiable results.

Prefer small, well-defined and maintainable implementations over large speculative changes.

**One approved SPEC at a time.**