# ❄️ Falla Cero — Predictive Maintenance for Smart Coolers

**A risk radar that predicts which connected beverage coolers will fail next month**, so technicians can visit them before drinks get warm and sales are lost.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/model-XGBoost-189FDD)
![PuLP](https://img.shields.io/badge/optimization-PuLP-4B8BBE)

> Built by team **Glitch Girls** for the **H4H** hackathon challenge on smart coolers.

---

## Why it matters

More than a third of sales at the point of sale depend on the coolers working. Maintenance today is **reactive**: a cooler fails, drinks warm up, customers leave, and the repair is slower and more expensive than preventing it.

## Approach (CRISP-DM)

1. **Business & data understanding** — four historical datasets of sensor readings from the coolers' microcontrollers (temperature, energy, door openings), failures and sales.
2. **Feature engineering** — technical signals such as voltage variation, energy efficiency and abnormal low temperatures.
3. **Preparation** — median imputation and normalization.
4. **Model** — **XGBoost** classifier, chosen for non-linear sensor relationships and strong class imbalance (logistic regression was less accurate). It outputs each cooler's **probability of being reported as failing next month**.
5. **Action** — an optimization layer (PuLP) to prioritize service visits, plus a dashboard concept with a per-cooler risk gauge, recommended action by risk level and the estimated economic impact of each avoided failure.

## Results (May 2025 data)

- **7,312 coolers** scored (`predicciones_mayo2025.csv`: `cooler_id`, `prob_failure`, `predicted_failure`).
- Risk distribution: **11 high-risk** (0.15 %), 5 medium-risk (0.07 %), 7,296 low-risk (99.78 %).
- Technicians can focus on a handful of devices instead of inspecting thousands.

## Repository contents

```
Reto_Coolers_Glitch_Girls.ipynb   # Full pipeline: EDA, features, XGBoost, optimization
predicciones_mayo2025.csv         # Next-month failure probability per cooler
FALLA CERO_GLITCH GIRLS.pdf       # Pitch deck
Video_Evidencia_GlitchGirls.mp4   # Demo video
MuestraRiesgos.zip                # Sample of risk outputs
```

## Running it

Open `Reto_Coolers_Glitch_Girls.ipynb` in Jupyter or Google Colab. The notebook downloads the challenge datasets with `gdown`; it needs `pandas`, `numpy`, `scikit-learn`, `xgboost` and `pulp`.

## Team

**Glitch Girls** — Valeria Arciga Valencia, Brisma Álvarez, Karen Estrada, Ximena Montes
