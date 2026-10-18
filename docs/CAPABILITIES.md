# Capabilities and Evidence

## How to read this document

Agenion is an **internal, human-in-the-loop operational prototype** under active development. The status labels below are deliberately conservative. They distinguish a capability exercised in recorded internal work from one that is merely designed, proposed, or expected.

**Evidence categories**

| Label | Meaning |
| --- | --- |
| **Demonstrated internally** | Used in identifiable internal work histories; the public preview does not expose the underlying artifacts. |
| **Implemented with limits** | Working mechanisms exist, but their coverage, enforcement, or operating conditions are incomplete. |
| **Under study / design** | Feasibility, audits, or designs exist; not a claim of completed implementation. |
| **Planned** | A directional future capability, not shipped or approved as a release. |
| **Not established** | Available evidence does not justify the stronger claim. |

This is an evidence summary, not an independently reproduced certification. Most observations originate from one internal project environment, and many detailed audit records remain private.

## Capability matrix

| Capability | Current evidence classification | What the claim does and does not mean |
| --- | --- | --- |
| Durable bounded work coordination | **Demonstrated internally** | Work episodes and their progress survive individual chat sessions. This does not imply unattended scheduling. |
| Replacement and retry history | **Demonstrated internally** | Internal incidents distinguish a task from a later replacement execution, including non-current historical results. This is not proof against every possible race. |
| Separate delivery and content review | **Demonstrated internally** | A structurally delivered result has been rejected for further work. Delivery alone does not imply acceptance. |
| Durable accepted state reused by later work | **Demonstrated internally in sampled cases** | Later independent work has consumed accepted state from earlier episodes. Generality across every kind of owner remains unproven. |
| Recovery from an incorrect current view | **Demonstrated internally in a bounded incident** | Preserved historical evidence supported correction of missing obligations. The failure was not prevented in the first place. |
| Repository-based structural checks | **Implemented with limits** | Validators and supporting scripts cover selected identity, binding, structure, and consistency questions. Invocation and enforcement are not universal. |
| Human-in-the-loop operator workflow | **Demonstrated internally** | Ordinary chat contexts and repository tools support an end-to-end work loop with human transport and consequential approvals. It is not an autonomous service. |
| Generic cross-domain control kernel | **Partially demonstrated** | Several principles recur across research, data work, internal engineering, and content tasks. Broad external transfer has not been established. |
| Automated end-to-end Campaign runtime | **Planned** | v0.6 direction: remove routine mechanical overhead while preserving review and authority boundaries. |
| Campaign/Worker web observability | **Under study / design** | Audits and foundation work exist. A live, generally available dashboard is not claimed. |
| System-wide Owner observability | **Planned** | v0.7 direction; not a delivered current capability. |
| Self-updating, evidence-aware system *Big Picture* | **Exploratory** | Architectural idea for combining generated system views with reviewed interpretation. No shipped implementation is claimed. |

## Where the evidence is strongest

### Execution continuity under replacement

Internal records document cases in which a prior execution was abandoned or superseded and the same underlying work needed a fresh execution. Maintaining separate historical and current execution states helped prevent an older result from being silently treated as the active one.

**Supported claim:** the distinction was used in operational decisions. **Unsupported claim:** a controlled experiment has established that the approach outperforms every disciplined alternative.

### Submission is not acceptance

Recorded work includes a structurally complete submission that did not pass semantic review, as well as a later execution whose output evidence did not satisfy the required submission binding. This is meaningful because a superficial "done" flag would have hidden different failure modes.

**Supported claim:** review and submission were treated as different operational facts. **Unsupported claim:** every future acceptance route is fully machine-enforced.

### Cross-episode accepted information

A later work episode has used a previously reviewed and accepted state as its starting point. This demonstrates that at least some lasting knowledge is not tied to the episode that created it.

**Supported claim:** sampled cross-episode reuse. **Unsupported claim:** all conceivable types of Persistent Owner have been independently validated.

### Recoverable history

A current representation of an ongoing research corpus omitted obligations that had not been validly closed. Historical accepted evidence remained available, allowing a bounded investigation and repair.

**Supported claim:** recovery was possible in the documented incident. **Unsupported claim:** the architecture prevents projections from drifting or guarantees automatic repair.

See [Case Studies](CASE_STUDIES.md) for public-safe narratives.

## What is not claimed

Agenion does **not currently claim**:

- A commercially ready, installable platform or generally available hosted service.
- An autonomous agent scheduler, automatic worker-session spawning, or unattended end-to-end operation.
- A universal preventive sandbox or write isolation for every agent/tool action.
- A single mandatory validator gate that protects every possible state mutation.
- Perfectly fresh dashboards, indexes, or summaries at all times.
- Guaranteed semantic correctness of model-generated conclusions.
- General, independently measured superiority in error rate, cost, speed, or recovery time.
- Fundamental novelty of provenance, workflow review, durable memory, acceptance, or authority controls.
- Extensive independent adoption across organizations or unrelated operating environments.

Some controls are strong in particular workflows; others remain procedural or detect errors after the fact. Descriptions of *designed safeguards* must not be mistaken for claims of universal enforcement.

## Why the strong comparison baseline matters

A fair comparison is not against an unreliable folder of notes. It is against **Git, careful written conventions, a useful runbook, and disciplined human review**.

Internal retrospective analysis suggests that Agenion's explicit controls are most useful when workflows develop nonlinear behavior: retries, late returns, multiple levels of review, evolving accepted state, and risky staged changes. For straightforward tasks, a simpler baseline may work just as well with less overhead.

A causal performance advantage remains **not established**. Future evaluations should measure control errors, fresh-reader recovery, elapsed time, operator effort, and the cost of maintaining the added structure.

## Present operating boundary

- **Current development line:** `v0.5-dev`.
- **Primary operating surface:** chat sessions connected through a human operator and durable Git-backed records.
- **Public availability:** documentation only.
- **Detailed source and execution evidence:** private and not independently auditable from this public repository.
- **Roadmap:** forward-looking; see [ROADMAP.md](ROADMAP.md).

These categories are deliberately revisable as newer, qualified evidence becomes available. Until then, **unknown** is preferable to an unearned **pass**.