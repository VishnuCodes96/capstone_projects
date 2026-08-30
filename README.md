# capstone_projects
All my rebounce course capstone projects together
## Capstone_project_1
# State-wise Renewable Energy Overview 2025–26

## 📊 Project Overview

This is my **first Data Analyst Capstone Project**, focused on analyzing state-wise electricity capacity, renewable energy adoption, thermal power dependence, electricity generation, peak demand, and population across **18 Indian states**.

The objective of this project was to explore how the power sector differs across states and identify patterns in **installed capacity, renewable energy penetration, thermal dependence, electricity demand, and capacity allocation**.

This project was completed as part of my learning journey as a **Data Analyst Trainee**, with a focus on applying practical data analysis techniques using Python.

---

## 🎯 Objectives

The main objectives of this analysis were to:

* Understand the state-wise distribution of installed power capacity.
* Identify states with the highest renewable energy capacity.
* Determine which states have a high dependence on thermal power.
* Compare renewable energy shares across states.
* Analyze the relationship between population, electricity demand, and installed capacity.
* Identify states with high installed capacity per capita.
* Compare electricity generation with installed capacity.
* Explore differences in power capacity mix across states.
* Perform regional-level analysis where appropriate.
* Derive actionable insights and identify areas for further investigation.

---

## 🗂️ Dataset

The dataset primarily represents information for **FY 2025–26** and covers 18 Indian states.

The data was mainly sourced from the **NITI Aayog India Climate & Energy Dashboard (ICED)**:

**Data Source:** NITI Aayog – India's Climate and Energy Dashboard

https://iced.niti.gov.in/analytics/state-wise-deep-dive

> Note: Some values in the dataset are derived or based on assumptions, as mentioned in the original data source/project documentation.

---

## 🛠️ Tools & Technologies

The project was developed using:

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Plotly Express** – Interactive visualizations
* **Jupyter Notebook / Google Colab**

---

## 🔍 Project Workflow

### 1. Data Exploration

The dataset was initially explored to understand its structure and quality.

The following checks were performed:

* Number of rows and columns
* Data types
* Descriptive statistics
* Missing values
* Duplicate records
* Basic dataset structure

The initial exploration identified:

* **7 missing values** in the `Nuclear` column.
* No duplicate rows.
* `Peak_Demand` required datatype conversion because the values contained commas and were stored as text.

---

### 2. Data Cleaning

Several data preparation steps were performed before analysis.

#### Handling Missing Nuclear Values

The missing values in the `Nuclear` column were replaced with `0`.

This was based on the assumption that the affected states did not have operational nuclear power capacity represented in the dataset. Using the mean or median would have introduced artificial nuclear capacity and could have distorted the analysis.

#### Converting Peak Demand

The `Peak_Demand` column contained comma-separated values stored as strings.

The commas were removed and the column was converted into an integer datatype to enable numerical analysis.

#### Adding Regions

A `Region` column was created to categorize the states into:

* North
* South
* East
* West
* Central
* North-East

This allowed the analysis to include some regional comparisons.

#### Creating Renewable Energy Capacity

A new `Renewable_Energy` column was calculated as:

```text
Renewable Energy =
Hydro + Other RES + Rooftop Solar Capacity
```

#### Checking Internal Consistency

The following relationship was checked:

```text
Total Capacity =
Hydro + Nuclear + Other RES + Thermal
```

Two records were found to violate this relationship.

The `Capacity_Including_Allocated_Shares` value was recalculated using the component capacity values to maintain internal consistency in the cleaned dataset.

The cleaned dataset was then exported as:

```text
cleaned_state_wise_renewable_energy.csv
```

---

## 📈 Analysis & Key Questions

The project explored several questions related to India's state-level power sector.

### 1. Which states are most dependent on thermal power?

Thermal power dependency was calculated as:

```text
Thermal Share (%) =
Thermal Capacity / Total Installed Capacity × 100
```

**Key finding:**

* **Bihar** had the highest thermal dependency in the analysis.
* Bihar, Jharkhand and Chhattisgarh showed particularly high thermal shares.
* Several states in the Eastern region showed relatively strong dependence on thermal capacity.

This highlights the differences in generation mix between Indian states and the potential importance of diversification strategies.

---

### 2. Which states have the largest renewable energy share?

Renewable share was calculated as:

```text
Renewable Share (%) =
Renewable Energy Capacity / Total Installed Capacity × 100
```

**Key finding:**

* **Arunachal Pradesh** had the highest renewable share, at approximately **91%**.
* However, its overall installed capacity is much smaller than that of major power-producing states.

This demonstrates an important analytical point:

> A high renewable percentage does not necessarily mean a state has a high absolute amount of renewable capacity.

Both **renewable share** and **absolute renewable capacity** should therefore be considered when comparing states.

