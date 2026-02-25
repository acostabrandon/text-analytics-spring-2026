# Assignment 1: Sentiment Analysis (VADER vs TextBlob vs Transformer)

## Project Overview

This project compares three pretrained sentiment analysis approaches on real-world airline review text:

- **VADER**
- **TextBlob**
- **Transformer model** (DistilBERT emotion model mapped to sentiment)

The goal was to:
1. Clean and prepare text data
2. Apply all three models
3. Compare predictions on the same sampled reviews
4. Evaluate model performance using manual labeling (ground truth)
5. Analyze strengths, failures, and practical tradeoffs (speed vs accuracy)

This assignment emphasizes both technical execution and critical evaluation of model behavior on real customer review text.  

---

## Dataset Description (Step 1 + Step 2)

### Dataset Chosen
- **Airline Reviews dataset** (Kaggle airline reviews / customer feedback dataset)

### Why I Chose This Dataset
I selected the airline review dataset because airline reviews are rich in real-world sentiment (positive, negative, mixed/neutral) and are strategically relevant for customer service analysis, service quality monitoring, and operational decision-making. This makes the comparison of sentiment models meaningful in a practical business context. (This aligns with my written justification in the assignment.) 

### Main Text Column
- The primary text field used for sentiment analysis was the **review body** (stored/renamed in my notebook as `text_raw`, with additional cleaned variants such as `text_vader` and `text_clean`).

### Dataset / Metadata Summary (from EDA)
From my exploration:
- The dataset contains airline review metadata such as ratings, route, traveler type, seat type, aircraft, and service sub-scores.
- Several columns had missing values (common in optional reviewer fields).
- The main review text column had strong coverage and was suitable for sentiment analysis.
- The review text was mostly English and highly sentiment-rich, with long-form customer feedback.

> Note: See the notebook for full metadata inspection, dtypes, missing-value checks, text-length statistics, and sample review outputs.

---

## Step-by-Step Work Summary (Steps 1–6)

## Step 1: Obtain Data
- Loaded the airline review dataset into Python / pandas.
- Selected airline reviews because they contain realistic customer experience narratives with strong sentiment and operational relevance.

## Step 2: Explore the Data (EDA)
I performed exploratory analysis to understand:
- Column names and data types
- Missing values
- Main text column quality
- Text length patterns
- Sample review content and language characteristics

### Initial observations
- Reviews were primarily in English
- Long-form text was common (not just short comments)
- Some punctuation-heavy reviews and quoted text existed
- The data included emotionally explicit wording (useful for sentiment testing)

### Visualizations created
- Text length distribution (histogram)
- Additional outputs in notebook tables and preview samples

---

## Step 3: Text Cleaning / Preprocessing

I created cleaned text versions for different models (instead of using one identical text field for all models), because each model behaves differently depending on punctuation and formatting.

### Cleaning approach (high level)
- Preserved a version for raw review inspection (`text_raw`)
- Created model-ready cleaned versions:
  - `text_vader` (retains more punctuation/emphasis useful for VADER)
  - `text_clean` (more standardized text for TextBlob / Transformer usage)
- Removed or standardized noise where needed (depending on model)
- Reviewed edge cases before deciding what to keep/remove

### Key edge-case findings from review
I explicitly checked for several text issues and found:
- **No empty strings**
- **No non-English / unusual character issues**
- Main edge cases identified:
  - **Quotes:** 798 rows
  - **Excessive punctuation:** 25 rows

I then sampled these edge cases and tested how each model behaved on them to document model sensitivity.

---

## Step 4: Tokenization / Feature Engineering (Model Preparation)

This project used pretrained sentiment models, so traditional vectorization (e.g., TF-IDF) was not the main focus. Instead, the “feature engineering” work centered on:
- preparing model-specific text inputs
- preserving/removing punctuation depending on the model
- mapping transformer emotion outputs to 3 sentiment classes

### Transformer sentiment mapping (emotion → sentiment)
The transformer model produced one of these top emotions:
- `sadness`, `joy`, `love`, `anger`, `fear`, `surprise`

I resolved these into sentiment classes as follows:
- **Positive** → `joy`, `love`
- **Negative** → `sadness`, `anger`, `fear`
- **Neutral** → `surprise`

This mapping was documented and used consistently during prediction and evaluation.

---

## Step 5: Apply Pretrained Models (VADER, TextBlob, Transformer)

## 5.1 VADER
- Implemented VADER using `SentimentIntensityAnalyzer`
- Used compound score thresholds:
  - `compound >= 0.05` → positive
  - `compound <= -0.05` → negative
  - otherwise neutral
- Also stored component scores:
  - neg, neu, pos, compound

## 5.2 TextBlob
- Computed polarity and subjectivity
- Resolved polarity to sentiment:
  - polarity > 0.05 → positive
  - polarity < -0.05 → negative
  - otherwise neutral

