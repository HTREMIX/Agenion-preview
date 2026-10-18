# How Agenion Works

**A practical view of coordinated AI work, durable state, and lasting knowledge.**

Agenion lets people organize substantial work across AI conversations and replaceable worker contexts without making any single conversation the authoritative record of what happened. The current implementation is a **human-in-the-loop, Git-native operational prototype**. The diagrams below explain its operating model, not its internal protocols or a fully automated product.

## 1. A simple idea: keep the work, replace the context

Imagine a research project that needs source collection, independent analysis, review, revisions, and follow-up work over several days or weeks. The conversations doing that work may change. A worker may stop, be retried, or be replaced; a later worker may need findings accepted in an earlier work episode.

Agenion keeps the continuity of that project in durable, inspectable records. A controller can recover the current work situation, delegate bounded tasks, review outcomes, and determine a next action without treating the latest chat message as the final authority.

Three responsibilities are central:

- **Work coordination:** organize what needs to happen and what has already happened.
- **Review and authority:** distinguish delivered work from results that have been reviewed or accepted.
- **Long-lived accepted state:** keep enduring knowledge available when the work episode that produced it has ended.

These responsibilities interact, but they are not interchangeable.

## 2. The product loop: from a goal to a reviewed result

![Conceptual product loop showing a user, controller, worker, and durable repository state](../assets/product-loop.png)

*Figure 1. A simplified view of the current chat-native operating loop. Arrows show logical relationships, not automatic API calls.*

A typical work episode unfolds as follows:

1. **A person sets a goal.** The goal may require research, analysis, implementation, validation, or a combination of these.
2. **A controller organizes the work.** It identifies a bounded task, its scope, and what evidence or output will be useful.
3. **The task is made durable.** The repository holds the relevant work state and task context so that another AI conversation can recover them.
4. **A worker performs the task.** In the present operating model, a human operator relays a compact assignment card to an appropriate worker chat. With suitable repository access, the worker reads its authoritative task context, works within its assigned scope, and records outputs.
5. **The controller retrieves and reviews the result.** The durable report and handoff matter more than a conversational claim of completion. A delivered artifact may still be incomplete, invalid, or require substantive revision.
6. **The work continues, changes direction, or closes.** A reviewed result can inform the next task. A lasting state change, when applicable, follows a separate acceptance boundary.

The key separation is **work submitted ≠ work reviewed ≠ lasting state accepted**. A Campaign can also finish without producing any change to a long-lived knowledge owner.

**Current operating reality:** Agenion does not automatically create and run independent worker chats in the background. The human operator still initiates or transfers work between contexts, and AI-assisted review remains a substantive part of the process.

## 3. One controller, several workers

![Controller delegating bounded work to three replaceable AI workers with shared durable context](../assets/controller-workers.png)

*Figure 2. Multiple workers can contribute to the same bounded effort. The example roles are illustrative, not fixed agent types; parallel execution is possible but is not implied for every task.*

Some projects benefit from dividing the work. One worker might collect evidence, another analyze it independently, and another address findings from a review. A controller coordinates the overall objective and reconciles the contributions.

The workers are **replaceable execution contexts**, not permanent owners of the project's truth. Replacing a worker should not require inventing a new history of the task. Nor should an older, superseded result automatically regain current status just because it arrives later.

The durable records make it possible to distinguish:

- **What task was requested**, even if it is attempted more than once.
- **What happened in a particular execution**, including incomplete or replaced attempts.
- **Which result is relevant to the current work**, rather than merely which result appeared most recently.
- **What still needs review or a decision**, rather than assuming every delivery is final.

The precise checks and recovery procedures differ by situation. This diagram intentionally does not specify the underlying state machine, dispatch protocol, or write-isolation implementation.

## 4. Knowledge can outlive a Campaign

![Persistent Owner retaining accepted state across three separate campaigns](../assets/persistent-owner-campaigns.png)

*Figure 3. Campaigns may propose or contribute changes, while an enduring owner retains accepted state. The upward arrows do **not** mean that a Campaign may directly approve or mutate the owner's authoritative state.*

