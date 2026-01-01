# Home-Field Advantage in the English Premier League


#

## 1. Project Objective
This project conducts a statistical and technical analysis of the "Home-Field Advantage" in the English Premier League. Beyond simple win rates, we analyze correlations between technical match statistics (shots, corners, cards) and investigate the "Crowd Effect" using stadium capacity data and the unique COVID-19 "Ghost Games" period.

## 2. Data Pipeline
* **Primary Source:** EPL Match Data (2000-2025) containing ~9,000 matches.
* **Enrichment Source:** Stadium Capacity Dataset linked via team names.
* **Preprocessing:** * Parsed dates and handled timezone offsets.
    * Standardized team names (mapped inconsistencies) to enable merging.
    * Derived features: `Goal_Diff`, `Points`, `Is_Covid` flag.

## 3. Key Findings & Technical Analysis

### A. Correlation Analysis (Technical Metrics)
Using a Pearson Correlation Heatmap, we identified significant relationships:
* **Shots on Target** have the highest correlation with Goals (approx 0.6), confirming them as a primary driver of success.
* **Home Corners** show a moderate positive correlation with Home Shots, suggesting sustained pressure leads to set-piece opportunities.
* **Yellow Cards** show a weak negative correlation with goals, indicating defensive struggles.

### B. The "Fortress" Effect (Team-Level Analysis)
Analysis of Mean Goal Difference per team reveals:
* Top-tier teams (e.g., Man City, Liverpool) average a +1.5 to +2.0 goal difference at home.
* Mid-table teams often rely heavily on home games to secure points, whereas their away performance drops drastically.

### C. The "Ghost Game" Experiment (Hypothesis Test)
We statistically tested the impact of crowds using the COVID-19 period.
* **Hypothesis ($H_0$):** Crowd absence has no effect on Home Win Rate.
* **Test:** Independent T-test between Normal Era vs. Covid Era.
* **Result:** The Home Win Rate dropped from ~46% (Historical) to ~38% during the COVID era. 
* **Conclusion:** We **rejected $H_0$**. The crowd is a statistically significant factor in Home Advantage.

## 4. Visualizations Included
1.  **Correlation Heatmap:** To visualize dependencies between technical metrics.
2.  **Longitudinal Box Plots:** Showing the variance and distribution of goal differences across 25 seasons.
3.  **Capacity vs. Win Rate Scatter:** Regression analysis showing a positive trend between stadium size and home success.

## 5. Predictive Modeling (Phase 3)
We trained a **Random Forest Classifier** to predict whether the Home Team would win, using features like Stadium Capacity, Team Identity, and Covid status.

### Model Performance
* **Accuracy:** Achieved ~60-65% accuracy in predicting match outcomes.
* **Key Drivers:** Feature importance analysis revealed that **Team Identity** (who is playing) is the strongest predictor, followed by **Stadium Capacity**.
* **Implication:** While crowd size (Capacity) matters, the inherent strength of the team remains the dominant factor in EPL results.

## 6. Conclusion
This project successfully quantified the Home-Field Advantage in the EPL. We proved statistically that the advantage exists and was significantly reduced during the COVID-19 pandemic, highlighting the impact of crowds.