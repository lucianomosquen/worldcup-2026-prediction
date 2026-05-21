## v2 Update — Probability Calibration

The original simulation overestimated top teams due to an aggressive probability transformation applied to normalized ratings.

This updated version includes:

- Logistic probability calibration
- Improved uncertainty modeling
- Reworked expected goals scaling
- Less deterministic knockout simulations
- Updated official World Cup groups

Example:
- Spain championship probability:
  - Previous version → 40.3%
  - Current version → 11.5%

# 🌍 Predicción del Mundial 2026 – Simulación Monte Carlo  
**Proyecto de Machine Learning + Modelos Estadísticos + ELO + Métricas Modernas**

Este repositorio contiene un pipeline completo para estimar las probabilidades de cada selección de ganar el Mundial 2026 utilizando:

- **ELO oficial internacional (2024)**
- **Métricas modernas (2018–2024)** basadas en performance reciente
- **Valores de mercado de planteles** (transfermarkt)
- **Modelo híbrido de poder de equipo**
- **Simulación Monte Carlo (5000 iteraciones)**

---

## 📂 Estructura del proyecto

```
worldcup-2026-prediction/
│
├── data/
│   ├── raw/
│   ├── external/
│   └── processed/
│       ├── worldcup2026_fixture_oficial.csv
│       ├── worldcup2026_montecarlo_top40.csv
│       ├── worldcup2026_probs_champion.csv
│       └── worldcup2026_probs_paths.csv
│
├── notebooks/
│   ├── 01-exploracion.ipynb
│   ├── 02-features-partidos.ipynb
│   ├── 03-modelo-historico.ipynb
│   ├── 04-modelo_moderno.ipynb
│   ├── 05-montecarlo-worldcup2026.ipynb
│   └── 06-simulacion_fixture_oficial.ipynb
│
├── reports/
│   └── figures/
│       ├── dashboard_powerbi.png
│       └── champion_top10.png
│
└── README.md
```

---

## ⚽ Modelo Híbrido del poder de un equipo

```
final_power = 0.55 * ELO_normalizado
             + 0.35 * performance_moderno_normalizado
             + 0.10 * market_value_normalizado
```

---

## 🎲 Simulación Monte Carlo

Cada partido se modela con Bradley–Terry + probabilidad de empate + Poisson para goles.  
Se ejecutan **5000 simulaciones** completas del mundial.

---

## 🏆 Resultados principales (Top 10 Campeón)

```
team,count,prob_campeon
Spain,2016,0.4032
England,882,0.1764
France,565,0.1130
Argentina,387,0.0774
Germany,317,0.0634
Portugal,283,0.0566
Brazil,225,0.0450
Netherlands,218,0.0436
Japan,29,0.0058
Belgium,23,0.0046
```

---

## 📊 Visualizaciones  
Incluye dashboard Power BI y figuras clave.

---

## 🛠 Tecnologías utilizadas

- Python (pandas, numpy, scikit-learn)
- ELO, Bradley–Terry, Poisson
- Monte Carlo
- Power BI

---

## 🚀 Próximos pasos
- Validación cruzada  
- Dashboard web interactivo  

---

## 📬 Contacto  
**LinkedIn:** https://www.linkedin.com/in/lucianomosquen

