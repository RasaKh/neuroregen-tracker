# NeuroRegen Tracker

**A live surveillance dashboard for clinical trials in stem-cell-based neuroregeneration**

## Abstract

NeuroRegen Tracker queries the [ClinicalTrials.gov API v2](https://clinicaltrials.gov/data-api/api) in real time to build a filterable landscape view of interventional studies at the intersection of neurodegenerative/neurotraumatic conditions (Parkinson's disease, Alzheimer's disease, ALS, spinal cord injury, traumatic brain injury, multiple sclerosis, stroke) and cell-based therapeutics (default keyword: "stem cell"). It is intended as a lightweight, reproducible companion to systematic literature review, allowing rapid, repeatable snapshots of trial phase distribution, recruitment status, and enrollment timing without manual registry searching.

## Motivation

Registry-based trial counts change continuously and are easy to lose track of during a systematic review's writing phase — new registrations, status changes, and terminations happen between search date and submission date. This tool automates the registry-monitoring step so that trial landscape figures can be regenerated on demand rather than manually re-tabulated, and is being used to track the trial landscape for autologous olfactory ensheathing cell (OEC) transplantation in human spinal cord injury.

## Data Source & Methods

- **Source:** ClinicalTrials.gov API v2 (`/studies` endpoint), queried with `query.cond` (condition) and `query.term` (free-text keyword) parameters.
- **Fields extracted:** NCT ID, brief title, overall status, phase, study type, interventions, country, start year.
- **Filtering:** Post-hoc filtering on status (e.g., recruiting, completed, terminated) and phase (Phase 1–4) is applied client-side after retrieval.
- **Limitations:**
  - Registry completeness depends on sponsor compliance with ClinicalTrials.gov reporting requirements; non-US trials are variably represented.
  - Single free-text keyword matching (`query.term`) may miss studies using alternative terminology (e.g., "OEC" vs. "olfactory ensheathing cell" vs. "olfactory mucosa").
  - Phase and country reflect the *first* listed value where multiple are present, which may understate multi-arm or multi-site complexity.
  - This is a snapshot tool, not a validated registry-synthesis method — it does not replace systematic search documentation (e.g., PRISMA search strings) required for a formal review.

## Figures

- **Figure 1.** Phase distribution of matched trials
- **Figure 2.** Recruitment status overview
- **Figure 3.** Trial registration timeline by start year

## Installation & Usage

```bash
pip install -r requirements.txt
jupyter notebook neuroregen-tracker.ipynb
```

Adjust condition, keyword, status, and phase filters via the notebook widgets, then click "Update dashboard." Results export automatically to a timestamped CSV.

Google Colab notebook available. But it can't show the plots due to external javascript load which the browser block. Natural limitation

## Citation

If you use this tool in academic work, please cite this repository. *Rasa Khosrofar M.D. 2026*
