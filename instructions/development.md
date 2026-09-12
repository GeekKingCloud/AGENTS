# Development Preferences

Use this file for implementation, debugging, refactoring, tests, repository maintenance, Git work, and development-tool choices.

## Understand Before Editing

- Read the nearest `AGENTS.md` and the relevant `README.md`, `STYLE.md`, `CONTEXT.md`, nested guidance, plans, and test documentation.
- Inspect the actual implementation, recent history, current branch/worktree state, and existing checks. Do not reason only from filenames, summaries, or intended architecture.
- Identify the behavior owner, public contract, local conventions, and narrowest proof of success.
- When the design or API is uncertain, run a bounded spike with a concrete question. Keep throwaway code outside production paths and remove it when the question is answered.

## Implementation Taste

- Make the smallest behavior-owning change that solves the current problem.
- Before broadening a bounded request into longer-term or production-ready work, present narrow and expanded options with the material time, complexity, and maintenance tradeoffs, then get the owner's choice.
- Match local architecture, naming, error handling, dependency choices, and formatting unless changing them is part of the request.
- Preserve released public interfaces and contracts with demonstrated consumers unless a breaking change is requested and its migration cost is understood. Do not assume backward compatibility is a goal merely because an old name or shape exists.
- For unreleased, internal, one-shot, or agent-operated tools without active consumers or persisted state, prefer the clean requested change. Do not add aliases, duplicate fields, migration branches, deprecation periods, or other compatibility shims unless a real compatibility requirement is identified.
- Add a helper, module, class, abstraction, or configuration surface only when it owns a real concept, removes demonstrated repetition, or protects an important boundary.
- Avoid defensive code for impossible states, broad catches that hide failures, compatibility shims with no active consumer, and cleanup unrelated to the requested outcome.
- When the consumer is another capable coding agent, prefer a clear contract, examples, and falsifiable checks over automation that tries to make the agent's decisions for it. Deterministic code should protect bytes, structure, protocol, or another mechanical invariant—not editorial, architectural, or situational judgment.
- Use the supported operating and threat model, not the strongest imaginable adversary. Accept and document low-value edge cases rather than growing a local utility into security or orchestration infrastructure.
- Comment tricky invariants, surprising edge cases, and external constraints. Do not narrate obvious code or preserve stale reasoning.
- Clean up files, branches, scaffolding, flags, and documentation made obsolete by the change; mention unrelated drift instead of silently expanding scope.

## Finish the Implementation

After the requested behavior works and before final verification or commit, review the task diff and directly affected flow for unnecessary scaffolding, speculative flexibility, brittle tests, narration, and residue. For a small change, one deliberate diff review can finish this pass; load the [implementation finish workflow](../workflows/implementation-finish.md) for substantial implementation or concrete residue needing attention. Preserve behavior, trust boundaries, durable coverage, and supported compatibility; this is not permission for a broad refactor.

That workflow owns implementation quality and task-diff residue. Use the full [workspace cleanup workflow](../workflows/workspace-cleanup.md) when the task created substantial or multiple local resources, or when ownership, reversibility, or risk is non-trivial. Retire small, exact, clearly task-owned disposable debris directly without turning cleanup into a separate programme.

## Tests and Verification

When expected behavior is clear, prefer a concrete failing test or reproduction before the fix. Confirm that it fails for the right reason, implement the minimal correction, rerun the focused check, then broaden only when the changed surface warrants it.

Match proof to the changed behavior and preserve repository-required gates. The [verification workflow](../workflows/verification.md) owns focused versus broad check cadence, exact-candidate proof, and evidence invalidation; do not add a second cadence here.

If no formal test harness exists, use the closest real proof: typecheck, lint, build, smoke command, fixture, snapshot inspection, dry-run, or source-backed manual verification. Do not change a test merely to make it pass, and do not contort production behavior around a bad assertion.

Commit durable tests when they protect an observable contract, regression, edge case, security boundary, or workflow expectation that could plausibly break again. Do not promote every temporary probe into permanent test scaffolding.

That workflow also owns proof states, provenance, and final claims.

## Git and Work Location

- Inspect `git status`, branch, worktrees, and relevant history before editing.
- Work in the current checkout for small isolated changes when safe. Prefer a dedicated branch and isolated worktree for substantial work, concurrent work, risky experiments, or when another agent may touch the original checkout.
- Local commits are allowed when they create useful checkpoints or a reviewable unit. Include only intended changes and use the repository's commit convention.
- Always report the exact repository or worktree path, branch, local commits, and remaining uncommitted state. Do not leave completed work hidden in an unnamed worktree.
- Follow the [root authority boundary](../AGENTS.md#local-and-remote-authority) for pushes, pull requests, merges, tags, releases, and deployments. Use the current granted action set; ask only for a useful next step that falls outside it.
- Before any authorized publication, inspect the diff and status, run the relevant checks, and report skipped proof or residual risk honestly.

### Commit and push cadence

Keep each local commit semantically atomic: give it one cohesive purpose, include the implementation and directly required tests, documentation, configuration, migrations, or generated artifacts, and exclude unrelated cleanup. Prefer commits that can be reviewed and reverted without dragging unrelated work with them. Do not manufacture micro-commits or deliberately broken intermediate states to appear atomic; when an ordered stack is clearer or required, make its dependencies explicit and keep the delivered stack coherent. Commit boundaries do not require a push or broad verification run after each commit, and Git reversibility is not a substitute for the owning rollback workflow.

Keep logical commits reviewable without treating every commit as a reason to push. Once the current task explicitly authorizes remote work on the branch, prefer to accumulate related local commits and push them together at a meaningful integration, review, or delivery checkpoint. This avoids repeatedly spending CI or hosted-runner time on intermediate states.

Push the accumulated commits sooner when remote continuity matters: before a foreseeable interruption or handoff, a user-requested stop or task switch, a blocking state, approaching session, context, or usage limits, or another credible risk that the local checkout will become unavailable. Report the exact pushed state and any checks still pending; a safety checkpoint is not a readiness claim. A concrete current collaboration, review, dependency, or backup need may also justify an immediate push. Treat batching as a cost-aware preference, not a prohibition against useful pushes.

Without current remote authorization, commit locally and hand off the exact path, branch, and hashes instead. This cadence never creates publication permission by itself.

## Default Development Loop

A capable coding agent working directly in its native harness is the default. It can inspect, plan, implement, verify, review, and iterate without adding orchestration machinery simply because that machinery exists.

When choosing or comparing AutoDev tools for a demonstrated durable-coordination need, read the [AutoDev reference](autodev.md). It is not a dependency of ordinary implementation.

When software work adds or changes agent-facing project documentation, follow `workflows/repository-guidance.md` rather than inventing a second file taxonomy here.
