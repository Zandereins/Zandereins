<div align="center">
  <img src="dev-mascots.svg" alt="Franz Paul — developer mascots" width="420" />

  # Franz Paul

  **Production AI engineer · Microsoft 365 / Cloud consulting background · Dresden, Germany**

  [![schliff on GitHub](https://img.shields.io/github/stars/Zandereins/schliff?label=schliff&logo=github)](https://github.com/Zandereins/schliff)
  [![schliff score](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/Zandereins/130bb61237b5b9b1536718e6a2296d4a/raw/schliff-score.json)](https://github.com/Zandereins/schliff)
  [![schliff on PyPI](https://img.shields.io/pypi/v/schliff?label=PyPI)](https://pypi.org/project/schliff/)
  [![Hydra](https://img.shields.io/badge/Hydra-review_council-blue)](https://github.com/Zandereins/hydra)
  [![fpaul.dev](https://img.shields.io/badge/fpaul.dev-portfolio-black)](https://fpaul.dev)
  [![LinkedIn](https://img.shields.io/badge/LinkedIn-connect-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/franz-paul-016938258/)
</div>

---

I build production AI tooling — agent quality scoring and multi-perspective code review — backed by years of Microsoft 365 and Microsoft Cloud consulting. **Available for freelance work.**

## What I Build

Deterministic, well-tested tooling for the agentic-coding ecosystem: things that score and review AI agents instead of just calling them. Stdlib-first Python, TypeScript where the runtime demands it, and a personal site to tie it together. The throughline is **measure first, then fix** — quality you can defend with numbers, not vibes.

## Currently Building

- **Schliff** — deterministic, stdlib-only quality scorer for AI agent instruction files. Runs 8 scorers (7 form the headline composite; `security` and `runtime` are separate opt-in signals) across five formats: `SKILL.md`, `CLAUDE.md`, `.cursorrules`, `AGENTS.md`, and system prompts. Anti-gaming detection, deterministic patches. MIT, on PyPI.
- **Hydra** — multi-perspective code-review council for Claude Code. 4 advisors review by default, escalating to 6 advisors plus 3 cross-examining reviewers and a chairman in deep mode (up to 10 agents), with cross-model diversity via Claude Opus and OpenAI Codex. Inspired by Karpathy's LLM Council. MIT.
- **vault-sync** — syncs GitHub repos + PyPI metadata into an Obsidian vault as a Context Mirror, across three surfaces: a CLI, a macOS menubar widget (Molty mascot), and a Claude Code MCP plugin shipping 4 read-only MCP tools, 4 skills, and 2 session hooks. Python ≥3.10, MIT.
- **project-beat** — private Python / FastAPI + Next.js system that scrapes 4 active German freelance job boards (freelance.de, GULP, Freelancermap, Hays — 13 sources configured) five times daily and ranks postings against profiles via a 6-component hybrid matching pipeline on a Supabase dashboard.
- **OpenClaw / Vega stack** — self-hosted OpenClaw Gateway running on a Hetzner VPS: Docker Compose, a security-hardening overlay, and access locked behind a Tailscale zero-trust network, driving an always-on OpenClaw agent workspace.
- **Mission Control** — private Next.js command center for the OpenClaw VPS: 23 server-side API endpoints, a Kanban board (Open / In Progress / Review / Done), JSON-file persistence (no database), reached only over Tailscale.

## Open Source

| Project | What it is | Highlights |
| --- | --- | --- |
| **[schliff](https://github.com/Zandereins/schliff)** | Deterministic quality scorer for AI agent instruction files | 8 scorers (7 in the headline composite) · five formats incl. system prompts · anti-gaming detection · ~32% of fixes apply deterministically · 1,231 tests · MIT · on PyPI |
| **[hydra](https://github.com/Zandereins/hydra)** | Multi-perspective review council for Claude Code | 4 advisors by default (6 in deep mode) · 3 cross-examining reviewers · chairman synthesis · up to 10 agents in deep mode · Claude Opus + OpenAI Codex · inspired by Karpathy's LLM Council · MIT |

**Contribution — `modelcontextprotocol/servers`** ([PR #3733](https://github.com/modelcontextprotocol/servers/pull/3733)): added a root `CLAUDE.md` covering the full reference-servers monorepo (7 servers — 4 TypeScript, 3 Python) to the official Model Context Protocol servers repo. Merged by a maintainer, April 2026.

<details>
<summary><strong>Dev Environment & Stack</strong></summary>

<br>

- **Languages:** Python (stdlib-first, ≥3.10), TypeScript, SQL
- **AI / Agents:** Claude Code, OpenAI Codex, MCP servers, agent instruction-file quality scoring, multi-agent review councils
- **Web:** Next.js 16, React 19, Tailwind CSS, MDX
- **Backend / Data:** FastAPI, Supabase / Postgres, Playwright, multilingual embeddings
- **Infra:** Docker, Tailscale zero-trust networking, Vercel, Hetzner VPS
- **Tooling discipline:** deterministic scorers, anti-gaming detection, heavy test coverage, single-sourced versioning, spec-driven workflows
- **Knowledge base:** Obsidian (PARA), synced to repos via vault-sync

</details>

## Featured Repos

| Repo | Description |
| --- | --- |
| [schliff](https://github.com/Zandereins/schliff) | Deterministic, stdlib-only scorer for `SKILL.md`, `CLAUDE.md`, `.cursorrules`, `AGENTS.md`, and system prompts. 8 scorers, anti-gaming detection, deterministic patches, 1,231 tests. MIT, on PyPI. |
| [hydra](https://github.com/Zandereins/hydra) | Multi-perspective review council: 4 advisors by default (6 in deep mode), 3 cross-examining reviewers, chairman synthesis, up to 10 agents. Cross-model via Claude Opus + OpenAI Codex. MIT. |
| **vault-sync** *(private)* | Syncs GitHub repos + PyPI metadata into an Obsidian vault as a Context Mirror. CLI + macOS menubar widget + Claude Code MCP plugin (4 read-only MCP tools, 4 skills, 2 session hooks). Python ≥3.10, MIT. |
| **project-beat** *(private)* | FastAPI + Next.js 16 freelance-job radar. Scrapes 4 active German boards five times daily, ranks postings via a 6-component hybrid pipeline on a Supabase dashboard. |
| **mission-control** *(private)* | Next.js 16 command center for an OpenClaw VPS — 23 server-side API endpoints, Kanban board, JSON persistence, Tailscale-only access. |
| [fpaul.dev](https://fpaul.dev) | Personal developer site — Next.js 16, MDX, with a Writing section on AI security and agent tooling. Live on Vercel. |

## Background

Production AI engineer with a consulting background in Microsoft 365 and Microsoft Cloud. Based in Dresden, Germany. I work spec-first: a spec is the single source of truth, the code follows, and claims get verified against the real artifact. I care about deterministic, defensible tooling — quality you can put a number on.

## Work With Me

Available for freelance engagements — AI tooling, agent quality, M365 / Microsoft Cloud, and full-stack web.

- **Portfolio:** [fpaul.dev](https://fpaul.dev)
- **LinkedIn:** [franz-paul](https://www.linkedin.com/in/franz-paul-016938258/)
