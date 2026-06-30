# SCI Mortality Calculator — Cox PH Model

**SCI-PReSS Project** | Jukrapope Jitpimolmard, MD

## Overview

Bedside calculator for long-term mortality prediction after spinal cord injury, using a Cox Proportional Hazards model trained on 35,631 patients from the NSCISC 2021 database (C-index 0.82, 85 engineered features).

## Cascade Architecture

| Stage | Name | Fields | Time | Use Case |
|:-----:|:-----|:------:|:----:|----------|
| 1 | Triage | 8 | ~2 min | Quick bedside screening |
| 2 | Refined | 17 | ~5 min | Clinical decision support |
| 3 | Full | 27 | ~10 min | Maximum accuracy |

All stages use the same Cox PH model. Unknown fields are handled natively via the code-9 pattern — missingness is predictive signal, not error.

## Deployment (GitHub Pages)

1. Push this folder to a GitHub repository
2. Enable GitHub Pages in repo Settings → Pages → Source: `main` branch, `/ (root)` folder
3. The calculator is pure client-side HTML/JS — no server required

### Local Testing

```bash
cd "Cox Mortality Calculator"
python3 -m http.server 8080
# Open http://localhost:8080
```

## Files

| File | Purpose |
|------|---------|
| `index.html` | Cascade calculator UI + feature engineering + risk computation |
| `cox_model.json` | Exported Cox PH coefficients (85 features) |
| `README.md` | This file |

## Model Details

- **Algorithm:** Cox Proportional Hazards (L2 regularization, α=0.1)
- **Training data:** NSCISC 2021 Public Release (35,631 patients, 12,125 deaths)
- **Features:** 85 engineered from 12 clinical categories
- **C-index:** 0.823 (bootstrap 95% CI: 0.814–0.833)
- **Validation:** 80/20 stratified split, 5-fold CV (0.8184 ± 0.0028)
- **Output:** Calibrated mortality risk probability (0–100%)

## ⚠️ Disclaimer

**Research use only.** Not for clinical decision-making without prospective validation. External validation is planned at Srinagarind Hospital, Khon Kaen University, Thailand.

## Reference

Jitpimolmard J. Development and Internal Validation of a Cox Proportional Hazards Model for Long-Term Mortality Prediction After Spinal Cord Injury: A Registry-Based Study with Deployable Bedside Calculator. 2026.
