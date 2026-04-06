# AI Usage Log

This log documents the portions of this ChatGPT conversation that were used in ways allowed by the assignment guidelines. I excluded exchanges that focused on model selection decisions, feature engineering decisions, error analysis, or evaluation/reflection on the 20 custom examples. Each entry below reflects a specific use of AI that supported implementation, debugging, concept understanding, visualization, or generation of custom inference examples.

---

## Entry 1 — Step 2 notebook setup and EDA structure

**1. AI use category**  
Code implementation

**2. What task were you trying to do?**  
I was starting the notebook for Assignment 2 and needed help building the Step 2 EDA section from the beginning using the IMDB dataset.

**3. What prompt did you use?**  
I asked ChatGPT to help me start the notebook from the beginning, use AutoEDA/AutoViz, and answer questions 2.1–2.3 step by step.

**4. What did AI suggest?**  
AI suggested a notebook structure for Step 2 that included importing the dataset, checking shape, columns, data types, missing values, and target distribution, and creating text analysis outputs for class balance and text length.

**5. What did you modify?**  
I later simplified the notebook and removed some parts that felt too busy or too polished. I also requested that the code be broken down requirement by requirement rather than generated as one large notebook.

**6. Why did you modify it?**  
I wanted the notebook to look like my own work, match class style more closely, and stay at a practical grad-student level.

**7. What did you learn?**  
I learned how to structure EDA for a text classification assignment in a way that answers the prompt directly rather than relying only on automated profiling.

**8. Any AI errors found?**  
Yes. The first version was more elaborate than I wanted and included extra sections I later removed or simplified.

---

## Entry 2 — Replacing manual AutoEDA with AutoViz

**1. AI use category**  
Code implementation

**2. What task were you trying to do?**  
I wanted to replace a manual dataframe summary block with AutoViz so that the notebook would automatically create visualizations.

**3. What prompt did you use?**  
I asked ChatGPT to change the manual summary block to an AutoViz version and tell me if a specific package was needed.

**4. What did AI suggest?**  
AI suggested importing `AutoViz_Class`, running `AV.AutoViz(...)` on the IMDB dataframe, and installing the `autoviz` package if needed.

**5. What did you modify?**  
I kept AutoViz but later reduced its prominence and made it a smaller supporting section rather than the main part of my EDA.

**6. Why did you modify it?**  
The first AutoViz output felt too heavy for this assignment and created too many visuals, which made the notebook look less natural.

**7. What did you learn?**  
I learned that AutoViz can be useful for quick exploratory inspection, but it is better to pair it with simple custom tables and charts for a class assignment.

**8. Any AI errors found?**  
Not exactly an error, but the first implementation encouraged an output style that was too large and visually noisy for my use case.

---

## Entry 3 — Debugging AutoViz and reducing excess output

**1. AI use category**  
Debugging syntax/errors; understanding concepts

**2. What task were you trying to do?**  
I was trying to understand why AutoViz gave strange output messages and why it generated far more visuals than I wanted.

**3. What prompt did you use?**  
I asked why I was seeing AutoViz-related messages and later explained that the notebook was producing too many visualizations and did not look natural.

**4. What did AI suggest?**  
AI explained that the “No continuous var in data set” message was not a real error, the NLTK download logs were dependency messages rather than failures, and AutoViz was less useful on raw text-only data. It also suggested minimizing AutoViz usage or using only a sample.

**5. What did you modify?**  
I kept AutoViz but treated it as a small overview only. I relied more on direct pandas summaries and simpler plots for the actual assignment requirements.

**6. Why did you modify it?**  
I wanted cleaner, more believable notebook output and less unnecessary noise.

**7. What did you learn?**  
I learned that AutoViz is better for structured tabular datasets than pure text datasets and that automated EDA should be used selectively.

**8. Any AI errors found?**  
AI initially leaned too hard into AutoViz output before I redirected the notebook toward simpler, assignment-focused analysis.

---

## Entry 4 — Step 2.1 metadata code blocks

**1. AI use category**  
Code implementation

**2. What task were you trying to do?**  
I wanted to rebuild the notebook from the dataframe import onward and answer the Step 2.1 metadata requirements one by one.

**3. What prompt did you use?**  
I asked ChatGPT to provide separate blocks for rows, columns, data types, missing values, and target distribution, and to keep the output simple.

**4. What did AI suggest?**  
AI provided separate code blocks for loading the dataframe, printing shape, listing columns and data types, calculating missing values, summarizing target distribution, and plotting a simple bar chart for sentiment labels.

