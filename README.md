# AI for ALS Research — Training Program

A practical AI training curriculum for **ALS TDI** researchers, scientists, and staff. Adapted from Dr. Ian McCullough's Johns Hopkins AI program and translated into the ALS research context.

## 📚 View the Site

**Live site:** `https://alstdi.github.io/als-ai-training/`

## 🗂 Curriculum

| Module | Topics |
|--------|--------|
| **Module 1: Foundations** | Foundation models, transformers, vector embeddings, LLMs |
| **Module 2: Working with AI** | Fine-tuning, hallucination, LLM vulnerabilities |
| **Module 3: Image & Multimodal AI** | GANs, diffusion models, biomedical imaging |
| **Module 4: Symbolic AI** | Rule-based AI, formal methods, hybrid systems |
| **Module 5: Data & Databases** | Relational calculus, query optimization, chase algorithm, data integration |
| **Module 6a: Claude & Anthropic** | Literature review, grant writing, data analysis prompts |
| **Module 6b: Google Antigravity** | Bioinformatics pipelines, OMOP, CCDA/FHIR extraction |

## 🚀 Local Development

```bash
# Clone the repo
git clone https://github.com/alstdi/als-ai-training.git
cd als-ai-training

# Install dependencies
pip install -r requirements.txt

# Serve locally with live reload
mkdocs serve

# Open http://127.0.0.1:8000
```

## 🏗 Build & Deploy

The site deploys automatically to GitHub Pages on every push to `main` via the GitHub Actions workflow in `.github/workflows/deploy.yml`.

To build manually:
```bash
mkdocs build
```

Output is written to the `site/` directory.

## ⚙️ GitHub Pages Setup

1. Go to your repo **Settings → Pages**
2. Set **Source** to `GitHub Actions`
3. Push to `main` — the workflow handles the rest

## 📝 Contributing

To add or edit content, modify the Markdown files in `docs/`. The navigation structure is defined in `mkdocs.yml`.

```
docs/
├── index.md                    # Home page
├── module-1/
│   ├── foundation-models.md
│   ├── large-language-models.md
│   └── why-llms-appear-smart.md
├── module-2/
│   ├── fine-tuning.md
│   ├── competence-hallucination.md
│   └── vulnerabilities.md
├── module-3/
│   ├── image-generation.md
│   └── autoencoders-diffusion.md
├── module-4/
│   ├── symbolic-ai.md
│   ├── applications.md
│   ├── limitations-hybrid.md
│   └── formal-methods.md
├── module-5/
│   ├── relational-calculus.md
│   ├── calculus-vs-algebra.md
│   ├── query-optimization.md
│   ├── chase-algorithm.md
│   └── data-integration.md
├── module-6/
│   ├── claude-anthropic.md
│   └── antigravity.md
└── assets/
    └── custom.css
```

## ⚠️ Data Privacy

This training program contains no patient data. All example data in prompt templates is fictional or de-identified. See [Module 6 security guidance](docs/module-6/antigravity.md#security-data-governance-checklist) for guidance on using AI tools safely with research data.

---

*Adapted from Dr. Ian McCullough, Johns Hopkins University. ALS TDI, 2025–2026.*
