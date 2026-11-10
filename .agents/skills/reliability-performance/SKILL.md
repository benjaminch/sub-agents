---
name: reliability-performance
description: Analyze SLOs, distributed failure modes, capacity, tail latency, resilience, and recovery readiness.
---

# Reliability Performance

Define user-facing SLIs, SLO windows, dependency boundaries, workload, RTO, and RPO. Calculate allowed bad events or downtime using the chosen denominator; request availability and time-based uptime differ. Separate targets from observed results.

Trace critical-path latency, fan-out, queues, connection limits, dependency tails, and saturation. Adding component percentiles does not yield an end-to-end percentile. State required tracing and load measurements. Include units, utilization, burst duration, and headroom in capacity estimates.

Analyze outages, partitions, slow responses, overload, process or zone loss, stale state, and operator mistakes, including correlated failures and recovery overload. Record detection, blast radius, degradation, recovery, data consequences, and validation for each relevant failure.

Evaluate deadlines, retry budgets and jitter, idempotency, load shedding, backpressure, circuit breakers, and isolation against specific failures. Quantify retry amplification. Define actionable alerts, runbook ownership, rollback triggers, and restore drills with measurable success criteria.

Deliver prioritized risks, calculations, a failure matrix using docs/architecture/templates/FAILURE-MATRIX.md when available, and a workload and fault-injection plan. Run load tests or fault injection only with authorization for that environment.

Work from repository evidence. Distinguish measured facts, estimates, and unknowns. State units and workload assumptions in calculations. Finish with findings or decisions, evidence locations, unresolved risks, and validation limits. Architecture work permits documents only; application, infrastructure, and external changes require implementation authorization unless already granted.
