# Hypertension Risk Factors — Kenya Case-Control Study

An epidemiology project identifying modifiable and non-modifiable risk factors
for hypertension in Kenyan adults using a case-control design and multivariable
logistic regression.

## Study Design

| Feature | Description |
|---|---|
| Design | Unmatched case-control study |
| Population | Adults aged 25–70 years |
| Sites | Kenyatta National Hospital, Coast General Hospital, Pumwani Maternity, Mombasa County Referral |
| Case definition | SBP ≥ 140 mmHg or DBP ≥ 90 mmHg on two readings, or current antihypertensive medication |
| Control definition | Normotensive adults from the same outpatient clinics |
| N | 800 (400 cases / 400 controls) |

## Research Questions

1. Which modifiable risk factors are independently associated with hypertension in Kenyan adults?
2. What is the strength of association (OR) for each risk factor after adjusting for confounders?
3. Which risk factors carry the highest population attributable fractions?
4. Does urban residence independently predict hypertension beyond individual lifestyle factors?

## Key Findings

| Analysis | Finding |
|---|---|
| Strongest risk factor | Family history of HTN — Adj OR ≈ 2.8 (p < 0.01) |
| Metabolic comorbidity | Diabetes/dysglycaemia — Adj OR ≈ 2.1 |
| Modifiable — lifestyle | Overweight/Obesity (Adj OR ≈ 2.3), Heavy alcohol (≈ 1.7) |
| Modifiable — behavioural | Physical inactivity (≈ 1.8), High dietary salt (≈ 1.6) |
| Urban residence | Adj OR ≈ 1.5, independent of lifestyle confounders |
| Highest PAF | Physical inactivity & high dietary salt (high prevalence × moderate OR) |
| Model discrimination | ROC AUC > 0.75 |
| Model calibration | Hosmer-Lemeshow p > 0.05 (adequate fit) |

## Analytical Pipeline

1. Synthetic case-control data generation (calibrated to Kenya STEPS 2015, KDHS 2022)
2. Baseline characteristics table (Table 1) with chi-square tests
3. Unadjusted odds ratios (2×2 tables, Woolf SE method)
4. Multivariable logistic regression (sklearn LogisticRegression, bootstrap 95% CI)
5. Forest plot of adjusted ORs with 95% CI
6. Side-by-side comparison: unadjusted vs adjusted ORs
7. Population attributable fraction (PAF) estimation (Levin's formula)
8. Age distribution by case status
9. Risk factor prevalence heatmap (cases vs controls)
10. ROC curve and AUC
11. Hosmer-Lemeshow goodness-of-fit test
12. Epidemiological interpretation with Kenya-specific public health context

## Quick Start (Google Colab)

Open `Hypertension_Risk_Factors_Kenya.ipynb` in Google Colab. All required
libraries (numpy, pandas, scipy, sklearn, matplotlib) are pre-installed.

## Tech Stack

`Python 3.10+` · `numpy` · `pandas` · `scipy` · `scikit-learn` · `matplotlib`

## Clinical and Epidemiological Background

Non-communicable diseases (NCDs) account for an increasing share of the disease
burden in Kenya. Hypertension is the leading NCD risk factor for stroke, myocardial
infarction, and chronic kidney disease, with an estimated prevalence of 24–30% in
Kenyan adults (WHO STEPS Kenya, 2015). Urbanisation, dietary transitions, physical
inactivity, and rising obesity rates are driving the epidemic — particularly in
Nairobi and other urban centres.

This analysis applies the case-control design — efficient for identifying
determinants of prevalent or common outcomes in settings where prospective cohort
follow-up is impractical. The multivariable logistic regression framework allows
estimation of independent effects of each risk factor while controlling for
potential confounders (age, sex, SES, urban/rural).

## Data Sources

Synthetic data calibrated to:
- Kenya STEPwise Survey (WHO STEPS, 2015): adult hypertension prevalence, BMI,
  physical activity, alcohol, smoking
- Kenya Demographic and Health Survey (KDHS 2022): urban/rural distribution,
  socioeconomic strata
- Awuah et al. (2022): ORs for hypertension risk factors in sub-Saharan Africa
- Damasceno et al. (2012): CARDI study — cardiovascular risk in Africa

## Policy Implications

Results support MOH Kenya's integrated NCD prevention strategy:
- **Opportunistic screening**: blood pressure + BMI at all outpatient encounters
- **Salt reduction campaigns**: population-level dietary intervention with largest PAF
- **Physical activity promotion**: community-level programmes targeting urban sedentary populations
- **Family-based cascade screening**: index case with hypertension → screen first-degree relatives

---

*ZENIK.AI · github.com/Mwauramos*
