# AI Usage Log — Assignment 1 Sentiment Analysis

## Overview
- AI was used only for allowed tasks:
  - Data loading and exploration
  - Cleaning pipeline implementation
  - Model implementation code
  - Visualization/result formatting
  - Debugging and error fixing
  - Code optimization/simplification
  - Documentation writing
- All code/results were reviewed, tested, and modified before submission.
- Manual labeling (`real_y`) and final interpretation decisions were completed by me.

---

## Entry 1 — Edge Case Identification (Quotes / Excess Punctuation)
**Category:** Data loading and exploration

- **Task:** Identify and test real edge cases present in the dataset.
- **Prompt used:** Asked how to test edge cases after confirming dataset did not have empty strings/non-English/unusual characters, only quotes and excessive punctuation.
- **AI suggested:** Use boolean masks, sample those rows, run all 3 models on same rows, document behavior.
- **What I modified:** Used my predefined masks (`has_quotes`, `has_excess_punct`) directly and sampled from those groups.
- **Why I modified:** To match my actual dataset and my notebook variables.
- **What I learned:** Edge-case testing should reflect the dataset’s real issues, not hypothetical ones.
- **AI errors found:** None (concept was fine; I simplified structure).

---

## Entry 2 — Edge Case Output Formatting (Readable Tables)
**Category:** Cleaning pipeline implementation / Visualization formatting

- **Task:** Make edge-case results readable in Jupyter.
- **Prompt used:** Asked to restructure outputs from one giant combined table into separate tables.
- **AI suggested:** Separate outputs by edge-case type and/or model (quotes vs punctuation; VADER/TextBlob/Transformer).
- **What I modified:** Created cleaner blocks for each edge case + model table.
- **Why I modified:** The original wide table was hard to read with long reviews.
- **What I learned:** Output formatting is important for manual review and documentation.
- **AI errors found:** None, but first version was too cluttered.

---

## Entry 3 — Transformer Emotion Scores Added to DataFrame
**Category:** Model implementation code

- **Task:** Add transformer emotion probabilities into DataFrame columns.
- **Prompt used:** Asked how to get emotion scores into the same output table.
- **AI suggested:** Return dict of scores, use `apply(pd.Series)`, assign columns back to DataFrame.
- **What I modified:** Adjusted variable names and output layout to fit my notebook.
- **Why I modified:** Needed consistency with my existing code and formatting.
- **What I learned:** How to expand dict outputs into multiple DataFrame columns.
- **AI errors found:** Later related variable mismatch issue (fixed separately).

---

## Entry 4 — Random 100-Row Sample Review Workflow (Step 6.1)
**Category:** Model implementation code

- **Task:** Build a 100-row sample for manual review and compare predictions from all 3 models.
- **Prompt used:** Asked if best approach was a table with `text_raw`, `real_y`, and predictions for each model to export as CSV.
- **AI suggested:** Yes — create same sample rows for all models, export CSV, manually label `real_y`, reimport for accuracy analysis.
- **What I modified:** Requested simpler code blocks and built predictions one model at a time.
- **Why I modified:** Easier to debug and explain in my notebook.
- **What I learned:** Strong evaluation workflow = predict → export → manually label → evaluate.
- **AI errors found:** None in method; I simplified implementation style.

---

## Entry 5 — Transformer Emotion → Sentiment Mapping Simplification
**Category:** Model implementation code / Code optimization

- **Task:** Simplify transformer sentiment mapping logic.
- **Prompt used:** Asked to avoid complicated scoring logic and use simple mapping:
  - sadness/anger/fear = negative
  - joy/love = positive
  - surprise = neutral
- **AI suggested:** Use top predicted emotion only, then map directly to sentiment.
- **What I modified:** Kept top emotion in CSV (`tr_top_emotion`) plus mapped sentiment prediction.
- **Why I modified:** Easier to explain and manually inspect.
- **What I learned:** Simpler deterministic mapping improves interpretability for assignments.
- **AI errors found:** None.

---

## Entry 6 — VADER Installation Help (`vaderSentiment`)
**Category:** Debugging and error fixing

