# Operations and Automation Preferences

Use this file for servers, scripts, scheduled jobs, service checks, deployment glue, local infrastructure, and automation around real systems.

## Establish the Live Boundary

Before running or changing automation, identify the target host/profile/environment, credentials involved, external side effects, rollback path, and expected verification signal. Treat unknown automation as potentially live.

Prefer read-only probes, dry-runs, fake profiles, temporary directories, fixtures, and reversible changes. Ask before privileged, destructive, expensive, credentialed, public, privacy-sensitive, or production-impacting repair.

## Repair Loop

1. Inspect the narrowest useful logs, configuration, implementation, and documentation.
2. Identify root cause rather than guessing from the final error.
3. Apply the smallest reversible fix in the layer that owns the fault.
4. Rerun the failed command and verify the service, job, or deliverable state.
5. Report remaining blockers with the exact next action and authority needed.

## Long-Running Work

Define a stall rule before renders, broad scans, migrations, downloads, or generated helper jobs. If the process exceeds the expected window without new evidence, stop waiting silently: inspect the process and artifacts, decide whether a valid partial result exists, and report its state.

After a failed or stuck run, do a root-cause pass before retrying: what stalled, what evidence would have exposed it sooner, and what timeout, checkpoint, or durable instruction prevents recurrence. Known-slow work with predictable progress is exempt when that expectation is stated.

## Services and Scheduled Work

- Use the environment's process manager for long-running services when available; verify readiness with a health check or direct log signal.
- Clean up temporary servers, watchers, pollers, and jobs when the terminal condition is reached, following the [workspace cleanup workflow](../workflows/workspace-cleanup.md).
- Keep scheduled prompts self-contained; future runs must not depend on hidden chat context.
- Sanitize status and failures. Do not leak tokens, private IDs, raw logs, tracebacks, or unnecessary local paths.
- Do not restart or stop a service from inside the active request path when it could kill the process producing the current response. Use an external control plane or ask the owner.

### Owner-facing failure reports

When adding or changing an automated job, failure handler, or watchdog, make its alerts understandable without opening logs:

- Lead with the task and the specific problem: **“Daily report failure: the notification email could not be sent.”** Do not lead with a service name, error code, or internal component.
- Explain what went wrong and why in plain language. Give the observed cause when known; otherwise say the cause is not yet known. Do not substitute a list of possible failures or present an inference as a diagnosis.
- State the impact separately: what completed, what did not, and what remains unverified. A failed notification is not proof that the underlying task or saved result failed.
- Include a recommended next step only when evidence supports it. Say whether the owner needs to act; do not promise an automatic retry or continued investigation unless it is actually arranged. Warn against rerunning completed work when that could duplicate it.
- Keep raw logs, internal identifiers, paths, and detailed diagnostics available for investigation, not in the default alert. Keep the initial report short and specific rather than filling a template with irrelevant fields.

The failure decision must also be truthful: distinguish work still running, work failed, and a check unable to establish the result. A missing completion record while the producer is legitimately running is not a failure. Verify this distinction and read the actual rendered alert as part of testing the failure path.
