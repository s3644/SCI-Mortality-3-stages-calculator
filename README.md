# SCI Mortality Calculator — GitHub Pages

**Cox Proportional Hazards model for SCI mortality risk prediction**
NSCISC 2021 · 35,631 patients · C-index 0.82 · 85 features

## Live Demo

After deployment: `https://<username>.github.io/sci-mortality-calculator/`

## Deploy to GitHub Pages

1. **Create a new GitHub repo** named `sci-mortality-calculator`
2. **Upload these 2 files** to the repo root:
   - `index.html`
   - `cox_model.json`
3. **Enable GitHub Pages:** Settings → Pages → Source: `main` branch, root folder → Save
4. Your calculator is live at `https://<username>.github.io/sci-mortality-calculator/`

## How It Works

- Pure client-side JavaScript — no server needed
- Cox PH model (C-index 0.82) exported as JSON coefficients
- Risk score = Σ(coefᵢ × (featureᵢ − medianᵢ))
- Probability = 1/(1 + exp(−(intercept + coef_cal × score)))
- Handles N/A inputs via code-9 unknown flags
- 27 clinical input fields with N/A toggles

## Author

**Jukrapope Jitpimolmard, MD**  
[ORCID: 0009-0001-9170-426X](https://orcid.org/0009-0001-9170-426X)

## Citation

If you use this calculator in research, please cite:
```
Jitpimolmard J. SCI-PReSS Mortality Calculator. 2026.
https://github.com/jukrapope/sci-mortality-calculator
```

## Disclaimer

⚠️ Not for clinical use without prospective validation. This is a research tool developed from retrospective NSCISC 2021 data. Clinical decisions should not be based solely on algorithmic predictions.
