# Agenion

**Durable work. Replaceable agents. Governed state.**

Agenion is a **Git-native control and memory architecture for long-running human–AI work**. It helps work continue across changing AI conversations, models, and execution contexts while keeping evidence, decisions, review outcomes, and accepted state inspectable outside any one agent.

**The premise is simple: work should outlive the agents doing it.**

> **Status:** `v0.5-dev` internal operational prototype. This repository is a **public documentation preview**, not an installable distribution of Agenion. The implementation and internal operating specifications are not published here.

## Why Agenion exists

AI agents can research, write, analyze, and implement substantial tasks. But long-running work introduces problems that a larger context window or a shared folder does not solve by itself:

- A context disappears, and its successor must determine what is actually current.
- An earlier execution returns after a replacement has taken over.
- A result has been delivered but has not passed review.
- A reviewed contribution has not yet been accepted into a durable source of truth.
- A convenient summary appears current even though the underlying state has changed.
- A proposed change is mistaken for an authorized change.

Saving more output is not enough. A system also needs to preserve **what the output means for the work**, what was accepted, who can change it, and what can safely happen next.

Agenion explores that missing layer: **continuity with explicit authority**, rather than memory alone.

## What Agenion enables

**Continuity across replaceable contexts.** A new controller or worker can resume bounded work from durable records rather than relying on an old conversation as the sole source of authority.

**Coordinated work with accountable outcomes.** Work can be delegated, reviewed, retried, or replaced while preserving the distinction between the work requested and the executions that attempted it.

**Review before acceptance.** Producing an artifact, delivering it, reviewing it, and accepting a lasting change are different events. Agenion keeps those responsibilities distinct when the workflow requires it.

**Knowledge that survives individual projects.** A bounded work effort can end while accepted information remains available for later, independent work.

**Traceable change and recovery.** Durable evidence and accepted history can help reconstruct what changed, investigate inconsistencies, and repair an incorrect current view.

**Human authority where it matters.** The current model keeps semantic judgment and consequential approvals with AI-assisted review and authorized people, while deterministic checks handle a bounded set of mechanical questions.

These are **observed or designed capabilities within a developing internal system**, not a claim that every path is fully automated or mechanically enforced. See [Capabilities and Evidence](docs/CAPABILITIES.md).

## The operating model, in brief

Agenion separates two kinds of continuity:

| Work continuity | Accepted-state continuity |
| --- | --- |
| What is being attempted, by whom, and what happens next? | What does an enduring subject currently accept as its state? |
| Can an execution be replaced or reviewed without losing its history? | Can later work reuse accepted results without replaying the earlier conversation? |

In Agenion, a **Campaign** organizes a bounded episode of work. A **Persistent Owner**, when the use case calls for one, maintains an enduring responsibility for accepted state beyond any single Campaign. Not every task needs a Persistent Owner.

This is a conceptual distinction, not a complete specification of the internal architecture. For an illustrated walkthrough, see [How Agenion Works](docs/HOW_IT_WORKS.md). For the principles behind it, see [Design Philosophy](docs/DESIGN_PHILOSOPHY.md).

## How it operates today

The current Agenion is **human-in-the-loop and subscription-first**. A human operator starts and connects AI work sessions. A controller plans, delegates, inspects results, and reconciles work. Workers perform bounded assignments. Durable repository records preserve the continuity and review trail between contexts.

The present user experience is primarily **chat-native**, not a fully autonomous agent service or a finished standalone application. Some structural validators and supporting scripts exist, but enforcement coverage is not universal. Human transport and review still account for meaningful operating effort.

Agenion is intended to cooperate with execution tools and frameworks, not replace all schedulers, sandboxes, workflow engines, or AI models.

## Evidence from real work

Agenion has been exercised in extended research, source organization, identity reconciliation, content production, and its own architectural development. Internal retrospective audits document cases in which:

- Earlier execution history remained distinguishable from a replacement execution.
- A complete submission was correctly kept separate from a failed content review.
- Accepted historical records supported the recovery of obligations missing from a current view.
- Accepted knowledge was used by a later, independently initiated work episode.

Those cases show **bounded operational utility**. They do **not** establish a lower overall error rate, lower cost, autonomous reliability, or superiority over a well-designed Git-and-runbook workflow. The underlying detailed records are private, so these public summaries are not independently reproducible from this repository.

Read the sanitized [Case Studies](docs/CASE_STUDIES.md) and the evidence classification in [Capabilities](docs/CAPABILITIES.md).

## What makes the approach interesting?

The core design question is not simply *how do we remember previous conversations?* It is:

**How can a sequence of replaceable reasoning contexts carry out long-running work without making any one context the final authority over the work's state?**

Agenion's answer is an explicit, durable distinction between execution, evidence, review, authorization, and accepted state. This draws on longstanding ideas from workflow systems, provenance, version control, and governed information management. **No claim of fundamental research novelty or unique invention is made here.**

A useful open question remains: *At what level of workflow complexity do these explicit controls justify their cost relative to disciplined Git, documented procedures, and human review?*

## Development direction

| Stage | Focus | Status |
| --- | --- | --- |
| **v0.5-dev** | Durable work state, accepted-state boundaries, replaceable execution, provenance | Current development line |
| **v0.6** | More efficient end-to-end Campaign operation, role-appropriate guidance, deterministic runtime checks, Campaign/Worker observability | Planned direction; not shipped |
| **v0.7** | Extend operational tooling and observability across Agenion, including Persistent Owners | Planned direction; not shipped |
| **Beyond** | A traceable, refreshable *Big Picture* of Agenion's own structure, state, and evolution | Exploratory concept |

The roadmap is directional, not a release commitment. The distinction between **planned**, **demonstrated**, and **released** is intentional. Read the [Roadmap](docs/ROADMAP.md).

## Availability

**This is a documentation-only public preview.** There is no public installation package, hosted service, API, or supported deployment process associated with this repository. The private development repository, internal governance, execution contracts, validators, and operational records are outside the scope of this publication.

The documents explain the purpose, observed capabilities, design philosophy, limitations, and direction of Agenion. They are not instructions for rebuilding the internal system.

## Documentation

- [How Agenion Works](docs/HOW_IT_WORKS.md): an illustrated tour of the product loop, multiple workers, and accepted state across Campaigns.
- [Design Philosophy](docs/DESIGN_PHILOSOPHY.md): principles, trade-offs, and boundaries.
- [Capabilities and Evidence](docs/CAPABILITIES.md): what has been demonstrated and what remains open.
- [Roadmap](docs/ROADMAP.md): intended development priorities and acceptance criteria.
- [Case Studies](docs/CASE_STUDIES.md): sanitized operational examples and their limitations.

## License and attribution

Original written documentation in this public repository is licensed under **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)** unless an individual item states otherwise. Credit **Agenion / HTREMIX**, link to the source and license, and indicate changes when reusing or adapting the text. See [LICENSE](LICENSE) for scope and exclusions.

This license **does not license unpublished implementation, internal material, or third-party content**. The Agenion name and any separately identified brand assets are not granted trademark rights by this documentation license.

---

**Agents are temporary. Work is not.**