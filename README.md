# World Cup 2026 Match Results Predictor (regulation time)
A machine learning model that predicts FIFA World Cup match outcomes 
(home win / draw / away win) using historical match data and FIFA rankings.

## Results
- Baseline accuracy (FIFA ranking only): 57.7%
- Model accuracy (Random Forest): 56.2%
- Comparable to published academic benchmarks (~55-58%) for 
  three-class football prediction, as shown in the paper https://arxiv.org/html/2505.01902v1

## How it works
1. Joins 30 years of international match results with historical 
   FIFA rankings using a temporal merge to avoid data leakage
2. Model features: rank difference, points difference, 
   recent form (last 5 matches), recent goal difference, 
   venue advantage, tournament type
3. Trains a Random Forest classifier with a time-based 
   train/test split (pre/post Jan 2018)
4. Predicts win/draw/loss probabilities for a matchup between any two teams

## Example prediction
France vs Argentina (neutral venue)
France win:    44.3%
Draw:          30.7%
Argentina win: 25.0%

## Data sources
- Match results: [Kaggle - International Football Results](https://www.kaggle.com/datasets/martj42/international-football-results-from-1872-to-2017)
- FIFA Rankings: [Kaggle - FIFA World Ranking](https://www.kaggle.com/datasets/cashncarry/fifaworldranking)

## Key learnings
- Temporal joins with merge_asof to prevent data leakage
- Why draw predictions are fundamentally limited in football and always have a lower prediction accuracy
- Feature engineering vs model tuning tradeoffs
- Time-based train/test splitting for sports data

## What's next
- An xg-boost model with calculated attack and defense scores with a larger and deeper dataset
