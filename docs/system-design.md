# System design notes

This document will grow with the developer's understanding. It is not a complete architecture specification.

## Decisions already made

- Rovia starts as a modular monolith.
- CSV and XLSX are both part of the first version.
- Imports run as background jobs through a queue.
- The first version uses one workspace and does not need multi-tenancy.
- Shipment events are preserved as history. The current shipment state is derived from them.
- Deterministic rules create exceptions and attach evidence.
- Rules stay separate from file parsing and future connectors.
- The first rules are explicit code, not a generic rule engine.
- Operators make the final decision.
- AI starts only after the deterministic flow is reliable.

## First vertical slice

Start with one synthetic shipment delivered after its expected deadline.

The design must explain:

1. which fields arrive in CSV and XLSX;
2. how the shipment and its events are identified;
3. which records are invalid or duplicates;
4. what the API does before creating an import job;
5. what the worker does and what may be retried;
6. how the timeline and current state are derived;
7. how the late-delivery rule is evaluated;
8. which evidence appears in the exception;
9. which decisions the operator may record;
10. what happens when the same file is imported again.

## Questions for the next design session

- What is the source-file contract?
- Which identity belongs to the source and which identity belongs to Rovia?
- When is an import rejected, partially accepted, or completed?
- Which failures are safe to retry?
- How does idempotency work across the API, queue, worker, and database?
- Which data is original and which data is derived?
- Which state changes need an audit history?
- What must be visible in logs without exposing imported data?

Technology choices should follow these answers. They should not define the problem first.
