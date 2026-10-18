# Roadmap

*A direction for product maturation, not a release schedule or an inventory of shipped features.*

Agenion's current emphasis is shifting from **establishing durable control semantics** toward **making those semantics easier to operate, verify, and understand**.

The roadmap is organized around successive scopes of operational improvement. Features named here are targets for development and qualification. They should not be interpreted as available until explicitly demonstrated and released.

## Current foundation: v0.5-dev

**Theme: Persistent State Authority and Durable Work Runtime**

The present internal prototype has accumulated a working model for bounded work, replaceable execution contexts, layered review, provenance, and accepted state beyond individual work episodes.

That foundation has been exercised, but it also reveals operational friction:

- Some tasks require an operator or controller to carry out repetitive mechanical checks.
- Different roles can encounter more governance material than their immediate action requires.
- Structural enforcement is uneven across workflows.
- Summaries and derived indexes can lag behind native state.
- The existing user experience remains largely chat-native and manually connected.

This is the starting problem, not an assertion that the v0.5 architecture has been frozen or formally released.

## v0.6: Campaign operability

**Intended theme: Efficient, verifiable, end-to-end Campaign operation.**

The priority is to make one bounded Campaign practical to operate from initial objective through delegation, work, review, recovery, and closure, while preserving the authority distinctions already learned from previous incidents.

### A. Task-appropriate guidance

Reduce broad, repetitive document reading by making the applicable obligations discoverable for the role and action at hand: planning, dispatch, execution, submission, review, recovery, or closure.

The design must preserve source traceability. A convenient compact guide cannot silently omit a mandatory rule. When applicability or source freshness cannot be established, the system should report uncertainty rather than inventing clearance.

### B. Mechanical runtime assistance

Move suitable checks from repeated AI reasoning into deterministic tooling. Candidate work includes content/reference verification, structural validation, consistency checks, and source-backed status resolution.

The aim is **less mechanical effort**, not automatic semantic acceptance. AI reviewers and authorized humans remain responsible for contextual judgment and consequential decisions.

### C. Reliable lifecycle operations

Improve the ordinary and exceptional paths of a Campaign, including incomplete submissions, replacement execution, retries, conflicting or stale state, and recovery after interrupted operations.

Qualification should cover safe repeated invocations, unambiguous current-state resolution, and conservative behavior when a required fact cannot be proved. A successful happy path alone is not sufficient.

### D. Campaign and Worker observability

Develop a private, read-oriented operational dashboard showing Campaign purpose, lifecycle, pending review, blockers, and next actions. Worker views should separate **assignment created**, **dispatch recorded**, **receipt acknowledged when observable**, **work activity when observable**, and **submission verified**.

A dashboard must not infer an agent is running merely because work was dispatched. It should show unknown, unavailable, or stale data explicitly and must not become a competing source of authority.

### Proposed exit criteria

A meaningful v0.6 milestone would include:

- A real Campaign completes its full lifecycle with the new support tooling.
- A replacement or retry path can be recovered without erasing earlier evidence.
- Mechanical checks have test coverage and fail conservatively when required evidence is missing.
- The operator handles fewer low-value copy/compare tasks than in a documented baseline.
- Dashboard state remains traceable to underlying sources and correctly distinguishes observed from inferred conditions.
- Semantic review and operator/owner approval remain separate from mechanical success.

These are **proposed acceptance criteria**, not passed tests or a commitment to ship every listed feature under the same release.

## v0.7: System-wide operability

**Intended theme: Extend verified operations and observability beyond Campaigns.**

Once Campaign-level runtime and presentation patterns have been qualified, a further development stage can extend reusable mechanisms to other enduring responsibilities, including Persistent Owners and relevant domain/identity state.

Potential capabilities include source-aware navigation across different object types, visibility into accepted-state maturity and changes, system-level health and unresolved obligations, and a Persistent Owner dashboard.

**The central design constraint:** do not force every object into a single universal workflow. An enduring accepted-state owner, a Campaign, and a reusable knowledge domain may have different authorities, lifecycle rules, and evidence needs. Reuse verification and navigation where appropriate; retain specialized acceptance semantics where required.

### Proposed exit criteria

- Multiple object families can be inspected without inventing a second authority for their state.
- The UI distinguishes accepted state, work in progress, derived projections, and unresolved questions.
- Cross-object navigation records source provenance and freshness.
- An independent reader can recover high-level state and descend to the relevant authoritative source.
- Shared tooling reduces duplication without erasing meaningful differences between owner families.

## Beyond v0.7: An evidence-aware Big Picture

**Exploratory concept: a durable, revisable understanding of Agenion itself.**

Today, a reader seeking to understand Agenion as a whole may need to reconstruct the picture from version records, current owners, governance, work history, audits, and decisions. A future *Big Picture* could make that reconstruction much more efficient.

The candidate design has two complementary responsibilities:

**Generated system picture.** A source-backed, freshness-aware view of what exists, how major responsibilities connect, what has changed, and where uncertainty remains. This would be a *derived view*, not a new source of authority for every underlying fact.

**Reviewed system understanding.** An evolving account of the system's architectural interpretation, significant decisions, known limits, and open questions, updated through explicit evidence and review. It could be owned persistently without taking over the native authority of its component systems.

That distinction helps avoid two failure modes: a beautifully organized overview that silently goes stale, and an all-powerful "meta-owner" whose summary overrules the very sources it is supposed to describe.

### What success would look like

A new controller or authorized reviewer could answer **what Agenion currently is, how it got here, what remains unresolved, and which sources support those conclusions**, without requiring the original developer's active chat history.

The system should also be able to identify when a major change may have invalidated a prior interpretation, prompting targeted reconciliation rather than silently rewriting history.

Big Picture is **not implemented or guaranteed by this roadmap**. Its design should be evidence-led and subject to independent review.

## How progress should be evaluated

The guiding questions are operational, not cosmetic:

1. Does a real workflow become easier to continue or recover?
2. Are critical errors detected or prevented more reliably?
3. Does the system preserve legitimate human and owner authority?
4. Can a new participant understand the next safe action with less effort?
5. Is the benefit worth the complexity and operating cost?

No date or version label should be used as a substitute for those answers.

Related reading: [Capabilities and Evidence](CAPABILITIES.md) · [Design Philosophy](DESIGN_PHILOSOPHY.md).