- **Task:** Fix `ModuleNotFoundError` for VADER.
- **Prompt used:** Asked how to install/download VADER for `sia`.
- **AI suggested:** Install/import `vaderSentiment` package correctly.
- **What I modified:** Installed in my notebook environment and used correct import path.
- **Why I modified:** Needed VADER working in current Jupyter kernel.
- **What I learned:** Difference between package install/import issues vs code logic issues.
- **AI errors found:** None.

---

## Entry 7 — VADER Column Errors (`KeyError: 'vader_score'`, `'vader_compound'`)
**Category:** Debugging and error fixing

- **Task:** Build VADER score columns and prediction column.
- **Prompt used:** Shared code and asked why VADER blocks were failing.
- **AI suggested:** Column naming mismatch was causing errors (using column names that were not created in current cell).
- **What I modified:** Used the correct existing column names (e.g., `compound_score` instead of `vader_compound`).
- **Why I modified:** I had mixed names from older/newer notebook cells.
- **What I learned:** Refactoring in Jupyter can easily break code due to stale column names.
- **AI errors found:** None; issue was naming inconsistency in my notebook.

---

## Entry 8 — Transformer `NameError` (`emo_df` vs `emotion_df`)
**Category:** Debugging and error fixing

- **Task:** Fix transformer DataFrame assignment block.
- **Prompt used:** Shared error `NameError: name 'emo_df' is not defined`.
- **AI suggested:** Replace `emo_df` with `emotion_df` (variable mismatch).
- **What I modified:** Corrected variable name in assignment line.
- **Why I modified:** The block failed due to typo / inconsistent variable naming.
- **What I learned:** Small variable mismatches can break otherwise correct logic.
- **AI errors found:** None.

---

## Entry 9 — Speed Timing Errors (Function Signature / Wrapper Issues)
**Category:** Debugging and error fixing / Code optimization

- **Task:** Measure speed for model comparison table.
- **Prompt used:** Shared timing errors (`TypeError` string vs float, missing `vader_pred_text`) and asked how to proceed.
- **AI suggested:** I was applying the wrong function type (numeric-threshold function to raw text); suggested timing the already-working model blocks directly.
- **What I modified:** Added timing to the original working model code cells instead of building new wrapper functions.
- **Why I modified:** Simpler and less error-prone in a notebook with multiple code versions.
- **What I learned:** Best timing approach in notebooks is often to instrument code that already runs correctly.
- **AI errors found:** No major issue; I simplified the approach.

---

## Entry 10 — Accuracy Report + Confusion Matrix (Step 6.2)
**Category:** Visualization/result formatting / Debugging

- **Task:** Generate accuracy report from manually labeled file.
- **Prompt used:** Asked for simple code with just accuracy + confusion matrix for each model.
- **AI suggested:** Load CSV, standardize labels, filter valid rows, calculate accuracy, print confusion matrices with `sklearn`.
- **What I modified:** Used a minimal version and verified outputs in notebook.
- **Why I modified:** Wanted a short block that clearly met assignment requirements.
- **What I learned:** How to compare multiple model predictions against manually labeled ground truth in one loop.
- **AI errors found:** None (I initially overlooked the confusion matrix display, but it was printed).

---

## Entry 11 — Success/Failure Example Extraction (3 per Model)
**Category:** Data loading and exploration / Visualization formatting

- **Task:** Pull 3 success and 3 failure examples per model for qualitative analysis.
- **Prompt used:** Asked for simpler filtering version (`pred == real_y` and `pred != real_y`) with just sample/head output.
- **AI suggested:** Filter by match/mismatch and display small subsets of rows.
- **What I modified:** Simplified outputs to only show needed columns and manually interpreted examples.
- **Why I modified:** I wanted to write the actual analysis myself and keep notebook outputs clean.
- **What I learned:** Good qualitative review workflow = filter programmatically, explain manually.
- **AI errors found:** None.

---

## Entry 12 — Failure Example Explanations (9 Total, 3 per Model)
**Category:** Documentation writing

