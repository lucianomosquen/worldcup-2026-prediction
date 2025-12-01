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
│   ├── raw/                  → resultados históricos originales
│   ├── external/             → fuentes externas (ELO oficial, market values, geodata)
│   └── processed/            → datasets limpios y final_power + Monte Carlo
│
├── notebooks/
│   ├── 01-exploracion.ipynb
│   ├── 02-features-partidos.ipynb
│   ├── 03-modelo-historico.ipynb
│   ├── 04-modelo_moderno.ipynb
│   └── 05-montecarlo-worldcup2026.ipynb
│
├── reports/
│   └── figures/              → visualizaciones finales
│
└── README.md
```

---

## ⚽ Modelo híbrido del poder de un equipo

El poder final de cada selección se calculó como:

```
final_power = 0.55 * ELO_normalizado
             + 0.35 * performance_moderno_normalizado
             + 0.10 * market_value_normalizado
```

Este enfoque busca capturar:

- **Fuerza a largo plazo (ELO)**
- **Forma reciente (modelos 2018–2024)**
- **Talento / profundidad del plantel (valor de mercado)**

---

## 🎲 Simulación Monte Carlo

Para estimar las probabilidades de ser campeón:

- Se tomaron las **40 mejores selecciones** según `final_power`.
- Se simuló un torneo knockout tipo Mundial.
- Cada partido se evaluó usando un **modelo Bradley–Terry modificado con probabilidad de empate ajustada**.
- Se corrieron **5000 simulaciones**.

El resultado son las probabilidades estimadas de salir campeón.

---

## 📈 Visualización principal

(Insertar imagen: `reports/figures/worldcup2026_champions_prob_top20.png`)

---

## 📊 Resultados principales (Top 20)

| Selección | Probabilidad |
|----------|--------------|
| Spain | 5.34% |
| Argentina | 5.04% |
| England | 4.88% |
| France | 4.76% |
| Portugal | 4.50% |
| Brazil | 4.50% |
| Netherlands | 4.48% |
| Germany | 3.90% |
| Japan | 3.78% |
| Mexico | 3.36% |
*(ver dataset completo en `/data/processed/worldcup2026_montecarlo_top40.csv`)*

---

## 🛠 Tecnologías utilizadas

- Python (pandas, numpy, sklearn)
- Modelos ELO y Bradley–Terry
- Simulación estocástica (Monte Carlo)
- Normalización MinMaxScaler
- Matplotlib / Seaborn para visualización
- Flujo de trabajo estilo Cookiecutter Data Science

---

## 📌 Próximos pasos

- Simulación **con el fixture real** después del sorteo del 5/12.
- Ajuste de pesos del modelo con validación cruzada.
- Dashboard interactivo para análisis profundo.

---

Si te interesa este proyecto, podés ver mis otros trabajos en:  
**LinkedIn:** https://www.linkedin.com/in/lucianomosquen
