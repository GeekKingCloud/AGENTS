# Pull Requests

Use this workflow before preparing, opening, updating, marking ready, or handing off a pull request. It owns the durable content and readiness policy; use the configured GitHub publication procedure for mechanics after the remote action is authorized.

## Prepare a reviewable state

- Confirm the repository, intended base, current branch, and exact head revision. Inspect the complete accumulated diff and commit stack against the base rather than describing only the latest commit.
- Read the nearest repository guidance and identify the goal, acceptance criteria, behavior owners, and explicit non-goals.
- Keep commits logically atomic and the delivered stack coherent. Follow [development preferences](../instructions/development.md) for commit and push cadence.
- Run checks appropriate to the claimed readiness state, following the [verification workflow](verification.md). Before a ready-for-review or delivery claim, run the repository-required final gates on the exact proposed state. For an intermediate draft or safety update, report pending proof instead of implying readiness. Distinguish fresh local evidence, same-commit CI, reused evidence, and unverified surfaces.
- Do not push directly to a protected or canonical branch, rewrite shared history, or force-push unless the repository workflow and user explicitly authorize it.

## Describe the pull request

Explain the outcome and why it is needed, not merely which files changed. Include the relevant parts of:

- scope, acceptance criteria, and non-goals;
- implementation summary and important design decisions;
- focused, broad, CI, and manual evidence actually run;
- security, data, migration, compatibility, integration, deployment, or rollback risk;
- screenshots or equivalent evidence for meaningful visual changes;
- blockers, unverified surfaces, follow-up work, and whether the pull request should remain draft.

Do not claim a check passed because it is expected to run in CI. Green generic checks do not replace a required environment, integration, browser, database, or manual proof.

## Review, update, and hand off

Use [pull-request-reviews.md](pull-request-reviews.md) when reviewing the accumulated changes and [review-comments.md](review-comments.md) when assessing feedback. After meaningful changes, refresh any stale summary, risk statement, screenshots, and check evidence before claiming readiness.

Use the [handoff workflow](handoff.md) for restart-safe interrupted work; do not duplicate its state record in the pull-request description unless reviewers need that information.

A request to implement, review, or commit does not authorize a push, pull-request creation or update, reviewer notification, merge, release, or deployment. Follow the [root authority boundary](../AGENTS.md#local-and-remote-authority): perform the currently granted remote actions without renewed permission for each already-authorized step; ask before an ungranted action.
