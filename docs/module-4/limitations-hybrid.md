# Limitations & Hybrid AI

!!! abstract "Module 4 · Lesson 11"
    **Where symbolic AI falls short — and how combining it with machine learning creates the most powerful solutions.**

## Limitations of Symbolic AI

### Rigid and Hard to Scale
Requires explicit manual definition of rules. Works well in stable, predictable environments. With hundreds of thousands of rules, maintenance becomes burdensome.

### Inflexible with New Information
Machine learning adapts and improves with experience. Symbolic AI doesn't — if a new ALS biomarker is discovered, you must manually update the rules.

### Limited with Unstructured Data
Text, images, voice recordings — the richest sources of research data — are difficult to handle with pure symbolic AI. Machine learning typically needs to parse and structure the data first.

---

## The Hybrid Approach

The most powerful AI systems combine both paradigms:

| Use Symbolic AI for… | Use Machine Learning for… |
|----------------------|--------------------------|
| Eligibility rule enforcement | Predicting trial dropout likelihood |
| Protocol compliance checking | Classifying free-text adverse event reports |
| IRB/FDA regulatory rules | Identifying imaging biomarker patterns |
| Audit-ready decision logging | Surfacing relevant literature |
| Supply chain automation | Analyzing wearable sensor data patterns |

!!! tip "Key Takeaway"
    Use symbolic AI for well-defined, repeatable, regulated processes where explainability is required. Use machine learning for pattern recognition, prediction, and unstructured data. **Build hybrid systems for maximum capability and minimum risk.**

---

## Case Study: Disability Benefits Approval

A powerful hybrid approach for insurance/benefits approval:

1. **Symbolic AI** rapidly approves clear-cut qualifying cases → near-instant approval for those who need it most
2. **Ambiguous cases** are elevated to human review
3. **Clear denials** are handled by symbolic rules with full audit trail

This is more palatable to claimants, faster for straightforward cases, and more defensible to auditors than either pure automation or pure human review.

---

[← Applications](applications.md) | [Next: Formal Methods →](formal-methods.md)