## 5.3 Transformer (DistilBERT emotion model)
- Used pretrained DistilBERT emotion classifier
- Extracted emotion probabilities
- Selected top emotion
- Converted top emotion to sentiment (positive/negative/neutral) using mapping above

---

## Step 6: Analyze and Review Results

## 6.1 Random Sample Review (100 Rows)
To create an evaluation set:
- I selected **100 random rows**
- Generated predictions from all three models on the **same 100 rows**
- Exported results to CSV
- Manually reviewed and labeled each row as:
  - `positive`
  - `negative`
  - `neutral`

This manual label column (`real_y`) served as the **ground truth** for comparison.

### Why this matters
This created a human-reviewed benchmark for evaluating the three models on the same real texts rather than relying only on model outputs.

---

## 6.2 Accuracy Report (Manual Ground Truth vs Model Predictions)

Using the manually labeled 100-row sample:

- **VADER accuracy:** **73%**
- **TextBlob accuracy:** **55%**
- **Transformer accuracy:** **82%**

### Summary
- The **Transformer** achieved the best overall accuracy on the reviewed sample.
- **VADER** performed surprisingly well and was much more competitive than TextBlob.
- **TextBlob** had the weakest performance, often struggling with nuanced or mixed reviews.

> Confusion matrices and notebook outputs are included in the notebook / figures section.

---

## 6.3 Success and Failure Examples (3 per model)

I documented **3 success examples** and **3 failure examples** for each model (VADER, TextBlob, Transformer), including:
- review text
- model prediction (and score where available)
- actual sentiment (`real_y`)
- short explanation of why the model was correct/incorrect

### What this analysis showed (high-level)
- **VADER** often succeeds when sentiment is explicit and punctuation/emphasis is strong
- **TextBlob** often misses context and can over-trust small positive words
- **Transformer** is strongest overall but still fails on mixed reviews, subtle complaints, and certain context-heavy cases

> The detailed examples are documented in the notebook and summarized in my written analysis section.

---

## 6.4 Model Comparison (5+ Criteria)

I compared the models on at least 5 criteria:

### 1) Accuracy (100-row manual sample)
- **Winner: Transformer**
- Reason: highest measured accuracy (82%)

### 2) Speed
Measured in my environment (timing from notebook runs):
- **VADER:** ~2.126 sec
- **TextBlob:** ~1.193 sec
- **Transformer:** ~7.21 sec

- **Winner: TextBlob** (fastest in my measured run)

> Note: Timing depends on hardware/environment and number of rows processed.

### 3) Handles Emphasis (caps / punctuation)
- **Winner: VADER**
- Reason: VADER is particularly sensitive to punctuation/emphasis and often captures tone intensity better on emphasized text.

### 4) Handles Negation
- **Winner: Transformer**
- Reason: better use of full context than lexicon-based scoring in many reviews with mixed phrasing or negation patterns.

### 5) Handles Long Reviews
- **Winner: Transformer**
- Reason: generally better at interpreting broader context across long customer review narratives (though still not perfect).

---

## 6.5 Final Recommendation

### Recommended model for this dataset: **Transformer**
I would recommend the **Transformer model** for this airline review dataset because it achieved the **highest accuracy (82%)** on the manually labeled 100-row evaluation sample and generally handled contextual sentiment, negation, and long reviews better than the other two models.

### Key limitation of the Transformer
- It is the **slowest** model in this comparison.
- It can still fail on mixed or nuanced reviews, especially when positive and negative statements are blended in the same review.

### When I would choose another model instead
#### Choose **VADER** when:
- speed matters more than maximum accuracy
- you want a lightweight baseline
- your text includes lots of emphasis (caps, punctuation)
- you need an interpretable lexicon-based method with sentiment component scores

#### Choose **TextBlob** when:
- you need a very simple baseline
- you want quick polarity/subjectivity features
- the project is exploratory and speed/simplicity matters more than nuanced accuracy

---

## Key Findings Summary (Quick Version)

- The airline review dataset is a strong fit for sentiment analysis because reviews contain rich real-world customer sentiment.
- Model-specific preprocessing matters (especially punctuation handling).
- Edge-case review testing (quotes, excessive punctuation) helped document model behavior.
- On a manually labeled 100-row sample:
  - **Transformer performed best (82%)**
  - **VADER was second (73%)**
  - **TextBlob was weakest (55%)**
- The best model overall for this dataset is the **Transformer**, despite slower runtime.
- VADER remains a strong practical alternative when speed and punctuation sensitivity are valuable.

---

## How to Run (Reproducibility Instructions)

## 1) Environment setup
Install required Python libraries (example):
```bash
pip install pandas numpy matplotlib seaborn nltk textblob vaderSentiment transformers torch scikit-learn
