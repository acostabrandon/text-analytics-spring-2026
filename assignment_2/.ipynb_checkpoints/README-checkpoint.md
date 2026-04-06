# Text Classification Assignment 2

**Student Name:** Brandon Acosta 
**Dataset Chosen:** IMDB Dataset of 50K Movie Reviews  

---

## Overview

This project is a **binary text classification** task. The goal is to classify movie reviews as either **positive** or **negative** sentiment.

---

## Dataset Details

- **Source:** IMDB Dataset of 50K Movie Reviews  
- **Size:** 50,000 reviews  
- **Target Classes:** positive, negative  
- **Class Distribution:** balanced  
  - 25,000 positive  
  - 25,000 negative  

This balanced distribution means class imbalance was not a major issue in model training.

---

## Best Model Results

The best-performing model was **Logistic Regression + TF-IDF**.

- **F1 Score:** 0.8879  
- **Precision:** 0.8845  
- **Recall:** 0.8914  
- **Training Time:** 0.3236 seconds

This model had the strongest overall balance between precision and recall and achieved the highest F1 score of all tested models.

---

## Important Class with Justification

For this dataset, the most important class is **negative reviews**.

### Why negative reviews matter more
In a real business setting, negative reviews are often more actionable than positive ones. They can point to dissatisfaction, poor audience response, or weaknesses in the movie experience. Missing negative reviews could cause important criticism to be overlooked.

### Precision-recall tradeoff
For this reason, **recall for the negative class** is especially important. A false negative in this context means a truly negative review is incorrectly classified as positive, which would hide criticism.

The final model, **Logistic Regression + TF-IDF**, performed strongly on the negative class while also maintaining the best overall F1 score.

---

## Model Comparison Table (5 Criteria)

| Model | Accuracy | F1 | Speed (sec) | Negative Recall | Interpretability | Ease of Tuning |
|---|---:|---:|---:|---:|---|---|
| Logistic Regression + CountVectorizer | 0.8790 | 0.8787 | 4.8793 | 0.8814 | High | Easy |
| Logistic Regression + TF-IDF | 0.8875 | 0.8879 | 0.3236 | 0.8836 | High | Easy |

### Comparison Notes
- **TF-IDF** performed better than **CountVectorizer**
- **Logistic Regression** performed better than **Multinomial Naive Bayes**
- The TF-IDF model achieved the best overall F1 score
- Both final models were fast, interpretable, and easy to tune

---

## Custom Inference Summary

I created 20 new review-style examples and ran inference using the best model.

- **Correct based on my manual review:** 17 / 20  
- **Incorrect / disagreed with model:** 3 / 20  

### Key findings
- The model performed very well on **easy examples**
- It also generalized reasonably well to **slightly different review contexts**
- Most disagreements occurred on **tricky examples with mixed sentiment**
- The model handled clear positive and negative reviews better than nuanced reviews with conflicting signals

---

## Recommendation with Justification

I recommend deploying **Logistic Regression + TF-IDF** for this task.

### Why this model is the best choice
- It achieved the **highest F1 score**
- It had the **best overall balance** between precision and recall
- It performed strongly on the **negative class**, which is the more important class in this context
- It remained **simple, interpretable, and efficient**
- It generalized well on custom inference examples, with **17 out of 20 predictions** matching my manual judgment

Overall, Logistic Regression + TF-IDF was the strongest and most practical model for IMDB sentiment classification in this assignment.