# Case Studies

*Sanitized accounts of internal operational experience, with explicit limits on what each example proves.*

These stories are drawn from retrospective reviews of Agenion's internal work history. They are intended to explain **why** certain control boundaries matter, not to disclose internal contracts, repositories, source data, or implementation procedures.

**Evidence boundary:** The underlying records are private and are not independently reproducible from this public documentation repository. The cases demonstrate particular events and decisions inside the observed environment. They are not controlled benchmarks or claims of broad external validation.

## Case 1: A current view loses obligations that history still remembers

### The situation

In a long-running research collection, a current working view omitted several unresolved obligations. Those obligations had not been validly closed or superseded. A reader relying on the current view alone could reasonably have reached the wrong conclusion about the project's remaining work.

### What happened

An independent review compared the current representation with preserved accepted history. The missing obligations were reconstructed, a corrective update was reviewed, and the current view was repaired. Previous accepted records remained intact rather than being retroactively rewritten to make the history appear cleaner.

### What this illustrates

**Recoverability and correctness are different properties.** The design made it possible to trace and repair the error, even though it had not prevented the error from occurring.

The case motivates a distinction between authoritative accepted history and current-looking summaries or projections. Such views can be useful without being infallible.

### What it does not prove

It does not establish automatic error detection, guaranteed completeness of current projections, or immunity to similar failures in the future.

## Case 2: Replacing an execution without rewriting the task's past

### The situation

A bounded delegated task did not produce an acceptable completed handoff. Work had to continue, but the original execution's status and evidence still mattered.

### What happened

The work was assigned to a replacement execution while retaining the original task's intent. The earlier execution's incomplete or abandoned status remained part of the record. The new execution could be treated as current without pretending that the first attempt had never existed.

### What this illustrates

**What was requested and what actually ran are different questions.** Preserving that distinction helps later participants understand retries, replacement, and possible late results.

It also supports more reliable post-incident explanations: an old result can remain historically attributable without automatically becoming the active result.

### What it does not prove

It does not establish complete prevention of races, guaranteed worker isolation, or measurable superiority over a rigorous manual runbook describing the same replacement.

## Case 3: Delivery is not approval

### The situation

An execution produced a structurally complete delivery. The output existed in the expected form, but its content or execution conditions did not yet justify acceptance.

A separate later execution produced promising work evidence but did not satisfy all of the conditions needed to treat its submission as valid.

### What happened

The review process kept these cases separate. A complete delivery could require rework; a technically promising result could remain an invalid submission; a corrected later delivery could undergo its own review.

### What this illustrates

A single `done` flag hides too much. It may mean that an output was produced, submitted correctly, substantively reviewed, or accepted for lasting use. Those states are not interchangeable.

The distinction becomes especially important when one controller must manage several workers or recover the state of work it did not personally witness.

### What it does not prove

It does not show that every acceptance boundary is enforced by code, nor that a semantic reviewer cannot make an incorrect decision.

## Case 4: Accepted knowledge continues after the work episode closes

### The situation

A work episode established a reviewed state for a persistent research subject. The episode itself could end, but the accepted knowledge still needed to serve subsequent work.

### What happened

The accepted state remained in the enduring subject's own records. A later, separately initiated episode read and used that state as its baseline instead of depending on the original conversation or redoing the initial work.

### What this illustrates

**Work memory and accepted knowledge have different lifetimes.** A finished project can contribute to longer-lived state without becoming the permanent owner of everything it produced.

This is why Agenion treats persistent accepted-state responsibilities as distinct from a bounded work campaign when that distinction is needed.

### What it does not prove

The evidence is from sampled internal subjects. It does not demonstrate that the same ownership model works equally well for every business, scientific, or operational domain.

## Case 5: Missing verification is not a successful check

### The situation

A consequential state-change workflow required validation evidence. At a critical point, the required automated verification was unavailable or could not be demonstrated as having run successfully.

### What happened

The responsible workflow did not interpret the absence of proof as a passing result. The consequential update remained blocked pending appropriate verification and review.

### What this illustrates

A system can preserve valuable safety boundaries by representing **unknown or not-run** separately from **passed**. This also shows why a human decision, a prepared candidate, and permission to perform a consequential mutation must not be collapsed into one event.

### What it does not prove

It does not establish universal enforcement across Agenion. In some paths, controls remain procedural or depend on a validator being explicitly invoked.

## What these cases collectively support

The strongest bounded conclusion is that Agenion's explicit distinctions have mattered in real internal operational decisions: replacement versus current execution, delivery versus review, enduring accepted state versus temporary work, historical evidence versus derived views, and missing verification versus permission to proceed.

The cases **do not establish** that Agenion is more reliable, cheaper, or faster than disciplined Git plus documented conventions and human review. That question calls for prospective, matched comparisons, ideally involving fresh operators and unrelated workloads.

Agenion's intended direction is to make the useful distinctions easier to operate and cheaper to maintain, without asking a language model to perform deterministic checks or allowing a dashboard to invent authority.

For current claims and proposed future work, see [Capabilities and Evidence](CAPABILITIES.md) and [Roadmap](ROADMAP.md).