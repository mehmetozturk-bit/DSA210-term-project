
##Quantifying Home-Field Advantage in the English Premier League

---

## 1. Motivation & Problem Statement

In competitive team sports, the "Home-Field Advantage" (HFA) is a widely discussed phenomenon. However, quantifying its magnitude and identifying its drivers requires rigorous statistical analysis rather than anecdotal evidence.

The objective of this project is to analyze **25 years of English Premier League (EPL) data** to determine:
1.  **Existence:** Is the point differential between home and away games statistically significant?
2.  **Crowd Effect:** Did the "Closed Doors" (Ghost Games) policy during the COVID-19 pandemic (2020-2021 season) significantly reduce the home advantage?
3.  **Drivers:** Can we predict a home win based on external factors like stadium capacity and team form?

---

## 2. Verified Data Sources

The project utilizes two specific, publicly available datasets which have been identified and inspected.

### Dataset 1: Main Match Data (Time-Series)
* **Source:** [English Premier League (EPL) Match Data 2000-2025 (Kaggle)](https://www.kaggle.com/datasets/marcohuiii/english-premier-league-epl-match-data-2000-2025)
* **Content:** This dataset contains **9,000+ match records** spanning from the 2000-2001 season to the present.
* **Key Attributes Identified:**
    * `Date` (Temporal analysis)
    * `HomeTeam` / `AwayTeam` (Categorical identifiers)
    * `FTHG` (Full Time Home Goals) / `FTAG` (Full Time Away Goals)
    * `FTR` (Full Time Result: 'H', 'A', 'D')

### Dataset 2: Enrichment Data (Stadium Metadata)
* **Source:** [Football Stadiums Dataset (Kaggle)](https://www.kaggle.com/datasets/antimoni/football-stadiums)
* **Enrichment Strategy:**
    * I will merge this dataset with the main match data on the `Team Name` key.
    * This adds the **`Capacity`** (integer) feature to every match row, allowing me to test the correlation between crowd size and win probability.

---

## 3. Formal Hypotheses

I will conduct the following specific statistical tests:

### Hypothesis 1: The General Home Advantage
* **Null Hypothesis ($H_0$):** There is no significant difference between the mean points earned at home ($\mu_{home}$) and the mean points earned away ($\mu_{away}$). ($\mu_{home} = \mu_{away}$)
* **Alternative Hypothesis ($H_1$):** Teams earn significantly more points at home. ($\mu_{home} > \mu_{away}$)
* **Test:** Paired T-Test (alpha = 0.05).

### Hypothesis 2: The "Ghost Game" Effect (COVID-19)
* **Null Hypothesis ($H_0$):** The Home Win Percentage during the 2020-2021 (no crowd) season is equal to the historical average Home Win Percentage.
* **Alternative Hypothesis ($H_1$):** The Home Win Percentage in 2020-2021 is significantly lower than the historical average.
* **Test:** Chi-Square Test for Independence / Z-test for proportions.

---

## 4. Technical Approach & Methodology

### Phase 1: Data Processing (By Nov 28)
* **Cleaning:** Handle standard naming inconsistencies (e.g., "Man Utd" vs "Manchester United") to ensure a clean merge between the Match and Stadium datasets.
* **Feature Engineering:**
    * `Goal_Diff`: $FTHG - FTAG$
    * `Is_Covid`: Boolean flag for matches played behind closed doors.
    * `Points_Home`: Derived from FTR (3 for Win, 1 for Draw, 0 for Loss).

### Phase 2: Machine Learning (By Jan 02)
I will treat this as a **Binary Classification Problem** (Predicting Target: `Home_Win` = 1/0).

* **Models:**
    * **Logistic Regression:** To establish a baseline and interpret coefficients (e.g., how much does 10,000 extra capacity increase win odds?).
    * **Random Forest Classifier:** To capture non-linear relationships between team rankings and match outcomes.
* **Features:** `Stadium_Capacity`, `Home_Team_Rolling_Avg_Goals`, `Away_Team_Rolling_Avg_Goals`, `Season`.
* **Evaluation Metrics:** Accuracy, Precision, Recall, and ROC-AUC Score.

---

## 5. Tools

* **Python:** Primary language.
* **Pandas:** For data merging and time-series manipulation.
* **SciPy / Statsmodels:** For conducting the T-tests and Chi-Square tests.
* **Scikit-learn:** For Logistic Regression and Random Forest implementation.
* **Matplotlib/Seaborn:** For visualizing goal distributions and win rates.
