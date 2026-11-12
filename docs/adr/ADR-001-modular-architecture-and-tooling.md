# Architecture Decision Record: Modular Architecture and Tooling

**Document ID:** ADR-001
**Project:** Infinite Ventures
**Status:** Accepted (approved by project owner on 2026-11-12)
**Reference:** SPEC-001: Modular Architecture and Tooling

---

## Context

Infinite Ventures requires a scalable, maintainable architectural foundation to support incremental development of an idle/tycoon game with multiple expansion stages. The specification requires separation of concerns between gameplay logic, application state, persistence, and user interface.

Key challenges:
- Supporting six progressive expansion stages without rewriting core systems
- Maintaining consistency between visual presentation and underlying economic/progression rules
- Enabling testable modules that can be developed independently
- Avoiding hidden dependencies and coupling between subsystems
- Preserving architectural boundaries while allowing flexibility for future specifications

Previous architectural decisions are documented in ARCHITECTURE.md, which establishes the project's logical system boundaries and technical constraints. This record formalizes the approved implementation technologies and development tooling.

## Decision

This record formalizes the approved technology stack and establishes conventions for module organization, dependency management, and development tooling within the Infinite Ventures architecture.

### Approved Technology Stack

| Layer | Technology | Responsibility |
|-------|-----------|----------------|
| Markup | HTML5 | Application structure and DOM entry point with semantic markup for UI elements |
| Styling | CSS3 | Visual presentation using modern layout capabilities (Flexbox, Grid) with design tokens |
| Programming Language | Native JavaScript | Application logic without frontend framework, ES6+ features only |
| Module System | ECMAScript Modules | Code organization through native `import`/`export` with explicit boundaries |
| Build Tool | Vite | Development server, HMR, asset processing (development tooling only) |
| Persistence | Browser localStorage | Game state serialization and retrieval with schema versioning support |
| Hosting Model | Static web hosting | HTTP/HTTPS served files without backend processes |

### Conventions Established

#### Module System
- **Clear module responsibilities**: Each module has a single, well-defined purpose and scope. Responsibilities do not cross architectural boundaries (e.g., business logic modules handle state management, UI modules handle rendering).
- **Explicit import/export interfaces**: All public APIs are exposed through documented `import`/`export` statements. Private implementation details are encapsulated within module boundaries.
- **Explicit and controlled dependencies**: Modules declare their dependencies explicitly through import statements. Dependencies are limited to what is required for core functionality, avoiding transitive coupling.
- **Separation of business logic from UI**: Business logic modules (game state, progression systems, economy) remain independent from UI rendering modules. Data flows in one direction: the UI requests data and receives updates, but does not directly modify internal business logic.
- **Clear state ownership**: Modules have clearly defined responsibilities for the state they manage. The Game State system maintains the authoritative representation of gameplay state. The Persistence system is responsible for state serialization, loading, and saving through localStorage. Gameplay modules must not independently write arbitrary portions of localStorage. State transitions are triggered through explicit actions within the owning system.
- **Avoidance of circular dependencies**: Module imports are designed to create a directed acyclic graph (DAG). UI modules depend on business logic, but business logic modules do not directly import UI components—they access rendered data through observable state updates.

#### CSS Organization
- **Base styles**: Global reset, box model, and fundamental typography rules
- **Design tokens**: Color palettes, spacing scales, and theme variables shared across the application
- **Layout**: Grid, flexbox, and spatial arrangement patterns for page structure
- **Components**: Styled units for reusable UI elements (buttons, inputs, cards)
- **Interface sections**: Page-level styling for navigation, headers, and footer areas
- **Utilities**: Helper classes for common styling needs (text alignment, margins, displays)

#### HTML Responsibilities
- HTML provides semantic markup for UI components and game entities
- DOM structure reflects logical system boundaries
- HTML remains independent of business logic implementation

#### Development Tooling
- Vite approved as development server and production build tool; installation and configuration are outside SPEC-001 scope
- Production builds target static hosting environments
- No runtime dependencies beyond the standard browser environment

## Consequences

### Positive Impacts
1. **Explicit architectural boundaries**: The technology stack clarifies separation between markup, styling, and logic layers, enabling better code organization and team workflow.

2. **No frontend framework required**: Eliminates learning curve for new contributors and reduces runtime complexity by removing abstraction overhead.

3. **Native module system**: ES6+ modules provide clear dependency graph visualization through `import` statements, making it easier to identify coupling issues.

4. **Development efficiency**: Vite's HMR support enables rapid prototyping and iterative development without application restarts.

5. **Static hosting compatibility**: All components work with any static hosting solution (GitHub Pages, Netlify, Vercel, etc.) without server-side dependencies.

6. **Deterministic build output**: Controlled asset processing simplifies deployment workflows.

### Potential Concerns
1. **Build tool maintenance**: Vite requires npm/node installation for local development. Alternative: Provide comprehensive documentation for alternative static hosting setups.

2. **Large-scale bundling**: Production-optimized build strategy may be required for future growth. Potential code splitting and lazy loading could be evaluated in future specifications as requirements emerge.

3. **No CSS preprocessor**: Direct CSS usage requires manual preprocessing for variable-like features (CSS variables). Mitigation: CSS Custom Properties (variables) provide equivalent functionality without compilation step.

## Alternatives Considered

### Alternative 1: React/Vue Framework
**Pros**: Component reusability, ecosystem tools, established patterns
**Cons**: Runtime abstraction overhead, additional dependency management
**Note**: The project owner approved native JavaScript without a frontend framework as documented in PROJECT_CONTEXT.md Section 4.2. This alternative was not experimentally evaluated.

### Alternative 2: CSS Framework (Tailwind)
**Pros**: Rapid styling development, utility-first approach
**Cons**: Adds build-time compilation step, increases bundle size
**Note**: Vite was selected by the project owner for workflow suitability. This alternative was not experimentally evaluated. Project owner approved native CSS without a CSS framework as per PROJECT_CONTEXT.md Section 4.2.

### Alternative 3: Node.js Server Runtime
**Pros**: Backend processing capabilities, server-side rendering
**Cons**: Requires server deployment (violates static hosting requirement), introduces persistent dependencies
**Note**: Vite was selected by the project owner for workflow suitability. Project constraints requiring static web hosting are specified in PROJECT_CONTEXT.md Sections 4.1 and 4.2.

### Alternative 4: Webpack/Rollup
**Pros**: Mature bundler ecosystem
**Cons**: Different configuration patterns, alternative performance characteristics, distinct developer workflows
**Note**: Vite was selected by the project owner for development workflow suitability. Alternative bundlers were not evaluated in this specification.

## References

- **SPEC-001 - Modular Architecture and Tooling.md**: `docs/SPECs/SPEC-001 - Modular Architecture and Tooling.md`
- **ARCHITECTURE.md**: Updated with technology stack documentation (Section 12)
- **PROJECT_CONTEXT.md**: Section 4.2 Approved Technology Stack

## Status History

| Date | Version | Change | Author |
|------|---------|--------|--------|
| 2026-11-12 | 1.0 | Initial decision record created per SPEC-001 requirements | Project Owner |
| 2026-11-12 | 1.1 | Status updated to Accepted; CSS organization expanded with six approved categories; module system conventions fully documented | Project Owner |

---

*This architecture decision record documents accepted architectural decisions for the Infinite Ventures project.*