---

### 3. How does population relate to electricity demand and capacity?

Correlation analysis was performed between:

* Population
* Peak Demand
* Installed Capacity

The analysis showed:

| Relationship                     | Correlation |
| -------------------------------- | ----------: |
| Population ↔ Peak Demand         |      ~0.663 |
| Population ↔ Installed Capacity  |      ~0.568 |
| Peak Demand ↔ Installed Capacity |      ~0.874 |

### Key finding

Peak demand and installed capacity showed the strongest relationship, with a correlation of approximately **0.87**.

Population had a positive but weaker relationship with installed capacity.

This suggests that factors beyond population—such as industrial activity, electricity consumption patterns, economic activity, infrastructure and demand intensity—may influence power capacity requirements.

> Correlation indicates association, not causation.

---

### 4. Which states have the highest capacity per person?

Capacity per capita was calculated as:

```text
Capacity Per Capita =
Total Installed Capacity / Population
```

**Key findings:**

* **Gujarat** recorded the highest capacity per capita in the analysis.
* Rajasthan was another high-capacity-per-capita state.
* At the regional level, the **West** had the highest average capacity per capita, followed by the South and North.

The results show that installed capacity is not distributed uniformly when adjusted for population.

---

## 📊 Visualizations

The project includes several visualizations to make the analysis easier to interpret.

### 1. Renewable Energy Capacity by State

A horizontal bar chart was used to compare renewable energy capacity across states.

A logarithmic scale was used because there were substantial differences between states with very high and very low renewable capacity.

**Key observations:**

* Gujarat and Rajasthan were among the leading states.
* Maharashtra and Tamil Nadu also had substantial renewable capacity.
* Renewable capacity was concentrated among a relatively small number of states.

---

### 2. Power Capacity Mix by State

A stacked bar chart was created to compare the contribution of:

* Hydro
* Rooftop Solar
* Other Renewable Energy Sources
* Thermal
* Nuclear

across the analyzed states.

**Key observations:**

* Rajasthan and Gujarat showed strong renewable contributions.
* Thermal power remained an important component in several states.
* Bihar, Jharkhand, West Bengal and Chhattisgarh showed relatively high thermal dependence.
* The power mix varies significantly from one state to another.

---

### 3. Renewable Energy Share vs Total Power Capacity

An interactive Plotly scatter plot was created to analyze:

* Total installed capacity
* Renewable energy share
* Population

Population was represented through bubble size.

**Key observations:**

* Gujarat and Rajasthan combine large power systems with high renewable penetration.
* Tamil Nadu also has a strong renewable position.
* Arunachal Pradesh is a notable example of a state with a very high renewable share but relatively small total capacity.
* Population size does not show a clear relationship with renewable energy share.

The interactive visualization is available in:

```text
scatter_plot_1.html
```

---

### 4. Electricity Generation vs Installed Capacity

A second interactive scatter plot was created to compare:

* Installed capacity
* Electricity generation
* Population

**Key observations:**

* Maharashtra represents a large-scale electricity market with substantial capacity and generation.
* Gujarat has very high installed capacity and strong generation.
* Chhattisgarh is an interesting outlier, showing very high generation relative to its installed capacity.

This suggests that installed capacity alone does not fully explain electricity generation.

The interactive visualization is available in:

```text
scatter_plot_2.html
```

---

### 5. Installed Capacity Heatmap

A heatmap was created to compare state-level capacity across:

* Hydro
* Rooftop Solar
* Other Renewable Sources
* Thermal
* Nuclear

**Key observations:**

* Rajasthan has a strong renewable-oriented capacity profile.
* Tamil Nadu has a relatively diversified capacity mix.
* Maharashtra has substantial thermal capacity alongside significant renewable capacity.
* Gujarat has the highest rooftop solar capacity in the analyzed dataset.
* Nuclear capacity is geographically concentrated among a small number of states.
* Several northeastern states have relatively smaller overall capacity and a greater contribution from hydro resources.

---

## 📌 Major Findings

The overall analysis produced several important observations:

### Renewable Energy

* Renewable capacity is highly concentrated among a few states.
* **Gujarat and Rajasthan** are leading states in absolute renewable capacity.
* **Arunachal Pradesh** has the highest renewable share, at approximately 91%.
* A high renewable percentage does not necessarily indicate a high absolute renewable capacity.

### Thermal Power

* **Bihar** recorded the highest thermal dependence.
* Bihar, Jharkhand and Chhattisgarh showed particularly high thermal shares.
* Thermal dependence varies considerably across states.

### Installed Capacity

* **Gujarat** had the highest total installed capacity in the analyzed dataset.
* Power capacity differs significantly across states.
* Capacity per capita also varies considerably.

### Demand & Population