- **Task:** Write short explanations for why each model failed on selected examples.
- **Prompt used:** Pasted all 9 failure examples and asked for concise 1–2 sentence explanations.
- **AI suggested:** Short interpretation-based reasons (mixed sentiment, model over-weighted positive words, missed context/nuance, etc.).
- **What I modified:** Kept/edited explanations to match my own reading of each review.
- **Why I modified:** Needed accurate, concise explanations in my own voice.
- **What I learned:** Failure analysis should explain what signal the model used and what context it missed.
- **AI errors found:** None obvious; I still verified each explanation manually.

---

## Entry 13 — Model Comparison Criteria (Step 6.4)
**Category:** Documentation writing / Code optimization / Debugging

- **Task:** Complete comparison table using 5+ criteria:
  - speed
  - accuracy
  - handles emphasis
  - handles negation
  - handles long reviews
- **Prompt used:** Asked for help with speed/accuracy coding and how to evaluate interpretive criteria.
- **AI suggested:** Use measured timing + 100-row accuracy; evaluate emphasis/negation/long reviews qualitatively from examples and observed behavior.
- **What I modified:** Used my exact measured numbers and my own qualitative judgments to fill the table.
- **Why I modified:** Final table needed to reflect my notebook outputs and actual observations.
- **What I learned:** Model selection should consider both quantitative and qualitative criteria, not just accuracy.
- **AI errors found:** Some early timing suggestions conflicted with my function setup, which I corrected.

---

## Entry 14 — Final Recommendation (Step 6.5)
**Category:** Documentation writing

- **Task:** Write final model recommendation with limitations and use-case tradeoffs.
- **Prompt used:** Asked whether Transformer should be recommended despite being slowest and when to choose other models.
- **AI suggested:** Recommend Transformer overall (best accuracy/context handling), but note VADER for speed/lightweight use and TextBlob as a simple baseline.
- **What I modified:** Matched recommendation wording to my final comparison table and results.
- **Why I modified:** Needed consistency with my measured values and assignment writeup.
- **What I learned:** Final recommendations should be use-case based, not just highest accuracy.
- **AI errors found:** None.

---

## Entry 15 — README Draft Creation (`README.md`)
**Category:** Documentation writing

- **Task:** Create README for GitHub submission including project overview + explicit assignment answers/summaries.
- **Prompt used:** Asked for a standard README draft first, then clarified professor expects explicit answers (e.g., success/failure analysis).
- **AI suggested:** A structured README with overview, dataset, methods, results, edge cases, sample review, accuracy, success/failure analysis, model comparison, recommendation, run instructions, and file links.
- **What I modified:** Requested stronger alignment with assignment prompts and planned to customize exact details/paths/results wording.
- **Why I modified:** README needed to function as both repo documentation and assignment response summary.
- **What I learned:** A good README can balance reproducibility and grading requirements.
- **AI errors found:** No technical errors; first version needed more explicit assignment-focused content.

---

## Entry 16 — AI Usage Log Draft Creation (`AI_usage_log.md`)
**Category:** Documentation writing

- **Task:** Create a complete AI usage log documenting all relevant ChatGPT-assisted tasks.
- **Prompt used:** Asked for a full AI usage log covering all applicable chats in the required format; later requested a more concise bullet-style version.
- **AI suggested:** A structured AI usage log with entries including task, prompt, AI suggestions, modifications, reasons, learning, and AI errors.
- **What I modified:** Requested a shorter bullet-point version for easier copy/paste and clearer submission formatting.
- **Why I modified:** Needed a concise but complete file that still documents the full workflow.
- **What I learned:** Good AI logs should document not only AI assistance, but also my own modifications and validation steps.
- **AI errors found:** Initial version was too long for my preferred submission format; no content issue.

---

## Final Submission Note
- I attached a **filled PDF version of my answers to the assignment prompts (Steps 1–6)**.
- I also used this ChatGPT conversation to request:
  - README drafting support
  - debugging help
  - model comparison support
  - and a **thorough AI usage log** covering the AI-assisted parts of the assignment.
- All final code execution, manual labeling, result verification, and final interpretations were reviewed and completed by me.