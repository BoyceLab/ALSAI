# The Chase Algorithm

!!! abstract "Module 5 · Lesson 16"
    **Enforcing integrity constraints across complex data ecosystems — the governance engine of relational calculus.**

## What It Does

The chase algorithm enforces **schema mappings** and **integrity constraints** across databases. It rewrites queries to comply with rules — before the query optimizer determines the most efficient execution path.

| Constraint Type | Example |
|-----------------|---------|
| Primary dependency | Every participant record must have a unique ID |
| Functional dependency | Participant ID uniquely determines all participant data |
| Inclusion dependency | Every adverse event must link to a valid enrolled participant |
| Schema mapping | Rules for how data translates between site databases |

## Privacy Policy Enforcement

The chase algorithm can encode privacy rules directly into queries:

- Database A alone: no privacy violation
- Database B alone: no privacy violation  
- **A + B combined: reveals patient identity → query blocked automatically**

This makes multi-site data sharing tractable in national security, healthcare, and clinical research contexts where manual review of every query is impossible.

## Chase vs. Query Optimizer

| | Chase Algorithm | Query Optimizer |
|--|-----------------|-----------------|
| Focus | Integrity constraints & schema mappings | Execution efficiency |
| When active | When constraints/dependencies exist | Every query |
| Analogy | Traffic laws you must follow | GPS finding the fastest legal route |

They work **in sequence**: chase rewrites the query to respect constraints → optimizer selects the most efficient compliant plan.

!!! warning "Ask Your Vendors"
    Any data platform built for ALS TDI should include a chase algorithm. Ask directly: *"What chase algorithm does your solution use?"* If they can't answer, that's a red flag for your data governance strategy.

---

[← Query Optimization](query-optimization.md) | [Next: Data Integration →](data-integration.md)