**5. What did you modify?**  
I kept the simple blocks and used them in place of earlier combined sections.

**6. Why did you modify it?**  
I wanted the notebook to answer the assignment requirements directly and clearly, without relying on extra helper columns or unnecessary AutoViz output.

**7. What did you learn?**  
I learned how to isolate each requirement into its own short code block so the notebook would be easier to follow and explain.

**8. Any AI errors found?**  
No major code errors. The main issue was that I had to ask for more simplification before the structure matched what I wanted.

---

## Entry 5 — Cleaning and preprocessing implementation for sentiment reviews

**1. AI use category**  
Code implementation

**2. What task were you trying to do?**  
I needed to build the Step 3 cleaning pipeline for IMDB reviews using the assignment guidance for sentiment/review data.

**3. What prompt did you use?**  
I asked for a simple, step-by-step cleaning process appropriate for sentiment reviews, with before/after validation examples.

**4. What did AI suggest?**  
AI suggested a light cleaning pipeline that removed HTML tags like `<br />`, removed leftover slash artifacts, normalized whitespace, and preserved punctuation, contractions, capitalization, and negation. It also suggested before/after checks for one positive and one negative review.

**5. What did you modify?**  
I tested the cleaning output, confirmed that HTML had been removed, and focused only on the minimal steps that made sense for sentiment analysis.

**6. Why did you modify it?**  
I wanted the cleaning to stay aligned with the assignment guidance and avoid over-cleaning review text.

**7. What did you learn?**  
I learned that preprocessing should depend on the task. For sentiment analysis, preserving punctuation and negation can matter more than making the text aggressively uniform.

**8. Any AI errors found?**  
At first, I thought the cleaning had not worked. AI helped me check whether I had printed the cleaned column correctly and then suggested a stronger regex pattern. The final code worked as intended.

---

## Entry 6 — Step 4 implementation of feature engineering setup

**1. AI use category**  
Code implementation

**2. What task were you trying to do?**  
I needed to implement Step 4 of the assignment by setting up the two chosen feature methods in a way that matched the class workflow.

**3. What prompt did you use?**  
I asked for the full Step 4 code in clean notebook order and later clarified that train/test split belonged in Step 5.1, so Step 4 should only define the feature methods and parameters.

**4. What did AI suggest?**  
AI provided code to import `CountVectorizer` and `TfidfVectorizer`, set `max_features=3000`, define both feature methods, and document the selected settings in a simple dataframe.

**5. What did you modify?**  
I kept the implementation but moved the train/test split to Step 5.1 to avoid leakage and stay consistent with the assignment structure.

**6. Why did you modify it?**  
The assignment placed train/test split in Step 5, and fitting the vectorizers before the split would have been bad practice.

**7. What did you learn?**  
I learned why it is important to separate feature-method setup from fitting the vectorizers and why leakage matters in text classification.

**8. Any AI errors found?**  
AI initially mixed the split into Step 4. I corrected that and used only the parts that fit the assignment order.

---

## Entry 7 — Step 5 implementation of train/test split, vectorization, and model training

**1. AI use category**  
Code implementation

**2. What task were you trying to do?**  
I needed to implement the full modeling workflow using my selected feature methods and algorithms.

**3. What prompt did you use?**  
I asked for Step 5 code blocks for train/test split, CountVectorizer, TF-IDF, and the selected algorithms.

**4. What did AI suggest?**  
AI generated code to split the cleaned text into training and test sets using stratification, fit CountVectorizer and TF-IDF on `X_train`, transform `X_test`, train Multinomial Naive Bayes and Logistic Regression on both feature sets, and compare the resulting accuracy, precision, recall, and F1 scores in a dataframe.

**5. What did you modify?**  
I kept the selected algorithms and feature methods but removed extra comments and any styling that did not match my notebook style.

**6. Why did you modify it?**  
I wanted the code to look more consistent with my own class notes and prior work.

**7. What did you learn?**  
I learned how to structure a fair model comparison by testing both algorithms on both feature methods and then comparing the results in one table.

**8. Any AI errors found?**  
No major code errors. The main adjustment was simplifying presentation and keeping the code closer to class style.

---

## Entry 8 — Confusion matrix and classification report implementation/debugging

**1. AI use category**  
Code implementation; debugging syntax/errors; visualization

**2. What task were you trying to do?**  
I needed to implement Step 6.1 and 6.2 for all four models and get the confusion matrices to actually display in the notebook.

