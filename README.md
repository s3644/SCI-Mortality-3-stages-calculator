# SCI Mortality 3-Stage Cascade Calculator

**Cox Proportional Hazards model for SCI mortality risk prediction**
NSCISC 2021 · 35,631 patients · C-index 0.82 · 85 features

## 🌐 Live Calculator

**https://s3644.github.io/SCI-Mortality-3-stages-calculator/**

> Enable GitHub Pages: Settings → Pages → Source: `main` branch, root folder → Save

## Files

| File | Description |
|:-----|:------------|
| `cascade_calculator.html` | **3-stage cascade calculator** (8→17→27 fields with tier toggle) |
| `index.html` | Single-page bedside calculator (all 27 fields) |
| `cascade_cox_model.json` | Cox PH coefficients for cascade model |
| `cox_model.json` | Cox PH coefficients for single-page model |

## How It Works

### Three-Stage Cascade
```
Stage 1 (Triage, 8 fields, ~2 min): Age, sex, AIS, neuro level, etiology
  → 40% cleared as LOW risk
Stage 2 (Refined, 20 fields, ~5 min): + comorbidities, surgical, residence
  → 40% stratified
Stage 3 (Full, 27 fields, ~15 min): + FIM, sphincter, hospital days
  → 20% get full survival curves + recommendations
```
**Weighted average time: ~6 min/patient** (vs. 15 min for full model)

### Technical Details
- Pure client-side JavaScript — no server, no database, no PHI transmission
- Cox PH coefficients exported as JSON (5.6 KB)
- Risk score = Σ(coefᵢ × (featureᵢ − medianᵢ))
- Probability = 1/(1 + exp(−(intercept + slope × score)))
- N/A inputs activate code-9 unknown flags (same as model training)
- Tier-based clinical recommendations with cited guideline support

## Author

**Jukrapope Jitpimolmard, MD**  
[ORCID: 0009-0001-9170-426X](https://orcid.org/0009-0001-9170-426X)

## Citation

If you use this calculator in research, please cite:
```
Jitpimolmard J. Bridging the SCI Mortality Prediction Gap: A Deployable
Cox Proportional Hazards Model with Structured Missing-Data Encoding
and Cascaded Clinical Deployment. 2026.
```

## Disclaimer

⚠️ Not for clinical use without prospective validation. This is a research tool developed from retrospective NSCISC 2021 data. Clinical decisions should not be based solely on algorithmic predictions.
