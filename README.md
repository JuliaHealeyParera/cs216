# Perfecting the March Madness Bracket

**Authors:** Alan Qiao, Angelina Huang, Julia Healey-Parera, John Lee, Daniel Zhu  
**Report:** [`Findings.pdf`](./Findings.pdf)  

**Repository Structure:**  
- `code/` – Python scripts and notebooks for data scraping, wrangling, modeling, and analysis  
- `data/` – Raw and processed datasets used in the project  
- `modelResults/` – Output files, model summaries, accuracy metrics, and feature importance plots  
- `Findings.pdf` – Full project report, including methodology, results, and discussion  

---

## Overview
This project investigates the predictors of success in NCAA Men’s Basketball, with a focus on March Madness outcomes from 2014–2024.  
We compared historical win rates against game- and player-specific statistics to determine which metrics are most influential in predicting wins.  
We also evaluated how model performance changes when the three most influential predictors are removed.

**Research Questions:**
1. What are the best predictors of NCAA basketball success and March Madness performance?  
2. Are historical win rates or game-specific statistics more influential?  
3. How effective are models built on these predictors?  

---

## Data Sources
- **March Madness Dataset** – [Kaggle](https://www.kaggle.com) (Nishaan Amin, March 2024)  
  Tournament performance, seeds, and results.  
- **Scoring Datasets** – [TeamRankings.com](https://www.teamrankings.com)  
  Win rates by scenario (home/away, underdog, after-loss, etc.).  
  Collected via Python web scraping.  
- **Team Data** – [Sports-Reference.com](https://www.sports-reference.com/cbb/)  
  Player rosters, stats, rankings, and upperclassmen counts.  

Data wrangling steps are detailed in [`Findings.pdf`](./Findings.pdf).

---

## Methodology
We developed three lasso regression models to handle high-dimensional predictors and multicollinearity:
1. **Model 1:** All predictors (win percentages, aggregated team stats, player stats, interaction terms)  
2. **Model 2:** Win percentages and interaction terms only  
3. **Model 3:** Team and player statistics only (no win percentages)  

Lasso regression penalizes multicollinear or irrelevant predictors, shrinking their coefficients to zero, leaving only the most influential variables.

---

## Results Summary
| Model   | Accuracy | Most Influential Predictor | Notes |
|---------|----------|----------------------------|-------|
| Model 1 | 0.75     | Field goals attempted      | Best performance, strong mix of features |
| Model 2 | 0.54     | Seed difference            | Underperformed despite including win rates |
| Model 3 | 0.75     | Seed difference, rebounds  | Equal to Model 1 without win percentage features |

**Key Takeaways:**
- Team-specific statistics (field goal attempts, rebounds, 3-pointers, free throw attempts) are stronger predictors than historical win rates.  
- Removing win percentages does not reduce predictive accuracy.  
- Seed difference appears influential even when not tied to direct ranking context.

---

## Limitations
- Narrow time frame (2021–2024) for some scraped datasets  
- Potential bias from focusing on top 7 scorers for upperclassmen analysis  
- Unequal weighting toward teams advancing deeper in tournaments  
- Per-season rather than per-game aggregation may obscure trends  

---

## Future Work
- Expand dataset to more seasons for robust trend analysis  
- Explore additional interaction terms and adjusted statistics  
- Analyze performance in other high-stakes tournaments  
- Incorporate more well-rounded player contribution metrics  

---

  
## Contact
Contact alan.qiao@duke.edu and julia.healey-parera@duke.edu for any questions!
