# Veltrix Skills

**Ready-made AI skills for Claude Code. Install, customise, use.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-16-blue)](#skills)
[![Profiles](https://img.shields.io/badge/profiles-13-purple)](#profiles)
[![Hooks](https://img.shields.io/badge/hooks-4-orange)](#hooks)
[![Website](https://img.shields.io/badge/Veltrix_Collective-veltrixcollective.com-00CFFF)](https://www.veltrixcollective.com)

A library of AI skills for running a business — not just writing code. Finance, sales, content, operations, customer success, and more. Each skill is a markdown file that tells Claude how to handle a specific type of work.

Works with **Claude Code**, **Cursor**, **Codex**, **Windsurf**, **Cline**, and any agent that reads markdown skill files.

> **Completed the [Veltrix AI Course](https://veltrixcollective.com/course)?** This is your next step. The course teaches you to build skills (Module 11). This repo gives you 16 ready-made ones to install and customise.

---

## Getting started

### Install a single skill

```bash
# Copy a skill into your Claude Code setup
cp -r skills/business/finance/  ~/.claude/skills/finance/
```

### Install all skills

```bash
# Clone the whole library
git clone https://github.com/LukeJMadden/veltrix-skills.git

# Copy everything to your Claude Code skills directory
cp -r veltrix-skills/skills/* ~/.claude/skills/
```

### What is a skill?

A skill is a `SKILL.md` file that gives Claude specific knowledge and instructions for a type of task. When you ask Claude to do something that matches a skill, it loads those instructions automatically.

Think of it like giving a new employee a handbook for their role — except the employee is AI and the handbook is a markdown file.

If you want to learn how to build your own skills from scratch, take the [free AI course](https://veltrixcollective.com/course) — Module 11 covers this step by step.

---

## Skills

### Starter skills

Best for **course graduates (Module 11+)** or anyone comfortable with Claude Code. Simple, single-purpose, immediate value.

| Skill | What it does | Install |
|---|---|---|
| [Social Media](skills/content/social-media/) | Drafts posts for LinkedIn, X, Instagram, Facebook. Platform-specific tone and length. | `cp -r skills/content/social-media/ ~/.claude/skills/` |
| [Brand Voice](skills/content/brand-voice/) | Maintains consistent voice across all content. Configurable tone, vocabulary, style rules. | `cp -r skills/content/brand-voice/ ~/.claude/skills/` |
| [Newsletter](skills/content/newsletter/) | Drafts weekly newsletters from source material. Subject lines, sections, CTAs. | `cp -r skills/content/newsletter/ ~/.claude/skills/` |
| [SEO + AEO + GEO](skills/content/seo-geo/) | Optimises content for search engines and AI answer engines. Schema, meta, citations. | `cp -r skills/content/seo-geo/ ~/.claude/skills/` |

### Business skills

For **operations leads, PMs, consultants, founders**. Each skill handles a business function that AI can assist with.

| Skill | What it does | Install |
|---|---|---|
| [Finance](skills/business/finance/) | Budget tracking, expense analysis, financial summaries, invoice processing. | `cp -r skills/business/finance/ ~/.claude/skills/` |
| [Sales](skills/business/sales/) | Lead research, outreach drafting, CRM updates, pipeline analysis. | `cp -r skills/business/sales/ ~/.claude/skills/` |
| [Customer Success](skills/business/customer-success/) | Ticket triage, response drafting, churn risk identification, feedback analysis. | `cp -r skills/business/customer-success/ ~/.claude/skills/` |
| [Product](skills/business/product/) | Feature prioritisation, roadmap drafting, user story writing, competitor analysis. | `cp -r skills/business/product/ ~/.claude/skills/` |
| [Strategy](skills/business/strategy/) | Market analysis, SWOT, competitive positioning, strategic planning. | `cp -r skills/business/strategy/ ~/.claude/skills/` |
| [Procurement](skills/business/procurement/) | Vendor comparison, RFP drafting, contract review, cost-benefit analysis. | `cp -r skills/business/procurement/ ~/.claude/skills/` |

### Technical skills

For **developers and technical users**. Requires some familiarity with code and infrastructure.

| Skill | What it does | Install |
|---|---|---|
| [Frontend Design](skills/frontend/design/) | UI component generation, responsive layouts, accessibility checks, design system compliance. | `cp -r skills/frontend/design/ ~/.claude/skills/` |
| [Deployment Monitor](skills/operations/deployment-monitor/) | Checks deployment health, verifies endpoints, alerts on failures. | `cp -r skills/operations/deployment-monitor/ ~/.claude/skills/` |
| [Cron Health](skills/operations/cron-health/) | Monitors scheduled jobs, detects failures, suggests fixes. | `cp -r skills/operations/cron-health/ ~/.claude/skills/` |
| [Incident Response](skills/operations/incident-response/) | Error triage, root cause analysis, runbook execution, post-mortem drafting. | `cp -r skills/operations/incident-response/ ~/.claude/skills/` |

---

## Profiles

Profiles are pre-configured sets of skills, model preferences, and tool permissions for different types of work.

13 profiles in `profiles/profiles.yaml`:

| Profile | Focus | Skills loaded |
|---|---|---|
| code | Write, fix, review code | frontend/design |
| research | Deep research, analysis | strategy |
| content | Articles, social, newsletters | brand-voice, newsletter, seo-geo, social-media |
| ops | Deploy, configure, maintain | deployment-monitor, cron-health, incident-response |
| admin | Scheduling, email, coordination | — |
| review | Code review, quality checks | — |
| finance | Budget, billing, costs | finance |
| data | Database, analytics, exports | — |
| sales | Outreach, leads, CRM | sales |
| customer | Support, feedback | customer-success |
| product | Roadmap, features, UX | product |
| strategy | Planning, competitors | strategy |
| procurement | Vendor research, purchasing | procurement |

See `profiles/README.md` for configuration details.

---

## Hooks

Safety and quality hooks that run before/after tool calls:

| Hook | What it does |
|---|---|
| [Safety Check](hooks/safety-check.md) | Blocks dangerous shell commands (rm -rf, force push, etc.) |
| [Lint After Write](hooks/lint-after-write.md) | Runs linter after file writes to catch errors immediately |
| [No Phantom Tickets](hooks/no-phantom-tickets.md) | Prevents AI from creating tickets for its own errors |
| [Restart Safety](hooks/restart-safety.md) | Confirms before restarting services |

---

## Course connection

This repo is designed as the graduation toolkit for the [Veltrix AI Course](https://veltrixcollective.com/course):

| Course module | What you learn | Skills to try after |
|---|---|---|
| Module 3: Prompting | How to write effective prompts | Read any SKILL.md to see prompts in action |
| Module 8: Claude Projects | Custom instructions and context | Brand Voice, Newsletter |
| Module 11: Skills & Workflows | How to build your own skills | Modify any skill, then build your own |
| Module 12: Agentic AI | Autonomous agents | Deployment Monitor, Incident Response, Cron Health |

---

## Build your own

Every skill is a markdown file. To create your own:

1. Create a folder: `~/.claude/skills/my-skill/`
2. Add a `SKILL.md` file with:
   - What the skill does (one paragraph)
   - When to use it (triggers)
   - How to do it (step-by-step instructions)
   - What NOT to do (constraints)
   - Example output
3. Claude Code auto-discovers it on next run

Module 11 of the [AI course](https://veltrixcollective.com/course) walks through this in detail.

---

## Stay connected

- [The AI Briefing](https://veltrixcollective.com/subscribe) — free weekly AI newsletter
- [AI Course](https://veltrixcollective.com/course) — 14 hands-on modules, free forever
- [AI Tool Rankings](https://veltrixcollective.com/tools) — 200+ tools ranked
- [Website Audit](https://veltrixcollective.com/websiteaudit) — $99 full-site analysis

Built by [Luke Madden](https://linkedin.com/in/lukejmadden) and [Veltrix Collective](https://veltrixcollective.com).