* Peak demand and installed capacity had a strong positive correlation of approximately **0.87**.
* Population and installed capacity had a more moderate correlation of approximately **0.57**.
* Population alone does not explain differences in power capacity.

### Electricity Generation

* Higher installed capacity does not automatically result in proportionally higher electricity generation.
* Chhattisgarh was a notable example that warrants further investigation into capacity utilization and generation efficiency.

---

## 📊 Project Summary

| Metric                                |        Result |
| ------------------------------------- | ------------: |
| States analyzed                       |        **18** |
| Total installed capacity              | **393.34 GW** |
| Renewable capacity                    | **238.07 GW** |
| Renewable share                       |    **60.53%** |
| Highest thermal dependence            |     **Bihar** |
| Highest total capacity                |   **Gujarat** |
| Strongest demand-capacity correlation |     **~0.87** |

---

## 💡 Recommendations

Based on the analysis:

* States with high thermal dependence, particularly in the Eastern region, could be prioritized for further diversification analysis.
* States with high renewable penetration should also be evaluated for **grid integration, storage and transmission requirements**.
* Future analysis should examine **capacity utilization** rather than relying only on installed capacity.
* Economic and industrial indicators could be incorporated to better understand electricity demand.
* Renewable-resource availability and state-level energy policies could be included to understand differences in renewable adoption.

---

## ⚠️ Limitations

This project has several limitations that should be considered when interpreting the results:

1. **Limited geographic coverage**
   The analysis includes only 18 Indian states and therefore does not represent the entire country.

2. **Single-period analysis**
   The dataset primarily represents FY 2025–26, so the analysis cannot identify long-term trends or changes over time.

3. **Correlation is not causation**
   The correlation analysis identifies relationships between variables but does not establish causal relationships.

4. **Limited explanatory variables**
   Factors such as GDP/GSDP, industrial activity, electricity consumption, capacity utilization, transmission infrastructure and state-level policies were not included.

5. **Derived and assumed values**
   Some values in the source dataset are derived or based on assumptions, which may introduce uncertainty.

6. **Regional classification**
   The regional categories were manually assigned for the purpose of this analysis and may differ from classifications used by different government organizations.

---

## 🚀 Future Scope

This project can be extended in several ways.

### Possible next steps:

* Analyze multiple years to identify renewable energy growth trends.
* Calculate and compare **capacity utilization factors**.
* Analyze electricity consumption per capita.
* Include GDP/GSDP and industrial activity.
* Study the relationship between electricity demand and economic growth.
* Compare state-level renewable energy targets with actual capacity.
* Analyze solar, wind and hydro capacity separately.
* Investigate transmission infrastructure and grid constraints.
* Develop an interactive dashboard using **Power BI or Tableau**.
* Build forecasting models for electricity demand and renewable capacity.
* Compare installed capacity with actual electricity generation by source.

---

## 🎓 What I Learned

As my first data analyst capstone project, this project helped me practice the complete data analysis workflow:

* Understanding a real-world dataset
* Performing data quality checks
* Handling missing values
* Correcting datatypes
* Creating derived variables
* Validating data consistency
* Performing exploratory data analysis
* Calculating correlations
* Comparing groups and regions
* Creating static and interactive visualizations
* Interpreting analytical results
* Communicating findings through a structured analysis

More importantly, the project helped me understand that **good data analysis is not just about creating charts or calculating statistics—it is about asking meaningful questions, validating the data, interpreting results carefully, and acknowledging limitations.**

---

## 🏁 Conclusion

The analysis demonstrates that India's state-level power landscape is highly heterogeneous.

States such as **Gujarat, Rajasthan, Maharashtra and Tamil Nadu** combine substantial power infrastructure with strong renewable-energy capacity, while several Eastern and Central states remain considerably more dependent on thermal power.

The analysis also shows why a single metric is not sufficient to evaluate a state's energy position. **Installed capacity, renewable share, thermal dependence, capacity per capita, peak demand and electricity generation** each provide a different perspective.

Overall, the project suggests that a more complete assessment of state-level energy performance should consider both the **scale and composition of the power system**, as well as how effectively installed capacity is utilized.

This project is my first step toward developing practical data analysis skills, and the findings also provide several opportunities for deeper analysis in future projects.

---

## 📚 Data Source

**NITI Aayog – India's Climate and Energy Dashboard (ICED)**

https://iced.niti.gov.in/analytics/state-wise-deep-dive

---

### 👤 Project

**Project:** State-wise Renewable Energy Overview 2025–26

**Type:** Data Analyst Capstone Project

**Tools:** Python, Pandas, NumPy, Matplotlib, Seaborn, Plotly

**Scope:** State-level Power Capacity & Renewable Energy Analysis

**States Analyzed:** 18
