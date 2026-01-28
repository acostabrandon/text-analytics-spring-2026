# Assignment 1: Sentiment Analysis

## Overview
This assignment compares two pretrained sentiment analysis models (**VADER** and **TextBlob**) on _[dataset name]_.  
The goal is to understand the strengths and weaknesses of each approach.

## Dataset
- **Name:** _[Dataset name]_
- **Source:** _[Kaggle link or source]_
- **Size:** _[X rows]_
- **Domain:** _[Movie reviews / Product reviews / etc.]_

> Note: Dataset files may be excluded from the repository depending on course requirements and licensing.
> If excluded, include instructions here on how to obtain them.

## Results Summary (to be completed)
- **Model Comparison:** _[brief summary of which model performed better + why]_
- **Key Metrics:** _[accuracy / F1 / etc.]_
- **Notable Patterns:** _[what kinds of text each model handled well/poorly]_

## Key Findings (to be completed)
1. _VADER performed better on [X] with [Y]% accuracy_
2. _TextBlob struggled with [specific cases]_
3. _[Your key insight #3]_

## Lessons Learned (to be completed)
- _[What you learned about preprocessing, sentiment, evaluation, etc.]_
- _[What you would change if you did it again]_

## AI Usage
This assignment includes AI-assisted development and documentation.  
See: `docs/AI_usage_log.md`

## Repository Structure / Files
- `notebooks/sentiment_analysis.ipynb` — Main analysis notebook
- `docs/AI_usage_log.md` — AI interaction documentation
- `docs/report.pdf` — Written report (if required)
- `docs/reflection.md` — Reflection / lessons learned (if required)
- `data/` — (optional) Dataset files, if permitted

## How to Run

### 1) Install dependencies
```bash
pip install pandas numpy vaderSentiment textblob matplotlib seaborn