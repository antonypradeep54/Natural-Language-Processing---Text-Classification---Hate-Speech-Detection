# Project Scope — Hate Speech Detection Using Natural Language Processing

## 1. Project Overview
Develop and evaluate a binary text classification model using Natural Language Processing (NLP) and machine learning to identify potentially racist or sexist hate speech in Twitter data. This is an educational portfolio project, not an operational Twitter/X system.

## 2. Business Problem
Social media platforms receive large volumes of user-generated content. Manual moderation alone can be difficult to scale. A classification model could help prioritize potentially harmful content for human review while minimizing unnecessary flags on legitimate expression.

## 3. Project Objectives
- Apply tweet-specific text preprocessing and TF-IDF feature extraction.
- Establish a Logistic Regression baseline.
- Evaluate the effect of balanced class weights on minority-class detection.
- Optimize regularization using stratified cross-validation.
- Compare model performance and explain precision-recall trade-offs from a product perspective.

## 4. Dataset
Input: `data/TwitterHate.csv`.
Expected fields: `id` (tweet identifier), `label` (0 = non-hate, 1 = hate), and `tweet` (text).
Validate schema, missing values, labels, duplicates and class distribution before training. The dataset is not included in the public repository because redistribution permissions remain unverified. Users must supply an authorized copy.

## 5. Functional and Technical Scope
1. Set up the GitHub project and Google Colab dependencies.
2. Load and validate the dataset; examine class imbalance.
3. Normalize casing, remove complete user handles and URLs, tokenize using NLTK TweetTokenizer, remove redundant tokens and hashtag markers while retaining hashtag terms. Preserve meaningful negations; evaluate other stop-word and short-token removal choices.
4. Inspect common terms using training data.
5. Check duplicate texts and conflicting labels; remove or isolate duplicates, including identical normalized texts, before partitioning to avoid cross-split leakage.
6. Create reproducible stratified training and held-out test partitions.
7. Use TF-IDF with a maximum vocabulary of 5,000 features. Fit preprocessing components that learn from data and TF-IDF only on training data, including within each cross-validation fold using a scikit-learn pipeline.
8. Train a baseline Logistic Regression model and a class-balanced Logistic Regression model.
9. Tune regularization strength C and compatible penalty/solver combinations using GridSearchCV and four-fold StratifiedKFold on training data. Use positive-class recall as the primary search metric, consistent with the original assignment; report precision and F1 alongside it.
10. Select the model using training cross-validation results, then evaluate frozen models on the held-out test data without refitting or tuning on that data.
11. Demonstrate predictions on illustrative unseen text and document limitations.

## 6. Evaluation Criteria
Report accuracy, positive-class precision, recall and F1-score, confusion matrices and class support. Compare the three model configurations and a majority-class reference. Explain false positives (legitimate content flagged) and false negatives (harmful content missed). Consider moderation workload and the precision-recall trade-off; no minimum performance target is established before validation. Do not select thresholds or hyperparameters using held-out test results.

## 7. Responsible AI and Product Considerations
The proposed use case is decision support: flag potentially harmful content for human review, not automatic deletion or account sanctions. Dataset labels are limited proxies for racist or sexist hate speech and may not generalize to all harmful content, languages or communities. Sarcasm, context, quoted speech and identity terms can produce errors. Document potential bias and fairness limitations; do not claim fairness without appropriate evidence. A production system would require policy alignment, representative evaluation, human oversight, appeals and monitoring.

## 8. Deliverables
- `requirements.txt` with dependencies, pinned after successful environment validation.
- `notebooks/Hate_Speech_Detection.ipynb` with numbered Markdown explanations preceding code blocks.
- `README.md` with project overview and execution instructions.
- `docs/project-scope.md` (this document).
- `docs/validation.md` with actual execution environment, data checks, metrics and limitations.
- LinkedIn portfolio post after validation and review.

## 9. Acceptance Criteria
- Notebook runs end-to-end in Google Colab with an authorized dataset.
- Data validation and split methodology are documented; duplicate leakage and test-set fitting are prevented.
- Baseline, balanced and tuned models are evaluated using consistent metrics.
- Cross-validation and model selection are confined to training data.
- Actual results and limitations are documented without unsupported performance claims.
- GitHub changes are reviewed through a pull request before merging.

## 10. Out of Scope and Future Enhancements
Live Twitter/X integration, automatic moderation, production deployment and transformer-based models are outside the current scope. Future work may evaluate BERT or other contextual models, threshold selection using validation data, fairness evaluation and a human-in-the-loop moderation prototype. These are proposals, not committed deliverables.

## 11. Reference and Status
Based on the original course assignment, “Help Twitter Combat Hate Speech,” and the agreed AI PM – CT project refinement. The leakage-prevention, responsible AI and acceptance criteria above are proposed refinements. Model performance and dataset redistribution permissions remain pending validation.
