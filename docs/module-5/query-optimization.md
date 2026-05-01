# Query Optimization

!!! abstract "Module 5 · Lesson 15"
    **How databases automatically choose the fastest retrieval path — the GPS of data access.**

The query optimizer takes your high-level request and determines the most efficient way to retrieve data from potentially dozens of interconnected tables.

## Decision Process

1. **Parse** — Convert human-readable request to machine-interpretable structure
2. **Generate plans** — Enumerate multiple possible execution paths
3. **Estimate cost** — Sample each plan's likely resource use (table size, indexes, data distribution)
4. **Select optimal plan** — Choose lowest cost (fastest, least memory/CPU)
5. **Execute** — Run the chosen plan and return results

## Example: Flights from Paris to New York

| Plan | Approach | When Best |
|------|----------|-----------|
| A | Full table scan row-by-row | Small tables |
| B | Use index on `source` column | Large tables with index |
| C | Join flights + cities first, then filter | Many distinct cities |

The optimizer samples data statistics and selects Plan B — skipping all non-Paris flights entirely.

!!! tip "For ALS Data Infrastructure"
    As the ARC Data Commons grows, queries that ran in milliseconds can take minutes if execution plans aren't updated. A query optimizer continuously adapts to the current state of the data — ensuring performance doesn't degrade as the research dataset scales.

---

[← Calculus vs. Algebra](calculus-vs-algebra.md) | [Next: Chase Algorithm →](chase-algorithm.md)
