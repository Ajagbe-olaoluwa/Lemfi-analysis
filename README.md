# LemFi Customer Friction Intelligence

## Overview

This project analyses **5,000 public Google Play reviews** for LemFi to identify where customer friction appears to be concentrated, how those issues changed over time, and which issues may deserve greater product attention.

The goal was not to build another review dashboard. The project was designed around a more practical question:

> **Which customer pain points are most prominent, which are becoming more important, and what should a product or risk team investigate next?**

---

## Business Question

App-store ratings can show whether customers are satisfied, but they do not explain:

- what customers are struggling with;
- which issues are growing;
- which complaints are most severe;
- or which areas may warrant product intervention.

This project therefore focuses on **customer-friction detection and prioritisation** rather than simple sentiment reporting.

---

## Dataset

- **Source:** Public Google Play reviews
- **Reviews collected:** 5,000
- **Observation period:** May 2025 to October 2026
- **Key fields:** review text, rating, date, thumbs-up count, app version, developer response
- **Friction subset:** reviews rated 1–3 stars

### Data-quality observation

A major change in review composition appeared around February 2026:

- review volume increased sharply;
- 5-star reviews became much more common;
- median review length fell;
- short and repeated positive phrases became more frequent.

Because of this, changes in average rating were **not treated as direct evidence of product improvement**.

---

## Analytical Workflow

The project followed this workflow:

1. **Data collection**
2. **Data cleaning and quality checks**
3. **Exploratory analysis**
4. **Semantic text embeddings**
5. **Customer-friction clustering**
6. **Trend analysis**
7. **Fraud/security deep dive**
8. **Issue-priority scoring**
9. **Business recommendations**

---

## Tools & Methods

- Python
- pandas
- matplotlib
- Sentence Transformers
- UMAP
- HDBSCAN
- K-Means
- cosine similarity
- manual validation of low-confidence fraud classifications

---

## Customer-Friction Themes

The analysis produced eight broad issue categories:

1. Fraud / scam / security concerns
2. App usability & technical problems
3. Transfer/payment failures & reliability
4. Transfer delays, reversals & pending transactions
5. Account access, verification & feature issues
6. Customer support & account/service issues
7. Country availability / geographic restrictions
8. General dissatisfaction / miscellaneous

---

## Key Trend

Comparing **April–June 2026** with **July–September 2026**:

| Issue | Apr–Jun | Jul–Sep | Change |
|---|---:|---:|---:|
| Fraud / scam / security | 10.1% | 17.1% | **+7.0 pp** |
| App usability / technical | 15.4% | 19.4% | **+4.1 pp** |
| Transfer/payment reliability | 13.2% | 15.3% | **+2.1 pp** |
| Country availability | 8.3% | 8.2% | -0.1 pp |
| Customer support / service | 10.5% | 9.4% | -1.1 pp |
| Account access / verification | 14.9% | 11.8% | -3.1 pp |
| General dissatisfaction | 9.2% | 5.9% | -3.3 pp |
| Transfer delays / pending | 18.4% | 12.9% | -5.5 pp |

The strongest emerging issue in the working analysis was **fraud / scam / security concerns**.

---

## Fraud / Security Deep Dive

A closer review of recent fraud/security-related comments revealed a recurring pattern in which reviewers described **third parties allegedly impersonating legitimate organisations or customer-service representatives and directing them toward LemFi**.

Examples referenced:

- refund scams;
- fake delivery/customer-service calls;
- airline compensation claims;
- retailer impersonation;
- parcel-related refund scenarios.

This finding should **not** be interpreted as evidence that LemFi itself is committing fraud. It reflects how reviewers described third-party activity involving or referencing the platform.

---

## Issue Priority Score

To move beyond simple complaint counts, I created a decision-support heuristic based on:

- **40% recent prevalence**
- **35% positive growth**
- **25% review severity**

### Result

| Issue | Priority Score |
|---|---:|
| Fraud / scam / security concerns | **93.0** |
| App usability & technical problems | **78.6** |
| Transfer/payment failures & reliability | **49.7** |
| Transfer delays / pending transactions | 35.6 |
| Country availability / geographic restrictions | 19.6 |
| Account access / verification & feature issues | 17.4 |
| Customer support / account/service issues | 15.8 |
| General dissatisfaction / miscellaneous | 13.4 |

The score is a **heuristic**, not an official LemFi metric.

---

## Business Recommendations

### 1. Strengthen scam-prevention friction

Introduce clearer pre-transfer warnings for users who may have been contacted by someone claiming to represent a:

- retailer;
- airline;
- delivery company;
- or customer-service team.

### 2. Improve fraud reporting and dispute access

Make it easier for users to:

- report suspected scams;
- understand whether payments can be cancelled;
- access dispute or recovery guidance;
- escalate urgent cases.

### 3. Investigate growing app-usability issues

Recent reviews suggest increasing friction around areas such as:

- login;
- biometrics;
- verification;
- general app functionality.

### 4. Improve communication around failed transfers

For incomplete or failed transactions, provide:

- clearer status explanations;
- realistic resolution timelines;
- better escalation routes.

---

## Limitations

This project has several important limitations:

- App-store reviews do not represent the full customer base.
- Review behaviour changed significantly over time.
- Topic labels were created from clustering plus analyst interpretation.
- Some categories overlap.
- The priority score uses analyst-defined weights.
- Fraud/security classification used a hybrid semantic + manual-validation workflow.
- Review text alone cannot establish causality.
- This project uses public data only and has no access to internal LemFi operational data.

---

## What I Would Do With Internal Data

If internal company data were available, the next stage would connect review themes with:

- transaction failure logs;
- fraud reports;
- transfer corridors;
- customer-support tickets;
- KYC/verification events;
- dispute outcomes;
- account age;
- refund/cancellation records.

That would allow the analysis to test whether public review signals correspond to measurable operational problems and whether interventions reduce friction.

---

## Repository Structure

```text
lemfi-customer-friction/
│
├── README.md
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_quality.ipynb
│   ├── 03_exploratory_analysis.ipynb
│   ├── 04_topic_modelling.ipynb
│   ├── 05_fraud_security_analysis.ipynb
│   └── 06_issue_prioritisation.ipynb
│
├── figures/
├── src/
└── reports/
```

---

## Project Status

**Project 01 — Building in Public**

This is an independent portfolio analysis using publicly available review data.

**Not affiliated with, commissioned by, or endorsed by LemFi.**
