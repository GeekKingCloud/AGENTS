# Workspace Cleanup

Use this full workflow before pausing or finishing when a task created substantial or multiple scratch files, logs, temporary tests or output, processes, servers, watchers, worktrees, containers, networks, caches, downloads, renders, or other local resources, or when ownership, reversibility, or cleanup risk is non-trivial. Retire a small, exact, clearly task-owned disposable directly with a proportionate safety check. This workflow owns non-trivial resource retirement across development, operations, computer use, research, and assistant work. A cleanup request is not blanket deletion authority and does not authorize remote artifact, cache, branch, run, or service mutation.

## Design for retirement

- Keep disposable files in one task-scoped scratch location or a known tool-owned reproducible-output path, outside durable source and documentation when practical.
- Record created resources by exact path or identifier, purpose, owner, terminal condition, and cleanup mechanism.
- Prefer a tool's native lifecycle and automatic retirement only when the scope is task-owned and cannot affect shared or valuable state.
- Avoid scattering logs, helpers, downloads, renders, test output, and proof artifacts across repositories or filesystems.

## Inventory and classify

Before mutation, inventory every proposed target. Resolve exact paths and identifiers, then establish who created it, which task owns it, whether anything still consumes it, whether it contains the only copy of work or evidence, and how removal will be verified.

- **Retain:** deliverables, durable tests, source files, user or pre-existing state, shared resources, active handoffs, unresolved failure evidence, valuable or uncertain uncommitted work, dirty worktrees, unique or unpublished commits, and uncertain ownership.
- **Retire:** reproducible task-owned scratch, temporary helpers, local logs, downloads, renders, test/build residue, and processes or containers whose terminal condition has been reached after useful evidence is summarized.
- **Escalate:** broad or recursive targets, paths outside the declared scratch or known tool-owned reproducible-output boundary, unknown or shared resources, hard-to-reverse state, expensive caches, worktrees or branches with unique state, Docker volumes, and cleanup requiring force.

Labels such as temporary, unused, old, stopped, generated, ignored, or cached do not prove removal is safe.

## Review risky cleanup

Exact task-created scratch, individually inventoried reproducible output, and processes may be retired directly when ownership, containment, consumers, terminal state, and reproducibility are clear. Before escalated cleanup, write the proposed target list, retained state, recovery or reproducibility assessment, exact action, and post-cleanup checks. Have an independent read-only reviewer verify ownership, boundaries, active consumers, unique state, reversibility, and the survival plan for the executing agent.

Independent review does not authorize deletion. If the required reviewer is unavailable or any target remains ambiguous, leave it in place, report its exact location or identifier, and ask the owner. Never self-review a risky cleanup plan and proceed as though independence was achieved.

## Protect state and use native lifecycles

- Never remove the active checkout or worktree, its checked-out branch, the process or shell producing the current run, or the control plane needed to report the result. Retire them later from a separate surviving worktree or external control plane after state is preserved.
- Never remove valuable or uncertain uncommitted work, unique commits, active handoff material, unresolved diagnostic evidence, or another user or agent's resources merely to look clean. Individually inventoried disposable residue may be removed after classification; never select it through broad repository or directory cleanup.
- Use Git's worktree inventory and removal lifecycle rather than raw directory deletion. Confirm clean status, account for untracked and ignored files, preserve reachable commits, respect locks, and decide worktree and branch retirement separately. Do not force removal past a failed safety check.
- Identify processes by exact PID, command, working directory, ports, creator, and active consumers; request graceful shutdown before termination. Do not kill by broad name or wildcard.
- Target exact task-owned Docker or Compose resources. Treat images and build cache as a rebuild-cost decision and volumes as stateful destructive targets requiring explicit target confirmation and risky-cleanup review. Never use daemon-wide prune as routine hygiene or stop an unrelated or shared service.
- Do not use broad filesystem deletion, generic repository clean commands, wildcard resource selection, or force flags as routine cleanup. If an exact resolved target cannot be proven to remain inside the approved boundary, stop.
- Deleting remote logs, artifacts, caches, branches, runs, or service state requires separate remote authorization.

## Execute and verify

1. Preserve or summarize evidence and handoff state that must survive.
2. Reconfirm the exact target immediately before mutation, then use the narrowest tool-native removal or graceful shutdown.
3. Re-inventory afterward: prove intended targets are gone and retained paths, commits, worktrees, processes, containers, volumes, and required services remain accessible.
4. Recheck relevant repository or task state. Run only checks whose environment or evidence the cleanup could have affected; cleanup is not a reason for an unrelated full suite.
5. Report what was removed, what was retained and why, what could not be verified, and any remaining resource cost or owner action.

Cleanup is complete only when task-owned residue is gone, protected state is usable, the executing agent can still report, and the final handoff names every intentionally retained resource.