**3. What prompt did you use?**  
I asked for classification report and confusion matrix code using the exact style suggested by the professor’s instructions, then later explained that the confusion matrix plots were not rendering.

**4. What did AI suggest?**  
AI suggested code that printed `classification_report(y_test, y_pred)`, computed `confusion_matrix(y_test, y_pred)`, and used `ConfusionMatrixDisplay(cm).plot()`. It later revised the confusion matrix cells to include `plt.subplots(...)`, `colorbar=False`, `values_format="d"`, and `plt.show()` so the figure would display.

**5. What did you modify?**  
I reran the confusion matrices with explicit plotting code and kept the final version that successfully displayed the four 2x2 plots.

**6. Why did you modify it?**  
The original confusion matrix display objects were not rendering correctly, so the code needed to be adjusted.

**7. What did you learn?**  
I learned that a `ConfusionMatrixDisplay` object may not always render in Jupyter unless the plotting cell is made more explicit.

**8. Any AI errors found?**  
Yes. The first confusion matrix version technically ran but only returned the object text instead of displaying the figure. It had to be debugged and revised.

---

## Entry 9 — Step 6.5 implementation of five-criteria comparison and summary chart

**1. AI use category**  
Code implementation; visualization

**2. What task were you trying to do?**  
I needed to build the Step 6.5 comparison table using at least five criteria and produce a visual summary of the final models.

**3. What prompt did you use?**  
I asked for help implementing the five-criteria comparison and a summary chart for the final two models.

**4. What did AI suggest?**  
AI suggested code to time the final two Logistic Regression models, build a comparison table using accuracy, F1, speed, negative recall, interpretability, and ease of tuning, and create a bar chart comparing the metrics.

**5. What did you modify?**  
I kept the criteria and chart because they fit the assignment well and were easy to interpret.

**6. Why did you modify it?**  
I wanted the comparison to be direct, assignment-compliant, and easy to explain in my own words.

**7. What did you learn?**  
I learned how to combine both quantitative criteria and practical deployment criteria into a single comparison table.

**8. Any AI errors found?**  
No significant code errors. The comparison section worked well once the prior model results were available.

---

## Entry 10 — Step 7 custom inference example generation and inference code

**1. AI use category**  
Generating custom inference examples; code implementation

**2. What task were you trying to do?**  
I needed to complete Step 7 by generating 20 new review-style text examples and running inference with my best model.

**3. What prompt did you use?**  
I asked for 20 new examples, including easy, tricky, and slightly different-context examples, and then asked for the inference code using the best model and vectorizer.

**4. What did AI suggest?**  
AI suggested 10 easy examples, 5 tricky examples involving mixed sentiment, ambiguity, or sarcasm, and 5 examples from slightly different contexts within the movie/review domain. It also provided code to store the new texts, transform them with the fitted TF-IDF vectorizer, predict labels with the best Logistic Regression model, and store the results in a dataframe.

**5. What did you modify?**  
I used the generated examples and inference code, then reviewed the model outputs myself.

**6. Why did you modify it?**  
The assignment explicitly allows AI-assisted generation of the 20 custom inference examples.

**7. What did you learn?**  
I learned how to test whether the trained model generalizes beyond the original train/test split using manually designed inference prompts.

**8. Any AI errors found?**  
No major implementation errors. Later evaluation of the examples was done separately and should not be counted as an allowed AI use item.

---

## Entry 11 — Creation of this AI Usage Log

**1. AI use category**  
Documentation writing

**2. What task were you trying to do?**  
I needed to create a complete AI usage log for this project using only the allowed AI-use categories.

**3. What prompt did you use?**  
I asked ChatGPT to review the full conversation, identify all relevant exchanges that fit the allowed list, and organize the results into a polished Markdown file suitable for a GitHub repository.

**4. What did AI suggest?**  
AI reviewed the conversation, filtered out disallowed uses such as model-selection decisions and error-analysis interpretation, and drafted structured log entries using the requested format.

**5. What did you modify?**  
I will review the log and make any final wording edits needed before submitting it with the project.

**6. Why did you modify it?**  
I want the final documentation to reflect my actual use of AI honestly and align with the class policy.

**7. What did you learn?**  
I learned the importance of distinguishing between AI-assisted implementation and areas where my own analysis and judgment were required.

**8. Any AI errors found?**  
No major errors in this final documentation step, but I will still review it carefully before submission.
