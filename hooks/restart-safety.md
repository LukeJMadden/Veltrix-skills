# Restart Safety Hook

**Trigger:** `execute_shell` (before)
**Condition:** Command contains `systemctl restart` or `process.exit`
**Action:** Run cron safety check

Prevents server restarts when cron jobs are running or about to run.

## Pattern

```yaml
- name: restart-safety
  trigger: execute_shell
  timing: before
  condition: "systemctl restart|process.exit"
  action: run
  command: "check-cron-safety --within 5"
```

## Logic

1. Load all cron job schedules
2. For the next N minutes, check if any job is scheduled to fire
3. If yes → output `BLOCK: job_name (in Xmin)` → hook blocks the restart
4. If no → output `OK` → restart proceeds

## Implementation Example

```typescript
function cronRunningOrImminent(withinMinutes: number = 5) {
  const jobs = loadCronJobs();
  const now = new Date();

  for (let m = 0; m <= withinMinutes; m++) {
    const check = new Date(now.getTime() + m * 60_000);
    for (const job of jobs) {
      if (shouldRunAt(job.schedule, check)) {
        return { safe: false, nextJob: `${job.name} (in ${m}min)` };
      }
    }
  }
  return { safe: true };
}
```

This prevents the common failure where a restart kills a 5-minute newsletter generation that was 4 minutes in.
