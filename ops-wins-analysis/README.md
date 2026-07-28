# OPS vs Wins Analysis
## Overview
This project investigates whether a team's OPS (On-base Plus Slugging) 
can predict how many games they win in a season, using 2026 MLB team 
batting and standings data.

## Process
**Step 1 — OPS as a predictor of Runs**
Tested AVG, OBP, SLG, and OPS against Runs Scored. OPS was the strongest 
predictor (r = 0.88), consistent with the well-known "Moneyball" finding 
that OBP/SLG matter more than batting average alone.

**Step 2 — OPS as a predictor of Wins**
Merged batting stats with team standings data. OPS alone was a much 
weaker predictor of Wins (r = 0.41, R² = 0.169) — since OPS only measures 
offense, and winning also depends on pitching and defense.

**Step 3 — Choosing a second predictor**
Tested Run Differential (Rdiff) and Runs Allowed (RA) as candidates. 
Rdiff was rejected despite its very high correlation (r = 0.91), since 
Rdiff = Runs Scored − Runs Allowed — mathematically too close to the 
definition of winning itself. RA was chosen instead, since it 
independently captures run prevention without overlapping with OPS.

**Step 4 — Multiple regression: OPS + RA**
Combining OPS and RA into one model dramatically improved performance: 
R² jumped from 0.169 to **0.756** — confirming that winning depends on 
both offensive production and run prevention together.

## Key finding
> A model using only OPS explained just 17% of the variation in team 
> wins. Adding Runs Allowed as a second predictor improved the model to 
> explain 76% of win variation — showing that OPS alone, while a strong 
> predictor of scoring, is insufficient to explain overall team success.

## Tools used
Python, pandas, matplotlib, scikit-learn

## Files
- `runs-explained.ipynb` — full analysis notebook
- `team_batting_2026.csv` — 2026 team batting stats (Baseball-Reference)
- `team_standings_2026.csv` — 2026 team standings (Baseball-Reference)
