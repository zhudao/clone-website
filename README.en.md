# Clone Website

English | [中文](./README.md)

> A tech-stack agnostic and agent-agnostic website cloning Skill — pixel-perfectly reverse-engineer any website into a clean, modern codebase

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Tech Stack: Agnostic](https://img.shields.io/badge/Tech%20Stack-Agnostic-blueviolet)](#tech-stack-agnostic)
[![Agent: Agnostic](https://img.shields.io/badge/Agent-Agnostic-success)](#supported-ai-coding-agents)

## Features

- **🔧 Tech-Stack Agnostic** — No React/Next.js lock-in. Developers freely choose framework, CSS solution, and build tool
- **🤖 Agent Agnostic** — No lock-in to a specific AI coding agent. Supports Claude Code, Codex, Cursor, Windsurf, Cline, Trae, and more
- **🎯 Pixel-Perfect** — Extracts exact CSS values via `getComputedStyle()`, not estimates
- **🎭 Multi-State Extraction** — Captures default, hover, scroll, and click states for every element
- **🧩 Component-Based Build** — Splits by section, each component has a detailed spec file as a build contract
- **📱 Responsive** — Extracts at desktop (1440px), tablet (768px), and mobile (390px) viewports
- **🎬 Behavior Replication** — Extracts not just static styles but scroll animations, hover effects, tab switching, and other interactions
- **📦 Real Assets** — Downloads real images, videos, SVGs, and fonts instead of using placeholders
- **✅ Verifiable Builds** — Every component is verified to compile, and the final full project build must pass

## Supported AI Coding Agents

This Skill follows the standard Skill specification (`SKILL.md` + YAML frontmatter) and can be installed on any AI coding agent that supports the Skill mechanism:

| Agent | Skill Directory | Status |
|---|---|---|
| [Claude Code](https://docs.anthropic.com/en/docs/claude-code) | `~/.claude/skills/` or `.claude/skills/` | Recommended |
| [Codex CLI](https://github.com/openai/codex) | `.codex/skills/` | Supported |
| [Cursor](https://cursor.com/) | `.cursor/` (via rules) | Supported |
| [Windsurf](https://codeium.com/windsurf) | `.windsurf/workflows/` | Supported |
| [Cline](https://github.com/cline/cline) | `.cline/` | Supported |
| [Trae](https://trae.cn/) | `.trae/skills/` | Supported |
| [OpenCode](https://opencode.ai/) | `.opencode/commands/` | Supported |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `.gemini/commands/` | Supported |
| [GitHub Copilot](https://github.com/features/copilot) | `.github/` (via instructions) | Supported |
| [Amazon Q](https://aws.amazon.com/q/developer/) | `.amazonq/` | Supported |
| [Augment Code](https://www.augmentcode.com/) | `.augment/commands/` | Supported |
| [Aider](https://aider.chat/) | `.aider.conf.yml` | Supported |
| [Continue](https://continue.dev/) | `.continue/` | Supported |
| [Roo Code](https://github.com/RooCodeInc/Roo-Code) | `.roo/` | Supported |

> **Note**: Skill loading mechanisms vary slightly across agents. Refer to your agent's official docs for installation details. This repository uses **flat layout** (`SKILL.md` at the repository root), which is the most universal structure.

## Installation

### Option 1: Git Clone (Recommended)

Clone this repository directly into your AI coding agent's Skill directory:

```bash
# Claude Code (global install)
git clone https://github.com/huangmingfu/clone-website.git ~/.claude/skills/clone-website

# Claude Code (project-level install)
git clone https://github.com/huangmingfu/clone-website.git .claude/skills/clone-website

# Codex CLI
git clone https://github.com/huangmingfu/clone-website.git .codex/skills/clone-website

# Trae
git clone https://github.com/huangmingfu/clone-website.git .trae/skills/clone-website
```

For other agents, refer to the Skill directory path in the table above and clone the repository to the corresponding location.

### Option 2: Using skillz Package Manager (Claude Code)

If you use [skillz](https://github.com/jakegoldsborough/skillz) (a Skill package manager for Claude Code):

```bash
skillz install github:huangmingfu/clone-website
```

### Option 3: Manual Download

Download the `SKILL.md` file and place it in your AI coding agent's Skill directory, named as `clone-website/SKILL.md`.

## Usage

Invoke the Skill in your AI coding agent by typing:

```
/clone-website <target-website-url>
```

For example:
```
/clone-website https://example.com
```

You can also clone multiple websites at once:
```
/clone-website https://example.com https://another-site.com
```

> **Note**: The way to invoke a Skill varies slightly across agents. Most agents support the `/skill-name` syntax, while some may trigger via natural language descriptions (e.g., "help me clone this website https://example.com"). The Skill will ask for your preferred tech stack (framework, CSS solution, build tool) before starting. Choose based on your needs.

## Workflow

The Skill executes a five-phase pipeline:

### Phase 1: Reconnaissance
- Full-page screenshots (desktop 1440px + mobile 390px)
- Global extraction: fonts, colors, favicon, global UI patterns
- Mandatory interaction sweep: scroll sweep, click sweep, hover sweep, responsive sweep
- Page topology mapping: record each section's order, layout, and interaction model

### Phase 2: Foundation Build
- Update font configuration
- Update global styles (color tokens, spacing, keyframe animations, global scroll behavior)
- Create type definitions (if using TypeScript)
- Extract SVG icons as named components
- Download global assets (images, videos, fonts)
- Verify project builds successfully

### Phase 3: Component Specification and Build
For each section, execute a three-step loop:
1. **Extract** — Screenshot, extract CSS, extract multi-state styles, extract real content, identify assets, assess complexity
2. **Write Spec File** — Create a detailed component spec file under `docs/research/components/`
3. **Build Component** — Build the component based on the spec file, verify compilation

### Phase 4: Page Assembly
- Import all section components
- Implement page-level layout (scroll containers, column structures, sticky positioning, z-index layering)
- Connect real content to component props
- Implement page-level behaviors (scroll snap, scroll-driven animations, IntersectionObserver, etc.)
- Verify full project build passes

### Phase 5: Visual QA Diff
- Side-by-side comparison screenshots (original vs clone)
- Compare at both desktop and mobile
- Test all interactive behaviors
- Fix any discrepancies found

## Tech Stack Agnostic

This Skill is **completely tech-stack agnostic**. In the Pre-Flight phase, the Skill will mandatorily ask for your preferred tech stack:

| Category | Options (not limited to) |
|---|---|
| **Framework** | React, Vue, Svelte, Solid, Astro, vanilla HTML, Angular, Preact, Lit, Qwik... |
| **CSS Solution** | Tailwind CSS, UnoCSS, CSS Modules, styled-components, vanilla CSS, Sass, Less, Emotion, Panda CSS... |
| **Build Tool** | Vite, Next.js, Nuxt, SvelteKit, webpack, Rollup, esbuild, Parcel, Astro, TanStack Start... |

You can also choose **vanilla HTML + CSS + JavaScript** (no framework), the Skill supports it equally.

**Key Principle**: The tech stack is decided by you. The Skill does not assume, recommend, or default to any specific tech stack.

## Prerequisites

- [Node.js](https://nodejs.org/) 18+ (for running asset download scripts)
- An AI coding agent that supports the Skill mechanism (see [Supported AI Coding Agents](#supported-ai-coding-agents))
- A browser automation MCP tool (e.g., Chrome DevTools MCP, Playwright MCP, browser-use, etc.)

## Use Cases

- **Platform Migration** — Migrate your own website from WordPress/Webflow/Squarespace to a modern codebase
- **Lost Source Recovery** — Your site is live but the repo is gone; recover the code in a modern format
- **Learning & Research** — Deconstruct how production sites achieve specific layouts, animations, and responsive behaviors by working with real code
- **Design Restoration** — Restore design mockups or reference websites into runnable code for learning

## Notes / Disclaimer

### ✅ Encouraged Uses
- Cloning your own websites for migration or backup
- Learning and researching implementation techniques of production websites
- Restoring design references into code for learning purposes

### ❌ Prohibited Uses
- **Phishing or Impersonation** — Must not be used for deceptive purposes, impersonation, or any illegal activities
- **Passing Off Others' Designs** — Logos, brand assets, and original copy belong to their owners
- **Violating Terms of Service** — Some websites explicitly prohibit scraping or reproduction; check first

Users bear all legal responsibility arising from the use of this tool.

## Project Structure

```
clone-website/                # This repository (flat layout)
├── SKILL.md                  # Skill definition file (required)
├── README.md                 # Chinese README (default)
├── README.en.md              # English README
├── LICENSE                   # MIT License
└── .gitignore
```

When using the Skill to clone a website, the following directories will be generated in your project (these are clone artifacts, not part of this repository):

```
your-project/
├── docs/
│   ├── research/             # Extraction output and component specs
│   │   ├── BEHAVIORS.md      # Behavior inventory
│   │   ├── PAGE_TOPOLOGY.md  # Page topology
│   │   └── components/       # Component spec files
│   └── design-references/    # Screenshots
├── scripts/                  # Asset download scripts
└── public/                   # Downloaded images, videos, fonts, etc.
```

## Referenced Projects

This Skill was designed with reference to the following open-source projects:

- **[firecrawl/open-lovable](https://github.com/firecrawl/open-lovable)** — An AI-driven React app building example by the Firecrawl team, which inspired the overall approach of "using AI agents to drive website restoration."
- **[JCodesMore/ai-website-cloner-template](https://github.com/JCodesMore/ai-website-cloner-template)** — A Next.js-based website cloning template project. Its five-phase pipeline (reconnaissance, foundation build, component specs, parallel building, assembly & QA) and the design of using component spec files as build contracts were important inspirations for this Skill.

Unlike these two projects, this Skill is **completely tech-stack agnostic** (no React/Next.js lock-in) and **agent-agnostic** (no lock-in to a specific AI coding agent). Developers can freely choose any framework, CSS solution, build tool, and AI coding agent.

## License

[MIT](./LICENSE)