A **Campaign** is a bounded episode of work: an effort with an objective, progress, evidence, decisions, and an eventual outcome. But the knowledge produced by that episode may need to remain useful long after the Campaign closes.

For such cases, Agenion uses the concept of a **Persistent Owner**: an enduring responsibility for accepted state relating to a continuing subject. It is **not** a second controller, a container for every worker output, or something that every Campaign must have.

Consider a series of research efforts around the same collection of material:

- **Campaign A** establishes evidence and proposes findings.
- **A relevant owner** may accept a resulting update after appropriate review and authorization.
- **Campaign B**, started independently later, can use that accepted state as its baseline and investigate remaining questions.
- **Campaign C** can extend or correct the subject's accepted state through its own work and review.

The Campaigns may end. The accepted subject state remains available to subsequent work, alongside the history needed to understand its evolution.

Crucially, **a Campaign's output does not become accepted knowledge simply because the Campaign was completed**. The authority to accept a durable change belongs at the appropriate boundary, and some tasks do not need any such change.

## 5. What happens when something goes wrong?

The value of persistent work state becomes clearer when progress is not linear.

**A worker disappears.** The controller can preserve the previous attempt as history and arrange a replacement without pretending the earlier attempt never existed.

**An output arrives, but review fails.** The submission can remain recorded while its content is marked as needing more work. The two facts do not have to collapse into one generic "done" flag.

**A summary becomes stale.** A convenient index or dashboard view should not override the underlying authoritative records. A reader may need to recheck its source or treat freshness as unknown.

**A long-lived record needs correction.** Previously accepted evidence and change history can support investigation and repair. They do not guarantee that every incorrect current view is prevented or detected automatically.

Internal Agenion work has encountered bounded examples of these situations. For what was observed, what was merely designed, and what remains unproven, see [Case Studies](CASE_STUDIES.md) and [Capabilities and Evidence](CAPABILITIES.md).

## 6. What the machine checks, and what still requires judgment

Agenion separates questions that can be checked mechanically from questions that require interpretation or approval.

| Mechanically checkable in principle | Requires judgment or authority |
| --- | --- |
| Whether a referenced artifact or revision exists | Whether the result actually answers the research question |
| Whether identifiers and expected references match | Whether evidence warrants a conclusion |
| Whether a submission has the expected structure | Whether an exception or reinterpretation is justified |
| Whether recorded states or derived views disagree | Whether a lasting change should be accepted |

The current prototype has validators for selected structural and consistency checks, **not one universal enforcement path for every action**. Human operators and AI-assisted controllers still perform meaningful work. A declared permission boundary should not be mistaken for a physical sandbox.

The intended direction for **v0.6** is to reduce repetitive mechanical Campaign operations and improve Campaign/Worker observability while preserving human and AI review where interpretation is required. **v0.7** is envisioned to extend that operational discipline beyond Campaigns to more of Agenion, including Persistent Owner views. Both are plans, not shipped capabilities; see the [Roadmap](ROADMAP.md).

## 7. What these diagrams do, and do not, represent

The figures provide a **conceptual product explanation**. They show why work is durable, why execution and acceptance are different, and how accepted knowledge may survive across work episodes. They are not a deployment topology, a complete technical architecture, an API reference, or an implementation blueprint.

In particular, they do **not** imply:

- automatic worker scheduling or unattended execution today;
- universal read/write access for every model or chat interface;
- unrestricted Worker authority to change accepted state;
- perfect correctness, prevention of every stale view, or universal validator coverage;
- a mandatory Persistent Owner update for every Campaign.

**Agenion's current promise is narrower and more concrete:** it provides an internally exercised way to coordinate replaceable AI contexts around durable work and explicit acceptance boundaries, while the next development stages aim to make that approach easier to operate and verify.

---

Further reading: [Design Philosophy](DESIGN_PHILOSOPHY.md) · [Capabilities and Evidence](CAPABILITIES.md) · [Case Studies](CASE_STUDIES.md) · [Roadmap](ROADMAP.md)

This page is part of the public documentation preview. It does not include Agenion's private implementation or operating contracts. See the repository [LICENSE](../LICENSE) for documentation licensing and exclusions.