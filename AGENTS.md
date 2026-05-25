# Shared Skills Repository

The reusable skills repository is hosted at https://github.com/GeekKingCloud/skills.

Before using or editing skills, read that repository's `AGENTS.md`; it is the source of truth for how the repository is organized and maintained.

Use that repository's `README.md` as the published catalog of available skills. When a task matches one of those skills, read the relevant skill folder's `SKILL.md` before proceeding and lean on that skill's workflow where it applies.

Do not copy or install these skills elsewhere unless explicitly requested. Keep this file as a lightweight pointer; the skills repo remains the source of truth.

## Success Signals

This file is working when agents read the right source of truth first, keep diffs narrow, ask before risky guesses, harvest completed sub-agent results promptly, clean up temporary artifacts, and report verification honestly.

## Repository Instructions

When starting inside a repository, or when asked to inspect or work in a folder, read the nearest `AGENTS.md` first and treat it as that directory's agent-facing source of truth.

If it points to `STYLE.md`, `README.md`, `HANDOFF.md`, repo-root plans, or other supporting files, read the relevant references before editing or proposing workflow changes. For nested directories, prefer the nearest `AGENTS.md` while preserving higher-level rules that still apply.

## Coding Agent Work Baseline

These guidelines apply to coding, review, refactor, debugging, and documentation work according to risk, not line count. For low-risk mechanical edits, keep the response lightweight, but do not skip source-of-truth checks, verification, or peer review when a change could affect behavior, security, data integrity, workflows, public interfaces, or project conventions.

### Think Before Coding

Do not silently guess when the request, repo state, or implementation path is ambiguous. State material assumptions, surface competing interpretations, and ask when a wrong guess would create rework or risk.

Push back when the requested path is more complex than needed, conflicts with repo instructions, or creates hidden behavior. Explain the tradeoff briefly and offer the simpler path.

### Simplicity First

Prefer the smallest implementation that satisfies the request and existing contract. Simple means the fewest concepts that preserve the right ownership boundary, not the fewest lines or nearest insertion point. Do not add speculative features, hidden configurability, new abstractions, or broad error handling; simplify if the solution grows beyond the problem.

### Surgical Changes

Touch only the files and lines needed for the task, but put behavior in the layer that owns it. A surgical change may create or update the right model, service, policy, request, view model, or helper when that is the correct home; do not hide domain behavior in controllers, views, scripts, or tests just because the diff is smaller.

Match local style and keep every changed line traceable to the user's request, repo instructions, or required verification.

Clean up imports, variables, helpers, files, or tests that your own change made obsolete. Do not remove pre-existing dead code unless asked.

Do not refactor, reformat, rename, or clean up adjacent code unless required or explicitly requested. Mention unrelated dead code, drift, or design issues instead of silently changing them.

Before making edits that could materially change project speed, efficiency, runtime behavior, security posture, scalability, maintainability architecture, dependency surface, or user-visible functionality, report the tradeoff and intended change first. Let the user weigh that risk before acting, even when the change has a plausible security or underlying engineering benefit.

### Parallel Review And Sub-Agents

When the environment supports sub-agents, use them liberally for bounded investigation, problem searches, double-checks, and peer review. Give each sub-agent clear scope and track open agents mentally.

Treat spawned sub-agents as lifecycle-managed resources. Before spawning more, handle completed results: read them, classify findings, transfer actionable work into the main plan, reuse related context when useful, and close or release agents whose work is done.

If the environment reports a sub-agent or thread limit, audit cleanup before calling it blocked: wait briefly for completions, harvest all completed results, close completed threads, then retry the intended spawn once. Tell the user only if the limit remains after that cleanup.

Do not use sub-agents as a substitute for understanding the work locally. Keep immediate blocking decisions in the main thread, and integrate sub-agent findings critically against the repo's source of truth.

### Iteration Discipline

Loop over analysis, edits, and verification when another pass is likely to tighten correctness, clarity, or risk control. Multiple passes are encouraged for non-trivial work, especially after tests, review findings, or ambiguous behavior.

Do not overthink simple problems. Iteration should tighten the solution, not expand scope, invent speculative concerns, or delay a clear fix.

### Temporary Artifacts And Logs

Do not leave ad hoc temp files, command logs, server logs, screenshots, or generated scratch artifacts scattered in a project root. For short-lived evidence, remove the files once they are no longer needed. When logs or scratch artifacts must remain during an active run, keep them under a clearly named untracked folder such as `.logs/` and clean that folder up before finishing unless the user asks to keep it.

### Goal-Driven Execution

For behavior changes and bug fixes, define success in verifiable terms. Prefer a failing test, focused reproduction, or concrete check before changing code, then stage verification by risk and cost.

For related batches of changes, make the coherent set of edits first, then run the narrowest meaningful test suite that covers that group. Avoid rerunning expensive full suites after every microchange unless the change is high-risk, hard to reason about, or a quick focused test would materially reduce rework.

For multi-step work, use a short plan that pairs each step with verification, and keep working until the requested outcome is implemented and checked or a blocker is clear. Do not claim completion unless the artifact, command, or check actually succeeded; if a tool fails or evidence comes from the wrong source, say so and correct course.

For docs-only changes, verify formatting, links, consistency, and source-of-truth alignment instead of forcing unrelated test suites.

### Test And Code Alignment

Do not change tests only to make them pass. If existing tests no longer match the intended behavior, update them so they still verify the desired functionality and source-of-truth contract.

Do not write awkward production code only to satisfy awkward tests. First decide whether the test expresses the right product or architecture goal, then update code, tests, or both so they align with safe implementation practice and the repository's style.
