# Euro–Korean Won (EUR/KRW) Exchange Rate Forecasting

> A practical, explainable workflow for forecasting the EUR/KRW rate using macro-financial factors and event-aware evaluation.

---

## Goal

Build a forecasting model for **EUR/KRW** that 
(1) leverages **macro-financial covariates**, 
(2) remains **interpretable** for policy/desk use, and 
(3) is **robust** across stress periods (Global Financial Crisis, COVID-19, Russia–Ukraine war, energy shocks).

---

## Modeling Overview

We estimate a **factor-augmented regression** (with time-series baselines for comparison) to predict the next-period EUR/KRW, using monthly macro features:

\[
\text{FX}_{t} \;=\; a_0 \;+\; a_1\cdot \text{RER}_{t}\;+\; a_2\cdot g_{KOR,t}\;+\; a_3\cdot g_{EA,t}\;+\; a_4\cdot \Delta \pi_{t}\;+\; a_5\cdot \Delta i_{t}\;+\; a_6\cdot \text{CA}_{KOR,t}\;+\; a_7\cdot \text{FXRes}_{KOR,t}\;+\; a_8\cdot \text{VIX}_{t}\;+\; a_9\cdot \text{DXY}_{t}\;+\;\varepsilon_t
\]

**Where (from the project slides/report):**
- `RER_t`: Real exchange rate  
- `g_{KOR,t}`, `g_{EA,t}`: Growth rate changes (Korea, Euro area)  
- `Δπ_t`: Inflation differential (KOR − EA)  
- `Δi_t`: Interest-rate differential (e.g., 3-month; also tested a common-factor version)  
- `CA_{KOR,t}`: Korea current account  
- `FXRes_{KOR,t}`: Korea FX reserves  
- `VIX_t`: Volatility index  
- `DXY_t`: U.S. Dollar Index
