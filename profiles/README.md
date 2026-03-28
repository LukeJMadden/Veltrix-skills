# Task Profiles

Profiles are scoped configurations for AI agent delegation. Instead of one agent doing everything (and doing it badly), you delegate to specialists with the right tools, context, and personality.

## How Profiles Work

```
User request arrives
  ↓
Classify: what type of task is this?
  ↓
Select profile (auto or explicit)
  ↓
Sub-agent spawns with:
  • Filtered tool list (only what this profile needs)
  • Scoped system prompt (personality + instructions)
  • Filtered lessons (only relevant categories)
  • Appropriate model tier (cheap for simple, expensive for complex)
  ↓
Sub-agent completes task → checkpoint written → destroyed
```

## Available Profiles

### Core

| Profile | Name | Model | Use case |
|---------|------|-------|----------|
| `code` | Developer | Medium (Sonnet) | Write, fix, review code |
| `research` | Researcher | Medium (Sonnet) | Investigate, analyse, summarise |
| `content` | Content & Marketing | Medium (Sonnet) | Write copy, social, newsletters |
| `ops` | Operations | Medium (Sonnet) | Deploy, monitor, fix infrastructure |
| `admin` | Personal Admin | Cheap (Haiku) | Reminders, email, personal tasks |
| `review` | Code Reviewer | Medium (Sonnet) | Review code quality and architecture |

### Business

| Profile | Name | Model | Use case |
|---------|------|-------|----------|
| `finance` | Finance & Accounting | Medium (Sonnet) | Invoicing, reconciliation, forecasting |
| `data` | Data & Analytics | Expensive (Opus) | Dashboards, KPIs, anomaly detection |
| `sales` | Sales & Revenue | Medium (Sonnet) | Pipeline, leads, proposals |
| `customer` | Customer Success | Medium (Sonnet) | Support, health scoring, churn |
| `product` | Product Management | Medium (Sonnet) | Roadmap, prioritisation, release notes |
| `strategy` | Strategy & Intel | Expensive (Opus) | Competitor analysis, positioning |
| `procurement` | Procurement | Cheap (Haiku) | Vendor management, spend analytics |

## Model Tiers

| Tier | When to use | Example models |
|------|-------------|----------------|
| Local (free) | Classification, notes, summaries | Ollama qwen2.5, llama3 |
| Cheap | Structured extraction, simple tasks | Haiku, GPT-4o-mini |
| Medium | Most work — conversations, code, content | Sonnet, GPT-4o |
| Expensive | Complex reasoning, strategy, data analysis | Opus, o3 |

## Auto-Classification

Profiles are auto-selected by keyword matching. Multi-word keywords score higher than single words for specificity.

Example: "review this code" → `review` profile (not `code`, because "review code" is a 2-word match worth 2 points vs "code" at 1 point).

## Why Not Persistent Agents?

Persistent named agents ("Developer Agent", "Marketing Agent") are a prompt engineering trick, not architecture. The LLM is stateless — there's no memory between calls. What matters is:

1. **Context window focus** — a profile with 10KB of finance rules outperforms one with 50KB of everything
2. **Tool scoping** — a finance profile can't accidentally deploy code
3. **Shared learning** — lessons are stored centrally, filtered per profile at query time

The system learns. The profiles are just lenses.

## Customising

Copy `profiles.yaml` into your project and modify:

```yaml
profiles:
  - id: your-profile
    name: Your Profile Name
    description: What it does
    tools:
      - tool_name
      - tool_pattern_*
    model_tier: medium
    lesson_categories:
      - relevant_category
    prompt: "Your system prompt here."
```

See the included `profiles.yaml` for the full 13-profile configuration.
