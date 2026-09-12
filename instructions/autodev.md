# AutoDev Tool Selection

Use this reference when choosing or comparing AutoDev tools for durable coordination, not for ordinary implementation. The [development preferences](development.md) retain direct capable-agent execution as the default; selecting a tool does not authorize its installation, agents, cost, or external actions.

Escalate to the AutoDev tools only when durable coordination provides demonstrated value:

| Tool | Owns | Does not own |
| --- | --- | --- |
| [`lumber-hack`](https://github.com/GeekKingCloud/lumber-hack) | Turning current/future state into a durable plan, ticket queue, and execution workflow. | The ticket database or implementation itself. |
| [`atoshell`](https://github.com/GeekKingCloud/atoshell) | Ticket state, dependencies, assignments, comments, and status transitions. | Product specifications, planning judgment, or orchestration policy. |
| [`g8ldfish`](https://github.com/GeekKingCloud/g8ldfish) | Parallel execution and verification of already-defined tickets. “Goldfish” may be used conversationally. | Deciding what should be built or decomposing an undefined goal. |

The full pipeline is experimental, not a default dependency. Use it when durable decomposition, parallel ownership, recovery after interruption, auditability, or coordination across many agents outweighs setup and state-management overhead. Otherwise stay in the native harness.

For an authorized evaluation of these tools, compare the same representative task through direct agent execution, a Crucible-governed native run, and the full AutoDev pipeline. Respect the task's model, tool, cost, and side-effect constraints; report a blocked comparison arm rather than silently substituting one. Judge delivery quality, elapsed effort, recovery, coordination clarity, and proof—not novelty or amount of machinery.
