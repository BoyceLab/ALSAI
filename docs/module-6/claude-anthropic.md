# Claude & Anthropic for ALS Research

!!! abstract "Module 6a — Special Section"
    **A practical guide to integrating Claude into your research workflows — from literature review to grant writing, data analysis, and beyond.**

!!! info "About Claude"
    Claude is an AI assistant developed by **Anthropic**, designed with safety and accuracy as core priorities — making it particularly well-suited for scientific and clinical research contexts where the stakes of AI error are high.

## Why Claude for Research?

| Feature | Why It Matters |
|---------|---------------|
| **Constitutional AI training** | Reduces confident-sounding but incorrect outputs |
| **Long document context** | Process entire research papers, clinical protocols, or grant applications at once |
| **Citation awareness** | Flags uncertainty rather than confabulating; can be prompted to always request sources |
| **Privacy controls** | API deployments can be configured so data is not used for model training |

---

## Use Case 1: Literature Review

Claude can dramatically accelerate systematic literature review — reading, summarizing, and synthesizing large volumes of papers faster than any human team.

### Single Abstract Summarization

```
Please summarize the following research abstract for an ALS researcher audience.
Focus on:
1. The primary research question
2. Key methodology
3. Main findings
4. Limitations
5. Relevance to TDP-43 pathology / SOD1 mutations / [your target]

Cite the paper in APA format. If any claims appear uncertain or 
unsupported by the abstract, flag them explicitly.

[Paste abstract here]
```

### Multi-Paper Synthesis

```
I'm going to provide you with summaries of 8 papers on ALS biomarkers.
After I share all of them, please:
1. Identify areas of consensus across studies
2. Highlight contradictions or conflicting findings
3. Identify the most significant methodological gaps
4. Suggest 3 high-priority future research questions

Please do not respond until I have provided all 8 summaries.
Confirm you understand.
```

!!! warning "Always Verify Citations"
    Ask Claude to cite its sources, then independently verify those citations exist. Claude is far less likely to fabricate when asked to provide references, but **always check before including in any official document.**

---

## Use Case 2: Data Analysis Support

Claude can help interpret statistical outputs, suggest appropriate analyses, and explain complex methods to non-statistician collaborators.

### Interpreting Statistical Results

```
I am an ALS researcher analyzing survival data from a 24-month clinical trial.
Here are my Cox proportional hazards model results:

[Paste output table here]

Please help me:
1. Interpret each hazard ratio in plain English for a non-statistician collaborator
2. Flag any results where assumptions may be violated (proportionality, multicollinearity)
3. Suggest appropriate follow-up analyses for significant findings
4. Draft a 2-paragraph "Statistical Analysis" section for the manuscript Methods
```

### Analysis Code Generation

```
Write Python code using pandas and lifelines to perform a Kaplan-Meier 
survival analysis on an ALS dataset with these columns:
- participant_id (string)
- time_to_event_months (float)
- event_occurred (1=event, 0=censored)
- treatment_arm (string: "treatment", "placebo")

Please:
1. Plot KM curves by treatment arm with 95% CI
2. Run a log-rank test and report the p-value
3. Export the plot as a 300 DPI PNG suitable for publication
4. Include comments explaining each step
```

---

## Use Case 3: Grant Writing

Claude excels at drafting, revising, and improving research grant applications — turning complex scientific content into compelling narrative.

### Specific Aims Page

```
Help me draft a Specific Aims page for an NIH R01 application.

Research gap: [describe the gap]
Hypothesis: [state your central hypothesis]
Aim 1: [describe Aim 1]
Aim 2: [describe Aim 2]
Aim 3: [describe Aim 3]
Innovation: [what's new about this approach]
Impact: [how this advances ALS research/treatment]

Write a compelling 1-page Specific Aims in standard NIH format. 
Use active voice, avoid jargon where possible, and make the clinical 
significance immediately apparent in the opening paragraph.
```

### Reviewer Response Letters

```
I need to draft a response to reviewers for an R01 resubmission.

[Paste reviewer critiques]

For each critique:
1. Acknowledge the reviewer's concern professionally
2. Summarize how we've addressed it in the revised application
3. If we disagree, draft a respectful, evidence-based rebuttal

Keep the tone collegial and confident.
```

---

## Use Case 4: Manuscript Writing & Editing

### Abstract Writing

```
Write a structured abstract (250 words max) for Annals of Neurology:

Background: [2-3 sentences]
Objective: [1 sentence]
Methods: [key design, N, primary outcome]
Results: [key findings with statistics]
Conclusions: [main takeaway and implications]

Use past tense for Methods and Results. Include the primary statistical 
result with confidence interval and p-value.
```

### Plain Language Summary

```
Rewrite the following abstract for a general audience — someone with 
no scientific background who has been diagnosed with ALS.

Goals:
- 8th grade reading level
- Explain what was studied and why it matters for patients
- Avoid all medical jargon, or define it when unavoidable
- End with what this means for future treatment hope
- Keep under 150 words

Abstract: [paste here]
```

---

## Use Case 5: Research Ideation

```
Based on the following recent findings in ALS research, help me 
brainstorm 5 testable hypotheses representing significant scientific gaps:

[Paste 3-5 brief summaries of recent papers]

For each hypothesis provide:
1. The hypothesis statement
2. The biological rationale
3. A proposed experimental approach (in vitro, animal model, or clinical)
4. Key challenges or limitations

Prioritize novel, mechanistically grounded, translationally relevant hypotheses.
```

---

## Best Practices

| Practice | Why |
|----------|-----|
| **Always request citations** | Significantly reduces hallucination |
| **Provide context upfront** | Better output quality |
| **Use iterative refinement** | Start broad, then narrow |
| **Never share PHI** | Use de-identified or synthetic data only |
| **Treat outputs as drafts** | Every output requires expert review |
| **Disclose AI use** | Follow journal and institution policies |

---

## Accessing Claude

| Channel | Best For |
|---------|----------|
| [claude.ai](https://claude.ai) | Individual use, free and paid tiers |
| [Anthropic API](https://console.anthropic.com) | Building research tools and custom applications |
| **Claude for Teams / Enterprise** | Organization-level deployment with privacy controls |
| **Claude Code** | Command-line tool for AI-assisted coding |

!!! tip "Recommendation for ALS TDI"
    For work involving proprietary research data, internal protocols, or sensitive collaboration details, evaluate **Claude for Teams** or an **API deployment** where data is not used for model training. Contact Anthropic at [anthropic.com](https://anthropic.com) for enterprise options.

---

[← Data Integration](../module-5/data-integration.md) | [Next: Google Antigravity →](antigravity.md)
