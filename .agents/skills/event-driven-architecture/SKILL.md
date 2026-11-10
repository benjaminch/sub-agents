---
name: event-driven-architecture
description: Design or review event contracts, delivery guarantees, asynchronous workflows, queues, and recovery.
---

# Event Driven Architecture

Identify the business transition, producer, authoritative state, consumers, ordering scope, retention, and replay requirements. Distinguish committed-fact events from commands.

Trace atomicity between state changes and publication. Consider an outbox or CDC where needed; explain persistence, publication, acknowledgement, and deduplication across crash windows. State delivery semantics per boundary. Exactly-once claims must identify the transaction boundary and treatment of external side effects.

Define event identity, schema evolution, partition keys, privacy and deletion, duplicate and out-of-order handling, bounded retries with jitter, poison messages, and dead-letter ownership. Explain replay without repeating irreversible side effects. For sagas, state compensation limits.

Estimate arrival and service rates, partition skew, backlog growth, and drain time. Draining requires spare service capacity. Define backpressure, lag alerts, and recovery after retention expiry.

Deliver flow or sequence diagrams, a contract example, guarantees, and integration-test scenarios for duplicate delivery, crash after side effect before acknowledgement, schema changes, replay, and consumer outage. Mark broker-specific behavior requiring documentation verification or experiment.

Work from repository evidence. Distinguish measured facts, estimates, and unknowns. State units and workload assumptions in calculations. Finish with findings or decisions, evidence locations, unresolved risks, and validation limits. Architecture work permits documents only; application, infrastructure, and external changes require implementation authorization unless already granted.
