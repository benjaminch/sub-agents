---
name: database-consistency
description: Choose data ownership, transactions, replication, and consistency guarantees for distributed data workflows.
---

# Database Consistency

Start with entities, authoritative owners, access patterns, hot keys, and invariants. Map each invariant to an enforceable constraint or transaction boundary before selecting technology.

Specify isolation and consistency per operation. Distinguish linearizability, serializability, read-your-writes, and eventual convergence. Explain stale reads and conflicts in user-visible terms. Analyze lost updates, write skew, uniqueness, fencing for expiring locks, and retries after uncertain commits.

Compare transaction-local designs with cross-service coordination. Identify replication lag, quorum assumptions, failover data loss, split brain prevention, and partition behavior. Give caches and search indexes explicit freshness and rebuild guarantees.

Estimate storage, index and replication overhead, write amplification, and hotspot limits. Describe online schema changes, throttled backfills, mixed-version compatibility, reconciliation, backup restoration, and rollback limits after data transformation.

Deliver a data ownership map, invariant-to-enforcement table, access-pattern rationale, and concurrency and recovery experiments. Label guarantees verified, assumed, or pending measurement; identify any invariant the design cannot enforce.

Work from repository evidence. Distinguish measured facts, estimates, and unknowns. State units and workload assumptions in calculations. Finish with findings or decisions, evidence locations, unresolved risks, and validation limits. Architecture work permits documents only; application, infrastructure, and external changes require implementation authorization unless already granted.
