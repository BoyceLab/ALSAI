# Google Antigravity for ALS Research

!!! abstract "Module 6b — Special Section"
    **An AI-native coding environment for bioinformatics pipelines, data workflows, OMOP queries, and clinical note extraction — with autonomous agents that plan, write, and verify code.**

!!! info "What Is Google Antigravity?"
    Announced November 2025, **Google Antigravity** is an agent-first IDE — a VS Code-based development environment where AI agents autonomously plan, execute, and verify complex coding tasks across your editor, terminal, and browser. Free during public preview at [antigravity.google](https://antigravity.google).

## Why Antigravity for ALS Researchers?

Many ALS researchers write Python or R code for survival analysis, biomarker modeling, imaging pipelines, or data cleaning — but aren't professional software engineers. Antigravity's agents handle the mechanical complexity of code while you focus on the science.

| Feature | Benefit |
|---------|---------|
| **Autonomous agents** | Plan, write, run, and debug end-to-end |
| **Parallel workspaces** | Multiple agents on different tasks simultaneously |
| **Artifact review** | Human-readable task plans before any code runs |
| **Model choice** | Gemini 3 Pro (primary), Claude Sonnet 4.5, GPT-OSS |

---

## Getting Started

1. **Download** from [antigravity.google/download](https://antigravity.google/download) (Mac, Windows, Linux). Sign in with a personal Google account.
2. **Open your project folder** — Antigravity indexes your codebase for full project context.
3. **Configure agent review policies:**
    - Set *Artifact Review Policy* → **Asks for Review**
    - Set *Terminal Command* → **Request Review**
    - Enable **Terminal Sandbox** mode
4. **Choose your model** — For complex statistical reasoning and ALS domain nuance, Claude Sonnet 4.5 is a strong choice inside Antigravity.

!!! warning "Security First"
    Agent requests are processed by cloud models — relevant code snippets and context may be sent to Google or partner model providers. **Do not open projects containing PHI, unpublished trial data, or proprietary compound data in Antigravity until your organization has reviewed Google's data handling policies.**

---

## Use Case 1: Survival Analysis Pipeline

```
Build a survival analysis pipeline in Python for an ALS clinical trial dataset.

The CSV file is at /data/als_trial.csv with columns:
- participant_id (string)
- time_to_event_months (float)
- event_occurred (1=event, 0=censored)
- treatment_arm (string: "treatment", "placebo")
- site_id (string)
- alsfrs_r_baseline (float)

Please:
1. Load and validate the data (flag missing values, check for duplicates)
2. Run Kaplan-Meier analysis stratified by treatment arm
3. Perform a log-rank test
4. Fit a Cox proportional hazards model adjusting for baseline ALSFRS-R and site
5. Generate publication-quality plots (300 DPI PNG)
6. Write a summary statistics table to summary_stats.csv
7. Include unit tests for each analysis step

After building, run the tests and show me the verification results 
before I approve.
```

---

## Use Case 2: Multi-Site Data Harmonization

```
I have ALSFRS-R data exports from 12 clinical sites in /data/sites/.
Each CSV has slightly different column naming conventions and some 
use different units for weight.

Build a data harmonization pipeline that:
1. Auto-detects column name variants and maps to a standard schema
2. Flags values outside clinically plausible ranges
3. Standardizes units (convert lbs to kg where detected)
4. Merges all sites into a single harmonized dataframe
5. Outputs a data quality report: row counts per site, % missing per 
   column, flagged anomalies
6. Saves harmonized data to /data/harmonized/als_combined.csv

Write tests that verify the merge preserves row counts and no values 
fall outside plausible ranges in the output.
```

---

## Use Case 3: Biomarker Analysis Dashboard

```
Build a Streamlit dashboard for exploring ALS biomarker longitudinal data.

Data: /data/biomarkers.csv
Columns: participant_id, visit_month, neurofilament_light, 
         phospho_tau, alsfrs_r, treatment_arm

Requirements:
- Sidebar filters: treatment arm, visit month range, participant subset
- Main panel:
  * Line plot of mean NfL over time by treatment arm with 95% CI
  * Scatter plot: NfL vs ALSFRS-R decline with regression line
  * Individual participant trajectory viewer (select by ID)
- Export button: download currently filtered data as CSV

After building, open the app in the browser, take a screenshot of 
each panel, and include those screenshots in your verification artifact 
so I can review the UI before approving.
```

---

## Use Case 4: RNA-seq Differential Expression

```
Set up a differential gene expression analysis pipeline using DESeq2 
(R/Bioconductor) for ALS vs. control iPSC motor neuron RNA-seq data.

Input files in /data/rnaseq/:
- counts_matrix.csv (genes × samples)
- sample_metadata.csv (sample_id, condition: "ALS"/"control", 
  cell_line, passage_number)

Steps:
1. Install required R packages if absent (DESeq2, ggplot2, 
   EnhancedVolcano, clusterProfiler)
2. Run DESeq2 with condition as primary factor, controlling for cell_line
3. Generate: volcano plot, MA plot, PCA plot
4. Extract top 50 DEGs (padj < 0.05, |log2FC| > 1)
5. Run GO enrichment on upregulated and downregulated gene sets
6. Write results to /outputs/deseq2_results.csv and 
   /outputs/go_enrichment.csv

Show me the implementation plan before running anything.
```

---

## Use Case 5: Working with OMOP CDM

The **OMOP Common Data Model (CDM)** is an internationally adopted open standard for observational health data. For ALS researchers, OMOP enables federated multi-site analyses without moving patient-level data.

### Key OMOP Tables for ALS Research

| Table | What It Contains | ALS Use |
|-------|-----------------|---------|
| `person` | Demographics | Cohort demographics, incidence |
| `condition_occurrence` | Diagnoses with dates | ALS diagnosis date, comorbidities |
| `drug_exposure` | Medications prescribed | Riluzole/edaravone use |
| `measurement` | Lab values, clinical scores | NfL, FVC, ALSFRS-R |
| `observation` | Other clinical observations | Symptom onset, milestones |
| `visit_occurrence` | Encounters with dates | Care utilization |
| `procedure_occurrence` | Procedures performed | PEG, tracheostomy, NIV |
| `concept` | Standardized vocabulary | Map codes to concept IDs |

!!! tip "Key ALS Concept IDs"
    - ALS diagnosis (SNOMED): `37016573`
    - Riluzole (RxNorm): `75516`
    - ALSFRS-R total (LOINC): `72101-1`
    - NfL (LOINC): `94085-8`

### 5a: ALS Patient Cohort Definition

```
Build a Python script using SQLAlchemy to extract an ALS patient cohort 
from an OMOP CDM v5.4 PostgreSQL database.

Inclusion criteria:
- ≥2 condition_occurrence records with ALS diagnosis
  (SNOMED concept_id 37016573 or descendants)
- First diagnosis 2015-01-01 to 2023-12-31
- Age at diagnosis 18–80

Exclusion criteria:
- Prior diagnosis of PMA, PLS, or Kennedy disease
- Death within 30 days of first diagnosis (data quality flag)

For each patient return:
- person_id, birth_year, gender, race
- index_date (first ALS diagnosis date)
- age_at_diagnosis
- days_to_first_riluzole (drug_exposure, RxNorm 75516)
- baseline_fvc (measurement ±90 days of index, LOINC 19868-9)
- baseline_alsfrs (observation ±90 days of index)

Output to cohort.csv. Include row counts at each filtering step 
as a data quality audit trail.

Show implementation plan before writing any code.
```

### 5b: Source-to-OMOP ETL

```
Build an ETL pipeline mapping ARC Study export data to OMOP CDM v5.4.

Source: /data/arc_export.csv
Key mappings:
- arc_participant_id → person.person_source_value
- dob → person.birth_datetime
- sex → person.gender_concept_id (map M/F to OMOP concepts)
- als_diagnosis_date → condition_occurrence.condition_start_date
  with condition_concept_id = 37016573
- alsfrs_total_score → measurement table (look up correct LOINC)
- riluzole_start_date → drug_exposure.drug_exposure_start_date
  with drug_concept_id = 75516

Requirements:
1. Validate all concept_ids exist in the concept table
2. Flag records where source values don't map cleanly → etl_errors.csv
3. Generate a mapping report: row counts per target table, % mapped
4. Use INSERT ... ON CONFLICT DO NOTHING (idempotent, safe to re-run)
5. Unit tests that verify referential integrity after load
```

### 5c: Natural Language to OMOP SQL

```
I'm working with an OMOP CDM v5.4 PostgreSQL database. Write SQL 
queries for these research questions. For each: look up relevant 
concept IDs from the concept table, write the query, run a COUNT(*) 
to validate it returns results.

Questions:
1. Median time from ALS diagnosis to first riluzole prescription, 
   stratified by sex and year of diagnosis?

2. Among riluzole-treated ALS patients, what proportion also received 
   edaravone within 2 years of diagnosis?

3. Distribution of FVC at baseline (±90 days of diagnosis) and 
   correlation with survival time?

4. Most frequent comorbidities in ALS patients in the 2 years 
   before ALS diagnosis?

For each query: show the SQL, explain each JOIN in plain English, 
flag assumptions about concept ID selection, note data quality caveats.
```

### 5d: OHDSI Federated Study Package

```
Set up an R-based OHDSI study package for a multi-site ALS 
characterization study using DatabaseConnector, SqlRender, 
and CohortGenerator packages.

The study should:
1. Define an ALS cohort using ATLAS-compatible JSON
   (SNOMED 37016573 + descendants, 2 occurrences required, 
   365-day washout)
2. Generate cohort across a connected OMOP database
3. Run baseline characterization: demographics, comorbidities 
   at index, medications in prior 365 days
4. Output standardized results shareable across sites without 
   sharing patient-level data
5. Include README with instructions for running at a partner site

Use SqlRender so queries work on both PostgreSQL and SQL Server.
Show implementation plan including file structure before writing code.
```

---

## Use Case 6: ALSFRS-R Extraction from C-CDA & FHIR

ALSFRS-R scores are frequently buried in unstructured or semi-structured clinical notes rather than cleanly encoded in structured EHR fields. Extracting them at scale requires a **three-layer pipeline**.

### The Challenge

| Challenge | Description |
|-----------|-------------|
| **Format variability** | Structured LOINC codes, C-CDA narrative, free-text notes, PDF attachments |
| **Linguistic variation** | "ALSFRS-R: 38", "ALS Functional Rating Scale total = 38/48", "functional score 38" |
| **Subscore vs. total** | 12 subscores may be present without a total; or vice versa |
| **Validation** | Values must be plausible (0–48 total, 0–4 per item) and linked to correct visit |

### Three-Layer Strategy

| Layer | Method | When Used |
|-------|--------|-----------|
| **1 — Structured** | FHIR `Observation` with LOINC `72101-1` | First choice: fast, deterministic |
| **2 — Regex** | Parse C-CDA narrative sections with targeted patterns | When structured fields absent |
| **3 — LLM fallback** | Locally-deployed LLM on de-identified free text | When layers 1+2 fail |

### 6a: FHIR Structured Extraction (Layer 1)

```
Build a Python pipeline to extract ALSFRS-R scores from a FHIR R4 
server for a cohort of ALS patients.

Step 1 — Structured Observation query:
Query Observation resources with LOINC codes:
- 72101-1 (ALSFRS-R total)
- 72089-8 through 72100-3 (12 subscores)

For each observation: patient_id, effective_date, score_value, 
score_type (total vs subscore), LOINC code, data_source

Where total absent but all 12 subscores present: compute total, 
flag as "derived"

Step 2 — Quality checks:
- Flag values outside valid ranges (total: 0–48, subscores: 0–4)
- Flag duplicate observations same patient/date
- Flag implausible increases >6 points between visits

Step 3 — Output:
- alsfrs_structured.csv: one row per patient per visit date
- extraction_report.csv: counts by source, % missing, flag rates

Use fhirpy or requests. Show implementation plan first.
```

### 6b: C-CDA Regex Extraction (Layer 2)

```
Build a Python pipeline to extract ALSFRS-R scores from C-CDA XML 
files (/data/ccda/) using lxml and regex.

Step 1 — Parse C-CDA XML:
- Extract metadata: patient_id (from recordTarget), document_date
- Target sections by LOINC:
  * Functional Status Section: 47420-5
  * Assessment and Plan: 51847-2
  * Progress Notes: 11506-3

Step 2 — Regex patterns covering all observed variants:
  r"ALSFRS-R:?\s*(\d{1,2})"
  r"ALS Functional Rating Scale[- ]Revised[^:]*:\s*(\d{1,2})"
  r"ALSFRS[- ]R total[^:]*:\s*(\d{1,2})"
  r"functional score[^:]*:\s*(\d{1,2})\s*/\s*48"
  Plus subscore table patterns (e.g., "Speech: 3", "Swallowing: 4")

Step 3 — Subscore aggregation:
- Sum 12 subscores if total absent; flag as "derived"
- Map subscore label variants to standard item names

Step 4 — Output:
- alsfrs_ccda.csv (same schema as FHIR output for merging)
- Unmatched log: documents where no score was found

Include unit tests with synthetic C-CDA snippets for each regex pattern.
```

### 6c: LLM Fallback for Free-Text Notes (Layer 3)

```
Build a Layer 3 pipeline using a locally-deployed LLM (via Ollama 
running llama3) for free-text notes where layers 1 and 2 found nothing.

Input: /data/unmatched_notes.csv
Columns: patient_id, note_date, note_text (de-identified)

Step 1 — Relevance filtering:
Only send chunks containing: "ALSFRS", "functional", "motor", 
"bulbar", "respiratory", "speech", "swallow", "walk", "climb", 
"write", "breath"

Step 2 — LLM extraction prompt (use exactly):
  "You are a clinical data extractor. Extract ALSFRS-R scores only 
   from the text provided. Return a JSON object with:
   - alsfrs_total: integer 0-48, or null if not found
   - alsfrs_subscores: object with item names and values, or null
   - visit_date: date mentioned near the score, or null
   - confidence: 'high' | 'medium' | 'low'
   - evidence: the exact sentence(s) the score was extracted from
   Do not infer or calculate scores not explicitly stated."

Step 3 — Post-processing:
- Validate JSON (retry 2x on parse failure)
- confidence = 'low' → human review queue, not main dataset

Step 4 — Merge all three layers:
- Priority: Layer 1 > Layer 2 > Layer 3 for same patient/date
- alsfrs_master.csv with source_layer column

Include a human review sample: 50 random Layer 3 extractions 
with evidence text for manual validation.
```

!!! danger "Privacy Requirement"
    Clinical notes almost always contain PHI. All three layers must run on **de-identified data** or on **PHI-approved infrastructure**. Do not process identifiable notes through Antigravity's public preview. Layer 3 LLM extraction should use a locally-deployed model (Ollama, llama.cpp) or Claude via the Anthropic API under a BAA.

### 6d: Write Extracted Scores to OMOP

```
Write extracted ALSFRS-R scores from alsfrs_master.csv to the OMOP 
CDM measurement table (PostgreSQL).

Mapping:
- measurement_concept_id: LOINC 72101-1 (total) → concept_id from concept table
- measurement_date: from visit_date column
- value_as_number: the extracted score
- measurement_source_value: "ALSFRS-R extracted from {source_layer}"
- measurement_type_concept_id: 44818702 (EHR)
- range_low / range_high: 0 / 48 for total; 0 / 4 for subscores

Before inserting:
1. Verify all concept_ids resolve in concept table
2. Check no duplicate (person_id, concept_id, date) exists
3. Layer 3 low-confidence → staging table only, not main measurement

Output load_summary.csv: rows inserted per source_layer, rows 
rejected, rows staged.
```

---

## Iterative Agent Feedback

One of Antigravity's most powerful features: leave inline comments on agent artifacts — like Google Docs — to steer the agent mid-task.

=== "Comment on Plans"
    Before code runs, review the implementation plan and comment: *"Use a mixed-effects model instead of a fixed-effects model here."* The agent revises the plan before executing.

=== "Comment on Screenshots"
    When the browser agent shows a plot, highlight a region and comment: *"The axis labels are too small — increase to 14pt."* The agent updates the code.

=== "Parallel Agents"
    Send one agent to clean data while another drafts analysis code. Review and merge from the Agent Manager dashboard.

=== "Replay Bundles"
    Every session is captured — every file edit, terminal command, and test result. Share with collaborators or re-run from any checkpoint.

---

## Claude vs. Antigravity: Choosing the Right Tool

| Task | Claude | Antigravity |
|------|--------|-------------|
| Summarize a research paper | ✓ | |
| Write a grant Specific Aims | ✓ | |
| Build a survival analysis pipeline | | ✓ |
| Explain a statistical method | ✓ | |
| Debug an R script (quick) | ✓ | |
| Debug a complex pipeline | | ✓ |
| Harmonize multi-site CSV data | | ✓ |
| Draft a manuscript Methods section | ✓ | |
| Build an interactive data dashboard | | ✓ |
| Build an OMOP cohort extraction query | | ✓ |
| Explain what an OMOP concept_id means | ✓ | |
| Build a source-to-OMOP ETL pipeline | | ✓ |
| Translate a research question to OMOP SQL | ✓ (snippet) | ✓ (pipeline) |
| Extract ALSFRS-R from C-CDA/FHIR | | ✓ |
| Explain what LOINC code to use | ✓ | |
| Build a regex + LLM NLP pipeline | | ✓ |
| Run a full RNA-seq pipeline | | ✓ |

!!! tip "Best Practice: Use Both Together"
    Use **Claude** to plan your analytical approach and interpret results in scientific context. Use **Antigravity** to implement and verify the code. Claude's output can directly become an Antigravity task prompt — paste Claude's methodology description as the agent's mission brief.

---

## Security & Data Governance Checklist

- ✅ Set Terminal Command policy to **Request Review** before allowing auto-execution
- ✅ Enable **Terminal Sandbox** mode in Agent settings  
- ✅ Never open folders containing PHI or unpublished trial data in the public preview
- ✅ Review Google's official privacy documentation before using on sensitive projects
- ✅ Use de-identified or synthetic datasets for developing and testing pipelines
- ✅ Treat all agent-generated code as a draft requiring scientific review before publication
- ✅ For Layer 3 LLM extraction: use locally-deployed models or a BAA-covered API

---

[← Claude & Anthropic](claude-anthropic.md) | [↩ Return to Home](../index.md)
