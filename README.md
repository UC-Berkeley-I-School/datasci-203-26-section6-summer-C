# Lab 2: Socioeconomic Factors and School Test Scores

DATASCI 203 — Description Using Models

## Team

| Name | 
|---|
| Mohammed Abdalla |
| Miriam Luka | 
| Jayant Kumar | 
| Kashif Awan |


## Research Question

Which socioeconomic factors contribute most heavily to district-level state test scores?

**Hypothesis:** Higher median income and % of adults with a bachelor's degree or higher, and
lower unemployment, poverty, SNAP receipt, and % single mothers, are associated with higher
test scores. We expect `baplusavgall` (% bachelor's+) and `povertyavgall` (poverty rate) to have
the largest coefficients.

**Framing:** we're writing as consultants to advise policymakers on which are the biggest drivers of state test scores

## Data

- **Source:** [Stanford Education Data Archive (SEDA) v6.0](https://edopportunity.org/opportunity/data/downloads/#documentation-6)
- **Files:** `seda_geodist_annual_cs_6.0` (district achievement) joined to
  `seda_cov_geodist_annual_6.0` (district covariates) on district ID, filtered to year 2018,
  "all students" aggregate only.
- **Unit of observation:** one U.S. public school district (~13,000 rows before sampling).
- **Y:** `cs_mn_avg_ol` — standardized math/reading test score effect size vs. national average.
- **X candidates:** `lninc50avgall` (log median income), `baplusavgall` (% bachelor's+),
  `povertyavgall` (% poverty), `unempavgall` (unemployment rate), `snapavgall` (% SNAP),
  `single_momavgall` (% single mothers).
- **Open sampling question:** districts in the same state/region aren't independent, so we need
  a sampling plan (e.g., one district per state cluster, or state fixed effects) before we can
  credibly claim i.i.d. — this is a first-order task, not an afterthought.


## Roadmap

Update the dates below once we agree on the actual due date; phases are ordered so each
depends on the one before it.

| Phase | Owner | Deliverable | Status |
|---|---|---|---|
| 1. Data wrangling & split | Mohammed | Cleaned joined dataset; exploration/confirmation split saved to `data/` | ☐ |
| 2. Sampling plan for independence | Kashif | Written justification for how we handle state-level clustering (subsample vs. fixed effects) | ☐ |
| 3. Exploratory analysis | Jayant | Univariate/bivariate plots on exploration set; NA and outlier decisions documented | ☐ |
| 4. Model 1 (simplest credible model) | Miriam? | Single-predictor regression, e.g. `cs_mn_avg_ol ~ povertyavgall` | ☐ |
| 5. Model 2+ (fuller story) | Miriam? | Additional predictors, transformations, interactions on exploration set | ☐ |
| 6. Assumptions check | Kashif | CLM/large-sample assumptions assessed for final spec | ☐ |
| 7. Draft report | Mo (Intro, operation), Kash (data), Jay (viz), model (Miriam) | Intro, data, operationalization, viz, model table (stargazer) | ☐ |
| 8. Swap to confirmation set | All | Re-run final model(s) + all report numbers on `data/confirmation/` | ☐ |
| 9. Appendix | All | Data link, list of specs tried + what we learned, residuals-vs-fitted plot | ☐ |
| 10. Polish & last minute Edits  | Mohammed | 4-page main report + 1-page appendix, proofread, all plots discussed in prose | ☐ |

Assign owners by editing the table above (one person can own multiple phases, but every phase
needs a name so nothing falls through the cracks).

## Grading Rubric Checklist

Self-check against the instructor's 9 criteria before submitting:

- [ ] **Introduction** — makes the case for the topic from sentence one; no part of the RQ feels arbitrary
- [ ] **Data source description** — provenance, collection method, unit of observation, relevant caveats
- [ ] **Data wrangling** — clean pipeline from raw → analysis data, wrangling code separated into scripts/functions, single source of truth
- [ ] **Operationalization** — concepts justified, alternatives discussed, count + reason for any dropped observations
- [ ] **Data visualization** — at least one plot of Y vs. X with final model predictions overlaid; plain-English labels; every plot discussed in prose
- [ ] **Model specification** — transformations justified, ordinal vars not treated as metric, stargazer table, correct SEs
- [ ] **Model assumptions** — CLM assumptions assessed fairly (no overclaiming), consequences of violations discussed
- [ ] **Results & interpretation** — statistical *and* practical significance, magnitude in context, hypothetical data points
- [ ] **Overall professionalism** — report is submission-ready, readable by a fellow student standalone

## Page Limits

- Main report: **4 pages**
- Appendix: **1 page**
- Format: `.Rmd` → `pdf_document`

## Git Workflow

- Branch per person/feature: `wrangling-mohammed`, `eda-miriam`, `model-jayant`, `writeup-kashif`, etc.
- Open a PR into `main` before merging; one other teammate reviews.
- Never commit raw data or knitted `.pdf`/`.html` output — keep those in `.gitignore`.
- Squash-merge to keep history readable.
