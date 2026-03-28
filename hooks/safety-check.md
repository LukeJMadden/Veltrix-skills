# Safety Check Hook

**Trigger:** `execute_shell` (before)
**Condition:** Matches destructive commands
**Action:** Block

Prevents the agent from running destructive shell commands.

## Pattern

```yaml
- name: safety-check
  trigger: execute_shell
  timing: before
  condition: "rm -rf|rm -r /|drop table|truncate|> /dev|mkfs|dd if="
  action: block
  message: "Blocked: destructive command detected."
```

Catches:
- `rm -rf` (recursive force delete)
- `drop table` / `truncate` (database destruction)
- Writing to `/dev` (device-level damage)
- `mkfs` / `dd` (disk formatting)
