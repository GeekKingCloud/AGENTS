# Pull-Request Reviews

Use this workflow when reviewing a pull request or accumulated change set for defects, requirements gaps, and evidence gaps. Preparing the pull request belongs in [pull-requests.md](pull-requests.md); handling resulting comments belongs in [review-comments.md](review-comments.md).

Treat review as an attempt to disprove the change, not as approval or a substitute for required gates, specialist judgment, or human ownership. Label self-review honestly. Claim independent review only when the reviewer did not make the material changes, following the [sub-agent workflow](subagents.md). A review-only request is read-only.

## Establish the evidence boundary

- Record the repository, base or merge-base revision, and exact head revision, then inspect the complete accumulated diff between them. If a remote pull request exists, refresh its state before the final report and tie CI evidence to the reviewed head.
- Read the stated goal, requirements, acceptance criteria, and repository guidance for the changed paths. Green checks are evidence, not proof of correctness.
- Use the diff for attribution, then inspect only the surrounding owners, producers, consumers, contracts, tests, configuration, or history needed to validate a material concern.
- Gather evidence only from repository sources, isolated local behavior, redacted fixtures or fakes, and already-authorized read-only sources. Review does not grant production, customer-data, provider, message-sending, replay, or shared-system access.
- Report issues the change introduces, worsens, exposes, or makes newly reachable. Do not turn a bounded review into an unrelated legacy audit.

When observable behavior changes or gains a new consumer, trace the material path to its real owner or producer. Confirm reachable inputs, fields, predicates, guards, failure paths, and supported legacy shapes satisfy the new use instead of inferring upstream guarantees from the changed call site.

## Review proportionately

Screen for logic and goal fulfillment first, then deepen the applicable lenses: security and trust boundaries; realistic tests and regression risk; failure behavior and observability; contracts, data, integrations, and compatibility; documentation accuracy; and unnecessary complexity or scope drift. Tests should exercise behavior with inputs real producers can emit or the reviewed trust boundary can accept, not merely line coverage or private implementation structure.

Scale independent lenses and skeptical review with the consequence of a miss. High-impact authorization, money, data integrity, migration, concurrency, destructive, or external-side-effect changes justify deeper separation; small changes do not require ceremonial parallelism.

## Report and re-check

- Anchor each supported finding to precise evidence, the concrete failure or violated rule, affected behavior, impact, evidence strength, and practical fix direction.
- Keep requested-but-missing, partial, and unrequested behavior on a requirements-and-scope axis. Call it a defect only when evidence also establishes a concrete failure and consequence.
- Retain an uncertainty only when evidence supports a plausible failure path with a material consequence; otherwise omit it. Name the cheapest settling check and classify its readiness effect by consequence. A material security, authorization, data-integrity, destructive, or similarly costly risk blocks readiness until settled or explicitly accepted by the authorized owner; lower-impact uncertainty can remain non-blocking. Never make the final claim broader than the evidence.
- Omit unrelated legacy defects, preference-only style notes, unsupported speculation, duplicates, and issues already settled by current deterministic evidence.
- Even when no findings remain, report the reviewed revisions, scope, lenses, evidence inspected, and unverified surfaces. "No findings" means only that no supported issue was found within that boundary.
- After fixes, re-review the affected areas and the final accumulated diff, then confirm the head revision again.

Default to a local report. Do not submit a review, post comments, update a branch, create issues, resolve threads, mark ready, or merge without explicit authorization. Follow the [verification workflow](verification.md) when stating what was actually checked.
