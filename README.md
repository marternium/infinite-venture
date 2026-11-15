# 🏢 Infinite Ventures

**Build an empire. Optimize everything. Conquer the universe.**

Infinite Ventures is a browser-based idle/incremental tycoon game where players build and expand a corporate empire, starting with local businesses and eventually reaching galactic dominance.

Through strategic investments, business automation, upgrades, and prestige progression, players transform a small enterprise into an interstellar megacorporation.

## 🚀 Project Status

<badge color="warning">In Development</badge>

The project is currently in its **Foundations and Architecture** phase.

The initial technical structure is being established before implementing the game's core systems and features.

## 🎮 Game Overview

The core gameplay loop revolves around:

1. Generate Corporate Credits (CC).
2. Purchase and expand businesses.
3. Hire managers to automate production.
4. Invest in upgrades to improve efficiency.
5. Reach milestones and unlock new opportunities.
6. Expand into new territories and industries.
7. Use prestige progression to build a stronger corporate legacy.

### Progression Stages

The corporate empire evolves through six major stages:

- **Local Entrepreneurship**
- **Industrial Powerhouse**
- **National Dominance**
- **Orbital Expansion**
- **Planetary Empire**
- **Galactic Dominance**

### Core Features

The planned game systems include:

- Business management and production.
- Corporate Credits economy.
- Managers and automation.
- Business upgrades and milestones.
- Expansion and progression.
- Offline progress (up to 12 hours).
- Prestige system and permanent bonuses.
- Corporate Legacy progression.

## 🛠️ Technology Stack

Infinite Ventures uses a lightweight, modular web architecture.

| Technology | Purpose |
|---|---|
| HTML5 | Application structure |
| CSS3 | Styling and visual presentation |
| JavaScript ES Modules | Application logic |
| Vite | Development server and production builds |
| localStorage | Local game persistence |

The project intentionally avoids frontend frameworks and mandatory backend services.

## 📁 Project Architecture

The application follows a modular architecture designed to keep responsibilities separated and allow incremental development.

The logical systems include:

- Core
- Configuration
- Game State
- Economy
- Business Management
- Managers
- Upgrades
- Milestones
- Expansion
- Persistence
- Offline Progress
- Prestige
- User Interface

Physical modules will be introduced incrementally as their implementation is authorized through the project's Specification-Driven Development workflow.

## 💻 Getting Started

### Prerequisites

- Node.js compatible with the project's Vite version.
- npm.

### Installation

Clone the repository:

```bash
git clone https://github.com/marternium/infinite-venture.git
cd infinite-venture
```

Install dependencies:

```bash
npm install
```

### Development

Start the local development server:

```bash
npm run dev
```

Vite will provide a local URL where the application can be accessed.

### Production Build

Generate the production build:

```bash
npm run build
```

The generated static application is placed in the `dist/` directory.

## 📐 Development Methodology

Infinite Ventures follows **Specification-Driven Development (SDD)**.

Development work is organized through:

**Milestone → Issue → Specification → Implementation → Validation → Acceptance**

Each implementation must have an approved specification that defines its scope, requirements, authorized files, acceptance criteria, and validation strategy.

Specifications are evaluated against the six INVEST principles:

- Independent
- Negotiable
- Valuable
- Estimable
- Small
- Testable

The Project Owner retains final approval and acceptance authority.

## 📚 Documentation

The repository contains technical documentation describing the project's architecture, development constraints, roadmap, and specification workflow.

The [GitHub Wiki](https://github.com/marternium/infinite-venture/wiki) is the authoritative source for the Game Design Document (GDD) and game design decisions.

Technical documentation must remain consistent with the approved game design.

## 🎨 Visual Identity

The game's visual direction combines:

- Industrial steampunk.
- Elegant cyberpunk.
- Science-fiction aesthetics.
- Corporate satire.

The visual palette is built around navy, charcoal, copper, bronze, gold, cyan, magenta, and violet.

The overall experience aims to combine strategic progression with an increasingly absurd corporate empire.

## 📌 Repository

**GitHub:** https://github.com/marternium/infinite-venture

---

*Build bigger. Automate smarter. Expand further.*

**Infinite Ventures — Your ambition has no limits.**