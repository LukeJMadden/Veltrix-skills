# No Phantom Tickets Hook

**Trigger:** `ticket_create` (before)
**Condition:** Title/description contains error-related keywords
**Action:** Block

Prevents agents from creating tickets to investigate their own tool errors. A common failure mode where the AI encounters an error, assumes it's a system bug, and creates a ticket like "Fix missing errors.log" for a file that was never supposed to exist.

## Pattern

```yaml
- name: no-phantom-tickets
  trigger: ticket_create
  timing: before
  condition: "missing|not found|ENOENT|EISDIR|Cannot read|undefined|circuit breaker|Permission denied"
  action: block
  message: "Blocked: Do not create tickets for your own tool errors."
```

## Why This Exists

Without this hook, agents will:
1. Try a tool → it fails (e.g. `read_file` on a nonexistent path)
2. Assume the file should exist → create a ticket to "investigate"
3. "Fix" it by creating the file → now there's a phantom file in the codebase
4. Repeat for every error they encounter

The correct behaviour: if a tool fails, try a different approach or report the blocker on the current ticket.

## Code-Level Guard (additional)

For stronger protection, add a regex guard in the ticket creation function:

```typescript
const phantomPatterns = [
  /missing.*file|file.*missing|not found.*fix/,
  /enoent|eisdir|eacces|eperm|cannot read properties/,
  /circuit breaker|undefined.*reading/,
];
if (phantomPatterns.some(p => p.test(title + goal))) {
  return { error: 'Blocked: ticket for own tool error' };
}
```
