# Home-Field Advantage in the English Premier League



## 1. Project Overview
This project analyzes the "Home-Field Advantage" in the English Premier League (EPL). The goal is to quantify how playing at home affects match outcomes and to investigate if this advantage has changed over time, specifically during the COVID-19 "ghost games" era.

## 2. Data Sources
The project uses two datasets located in the `data/` folder:
1.  **epl_matches.csv**: Contains match results (Date, Teams, FTHG, FTAG, FTR) from 2000 to 2025.
2.  **stadiums.csv**: Contains stadium names and capacities for EPL teams.

## 3. Analysis & Findings (Phase 1)

### Data Processing
* Merged match data with stadium information.
* Created features: `Goal_Diff` (Home Goals - Away Goals) and `Is_Covid` (binary flag for 2020-2021 season).
* Cleaned missing values and standardized team names.

### Key Findings from EDA
* **Win Rates:** Historical data shows a consistent higher win rate for home teams compared to away teams.
* **Goal Difference:** The distribution of goal differences is skewed positively, indicating home teams score more on average.

### Hypothesis Testing Results
1.  **Home Advantage Existence:**
    * Test: T-test on Goal Difference.
    * Result: Statistically significant. We rejected the null hypothesis. Home teams perform significantly better.
2.  **COVID Impact:**
    * Test: T-test comparing home win rates during COVID (empty stadiums) vs. normal periods.
    * Result: The home advantage decreased significantly during the COVID era, suggesting fans play a crucial role.

## 4. Future Work (Phase 2)
For the next phase (due Jan 02), I will build machine learning models (Logistic Regression and Random Forest) to predict match outcomes based on stadium capacity and team form.
