# Veltrix Skills

**Business operations skills for AI agents. Run a company, not just write code.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-16-blue)](#skills)
[![Profiles](https://img.shields.io/badge/profiles-13-purple)](#profiles)
[![Hooks](https://img.shields.io/badge/hooks-4-orange)](#hooks)

Most AI skill libraries focus on coding. This one focuses on everything else — finance, sales, customer success, strategy, content, operations. Skills that help you run a business autonomously.

Works with **Claude Code**, **Cursor**, **Codex**, **Windsurf**, **Cline**, and any agent that reads markdown skill files.

---

## Quick Start

```bash
# Clone into your project
git clone https://github.com/LukeJMadden/veltrix-skills.git .veltrix-skills

# Or install specific skills
cp -r veltrix-skills/skills/business/finance ~/.claude/skills/
```

For Claude Code plugin:
```bash
claude plugin add LukeJMadden/veltrix-skills
```

---

## Skills

### Business Operations

| Skill | Description |
|-------|-------------|
| [Finance](skills/business/finance/SKILL.md) | Invoicing, reconciliation, cash flow, forecasting, tax compliance |
| [Sales](skills/business/sales/SKILL.md) | Pipeline management, lead scoring, proposal generation |
| [Customer Success](skills/business/customer-success/SKILL.md) | Support triage, health scoring, churn prediction |
| [Strategy](skills/business/strategy/SKILL.md) | Competitor analysis, market positioning, strategic recommendations |
| [Procurement](skills/business/procurement/SKILL.md) | Vendor evaluation, spend analytics, contract renewals |
| [Product](skills/business/product/SKILL.md) | RICE prioritisation, roadmap tracking, release notes |

### Content & Marketing

| Skill | Description |
|-------|-------------|
| [SEO + AEO + GEO](skills/content/seo-geo/SKILL.md) | Search, answer engine, and generative engine optimisation |
| [Newsletter](skills/content/newsletter/SKILL.md) | Draft, QA, approval, and send pipeline |
| [Social Media](skills/content/social-media/SKILL.md) | Multi-platform content adaptation |
| [Brand Voice](skills/content/brand-voice/SKILL.md) | Brand consistency enforcement |

### Operations

| Skill | Description |
|-------|-------------|
| [Deployment Monitor](skills/operations/deployment-monitor/SKILL.md) | Self-healing deployment checks with auto-retry |
| [Incident Response](skills/operations/incident-response/SKILL.md) | 5-step incident playbook |
| [Cron Health](skills/operations/cron-health/SKILL.md) | Scheduled task monitoring and alerting |

### Frontend

| Skill | Description |
|-------|-------------|
| [Design](skills/frontend/design/SKILL.md) | Production-grade UI with bold aesthetic direction |

---

## Profiles

Profiles are scoped configurations that give agents the right tools, context, and personality for a task. Instead of one agent doing everything, you delegate to specialists.

13 profiles included: `code`, `research`, `content`, `ops`, `admin`, `review`, `finance`, `data`, `sales`, `customer`, `product`, `strategy`, `procurement`

See [profiles/README.md](profiles/README.md) for details.

---

## Hooks

Pre/post actions that run around tool calls. Safety rails, quality checks, and audit trails.

| Hook | Trigger | Action |
|------|---------|--------|
| [Safety Check](hooks/safety-check.md) | Before destructive shell commands | Block |
| [Lint After Write](hooks/lint-after-write.md) | After writing to source files | Run linter |
| [No Phantom Tickets](hooks/no-phantom-tickets.md) | Before creating error-investigation tickets | Block |
| [Restart Safety](hooks/restart-safety.md) | Before server restart | Check cron schedule |

---

## Philosophy

1. **Business-first, not code-first.** Most AI agents are set up to write code. Few are set up to run a company.
2. **Profiles over personas.** Scoped task configurations, not named persistent agents. The system learns, not the agent.
3. **Agent-agnostic.** Plain markdown files. No framework lock-in. Works anywhere.
4. **Hooks are guardrails.** Prevent the AI from creating phantom tickets, deleting production data, or deploying on Fridays.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). PRs welcome for new skills and hook patterns.

---

## License

MIT — see [LICENSE](LICENSE).

Built by [Veltrix Collective](https://veltrixcollective.com). Powered by Vel.
