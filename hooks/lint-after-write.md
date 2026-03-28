# Lint After Write Hook

**Trigger:** `write_file` (after)
**Condition:** File path contains `src/`
**Action:** Run linter

Automatically checks code quality after any file write to the source directory.

## Pattern

```yaml
# TypeScript
- name: lint-after-write
  trigger: write_file
  timing: after
  condition_arg: "path:src/"
  action: run
  command: "npx tsc --noEmit 2>&1 | head -5"

# Python
- name: python-check
  trigger: write_file
  timing: after
  condition_arg: "path:automations/"
  action: run
  command: "python3 -c \"import py_compile; py_compile.compile('${path}')\" 2>&1"
```

Catches:
- TypeScript type errors immediately after writing
- Python syntax errors before they hit production
