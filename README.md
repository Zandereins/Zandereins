<div align="center">
  <img src="dev-mascots.svg" alt="Franz Paul — developer mascots" width="420" />

# Franz Paul

**Production AI engineer** · Microsoft 365 / Cloud consulting background · Dresden, Germany

I build deterministic tooling that makes AI agents measurable — quality you can defend with numbers, not vibes. **Available for freelance.**

[![Total stars](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/Zandereins/Zandereins/main/stars.json&logo=github&color=blue)](https://github.com/Zandereins?tab=repositories)
[![schliff score](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/Zandereins/130bb61237b5b9b1536718e6a2296d4a/raw/schliff-score.json)](https://github.com/Zandereins/schliff)
[![schliff on PyPI](https://img.shields.io/pypi/v/schliff?label=PyPI)](https://pypi.org/project/schliff/)
[![Hydra](https://img.shields.io/badge/Hydra-review_council-blue)](https://github.com/Zandereins/hydra)
[![fpaul.dev](https://img.shields.io/badge/fpaul.dev-portfolio-black)](https://fpaul.dev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-connect-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/franz-paul-016938258/)

[Featured](#featured) · [Open source](#open-source) · [Work with me](#work-with-me)

</div>

---

Most AI tooling calls the agent and hopes. I build the layer that makes the agent's output **measurable** — one coherent stack with three jobs: you **score** the instructions before you trust the agent, you **review** its output with more than one mind, and you give it the **context** to be right in the first place. The throughline is **measure first, then fix**.

| Layer | Tool | Its job |
| --- | --- | --- |
| **1 · Score** | **[schliff](https://github.com/Zandereins/schliff)** | Measure the instructions before you run the agent. |
| **2 · Review** | **[hydra](https://github.com/Zandereins/hydra)** | Review the diff with more than one model's read. |
| **3 · Context** | **vault-sync** *(private)* | Keep the agent working from ground truth. |

## Featured

Two shipped, public tools do the heavy lifting; the rest are private systems that show how I work end to end.

| Repo | What it does | Signal |
| --- | --- | --- |
| **[schliff](https://github.com/Zandereins/schliff)** | Deterministic, stdlib-only quality scorer for AI agent instruction files — `SKILL.md`, `CLAUDE.md`, `.cursorrules`, `AGENTS.md`, system prompts | 9 scorers · anti-gaming detection · deterministic patches · 1,347 tests · MIT · on PyPI |
| **[hydra](https://github.com/Zandereins/hydra)** | Multi-perspective review council for Claude Code: advisors analyze, reviewers cross-examine, a chairman synthesizes | 4 advisors (6 in deep mode) · 3 cross-examining reviewers · up to 10 agents · Claude Opus + OpenAI Codex · MIT |
| **vault-sync** *(private)* | Syncs GitHub repos + PyPI metadata into an Obsidian vault as a Context Mirror | CLI + macOS menubar widget (Molty mascot) + Claude Code MCP plugin (4 read-only MCP tools, 4 skills, 2 hooks) · Python ≥3.10 · MIT |
| **project-beat** *(private)* | FastAPI + Next.js 16 freelance-job radar across German boards | Scrapes 4 active boards five times daily · 6-component hybrid matching · Supabase dashboard |
| **mission-control** *(private)* | Next.js 16 command center for an OpenClaw VPS | 23 server-side API endpoints · Kanban board · JSON persistence · Tailscale-only access |
| **[fpaul.dev](https://fpaul.dev)** | Personal developer site — Next.js 16, MDX, Writing section on AI security and agent tooling | Live on Vercel |

## What I build

Deterministic, well-tested tooling for the agentic-coding ecosystem: things that **score and review AI agents** instead of just calling them. The throughline is **measure first, then fix** — anti-gaming detection so a score can't be juiced, deterministic patches that apply ~32% of schliff's fixes mechanically, and spec-first discipline where every claim is checked against the real artifact. Stdlib-first Python, TypeScript where the runtime demands it.

## Open source

A clean merged PR is the receipt I trust most — third-party-validated proof a maintainer accepted the work.

| Project | Contribution | Status |
| --- | --- | --- |
| **[modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers/pull/3733)** | Added a root `CLAUDE.md` covering the full reference-servers monorepo — 7 servers (4 TypeScript, 3 Python) | [PR #3733](https://github.com/modelcontextprotocol/servers/pull/3733), merged by a maintainer, April 2026 |

Same thesis, applied upstream: better context, fewer guesses.

<details>
<summary><strong>Dev environment & stack</strong></summary>

<br>

- **Languages:** Python (stdlib-first, ≥3.10), TypeScript, SQL
- **AI / Agents:** Claude Code, OpenAI Codex, MCP servers, agent instruction-file quality scoring, multi-agent review councils
- **Web:** Next.js 16, React 19, Tailwind CSS, MDX
- **Backend / Data:** FastAPI, Supabase / Postgres, Playwright, multilingual embeddings
- **Infra:** Docker, Tailscale zero-trust networking, Vercel, Hetzner VPS
- **Tooling discipline:** deterministic scorers, anti-gaming detection, heavy test coverage, single-sourced versioning, spec-driven workflows
- **Knowledge base:** Obsidian (PARA), synced to repos via vault-sync

</details>

<details>
<summary><strong>More private systems</strong></summary>

<br>

- **OpenClaw / Vega stack** — self-hosted OpenClaw Gateway on a Hetzner VPS: Docker Compose, a security-hardening overlay, and access locked behind a Tailscale zero-trust network, driving an always-on OpenClaw agent workspace.
- **Mission Control** — private Next.js command center for the OpenClaw VPS: 23 server-side API endpoints, a Kanban board (Open / In Progress / Review / Done), JSON-file persistence (no database), reached only over Tailscale.
- **project-beat** — private Python / FastAPI + Next.js system that scrapes 4 active German freelance job boards (freelance.de, GULP, Freelancermap, Hays — 13 sources configured) five times daily and ranks postings against profiles via a 6-component hybrid matching pipeline on a Supabase dashboard.

</details>

## Why I build this way

Production AI engineer with a consulting background in Microsoft 365 and Microsoft Cloud, based in Dresden, Germany. The enterprise work taught me the thing the AI-hype market keeps forgetting: tooling that can't be measured can't be trusted. So I work spec-first — a spec is the single source of truth, the code follows, and claims get verified against the real artifact — and I build to the same standard I'd ship to a client. That's the whole reason the stack starts with *score*.

## Work with me

**Available for freelance engagements** — AI tooling, agent quality / eval systems, Microsoft 365 / Microsoft Cloud, and full-stack web.

→ **[fpaul.dev](https://fpaul.dev)** · [LinkedIn](https://www.linkedin.com/in/franz-paul-016938258/)
