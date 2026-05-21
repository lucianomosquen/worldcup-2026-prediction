## Actualización v2 — Recalibración del modelo probabilístico

Luego de revisar los primeros resultados de la simulación, detecté que el modelo estaba sobreestimando a las selecciones más fuertes debido a una transformación probabilística demasiado agresiva aplicada sobre ratings normalizados.

En esta nueva versión se realizaron mejoras sobre:

- Calibración probabilística de partidos
- Modelado de incertidumbre
- Escalado de goles esperados (xG)
- Simulación de fases eliminatorias
- Actualización de grupos oficiales del Mundial 2026

Ejemplo:
- Probabilidad de España campeón:
  - Versión inicial → 40.3%
  - Versión recalibrada → 11.5%

El objetivo de esta iteración fue obtener una distribución de probabilidades más realista y representativa de la volatilidad propia del fútbol internacional.

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
Spain	0.9202	0.6180	0.4146	0.2856	0.1870	0.1154
England	0.8860	0.5744	0.3596	0.2218	0.1356	0.0822
France	0.8546	0.5408	0.3442	0.2086	0.1210	0.0692
Argentina	0.8742	0.5174	0.3168	0.1858	0.1096	0.0642
Germany	0.8832	0.5430	0.3354	0.1910	0.1096	0.0598
Brazil	0.8572	0.4984	0.2976	0.1830	0.1028	0.0570
Portugal	0.8126	0.4812	0.2780	0.1592	0.0968	0.0526
Netherlands	0.8160	0.5008	0.2944	0.1678	0.0904	0.0450
Belgium	0.7644	0.4294	0.2358	0.1226	0.0582	0.0320
Japan	0.7452	0.4094	0.2066	0.1156	0.0582	0.0284
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

