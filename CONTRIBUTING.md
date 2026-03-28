# Contributing to Veltrix Skills

Thanks for contributing. Here's how to add skills, hooks, or profiles.

## Adding a Skill

1. Create a directory under the appropriate category: `skills/{category}/{skill-name}/`
2. Add a `SKILL.md` with this frontmatter:

```yaml
---
name: your-skill-name
description: One-line description. Include trigger phrases (when to use this skill).
---
```

3. Write clear, actionable instructions. Not theory — patterns the agent can follow.
4. Include examples of good and bad output.
5. Submit a PR.

## Skill Quality Checklist

- [ ] Has frontmatter with name and description
- [ ] Description includes trigger conditions ("Use when...")
- [ ] Instructions are specific and actionable
- [ ] Includes at least one example or template
- [ ] No references to specific APIs or credentials
- [ ] Agent-agnostic — works with any markdown-aware agent

## Adding a Hook

1. Create a markdown file in `hooks/`
2. Document: trigger, timing, condition, action
3. Include the YAML pattern for easy copy-paste
4. Explain why the hook exists (what problem it prevents)

## Adding a Profile

1. Add to `profiles/profiles.yaml`
2. Include: id, name, description, tools, model_tier, lesson_categories, prompt
3. Add classification keywords
4. Update `profiles/README.md` with the new profile

## Style Guide

- British English
- Direct and concise — no filler
- Lead with what to do, not why (put "why" after)
- Use tables for structured information
- Use code blocks for patterns and examples
