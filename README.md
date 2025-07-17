# Findings

For this project, my main goal was to accurately predict which customers are likely to say “yes” to a term deposit to enable the bank to optimize marketing efforts and reduce wasted outreach.

I established a baseline to start: predicting the majority class (“no”) would have 88.73% accuracy.

Though accuracy is typically an important metric, due to class imbalance, I focused on recall, precision, F1-score, and ROC AUC because they more accurately reflected model performance given the class imbalance. Specifically:

- **Recall**: We don’t want to miss real subscribers to a term deposit
- **Precision**: We’d like to avoid wasting effort on those that are unlikely to say yes (i.e. more likely not to subscribe)
- **F1 score**: As a balance of the 2 above (recall + precision)
- **ROC AUC**: To help us rank/separate how well our model is able to separate non-subscribers from subscribers. Given the dataset imbalance, this metric helps us evaluate how good the model is at ranking and not just classifying customers.

---

For feature engineering, I one-hot encoded categorical features, dropped the “Duration” column per the dataset’s documentation, and also removed the 10 lowest-importance features based on a Random Forest feature importance.

| Metric        | Before (52 features) | After (42 features) |
|---------------|----------------------|----------------------|
| Accuracy      | ~90.05%              | ~90.02%              |
| ROC AUC       | ~0.7823              | ~0.7826              |
| Recall (Yes)  | ~0.22                | ~0.22                |

These results confirmed that the 10 features removed did in fact add little signal and removing them did not sacrifice predictive quality.

---

Then, to tune the model I used various hyperparameters for KNN, Decision Tree, and also re-evaluated Logistic Regression since that was our original baseline. I also used GridSearchCV to ensure each model was tuned fairly and not under- or overfitting due to poor hyperparameter choices.

- KNN best params: `k=41, p=1, weights=‘uniform’`
- Decision Tree best params: `max_depth=3, criterion=‘gini’, min_samples_split=2`

---

## Findings Summary

- Logistic Regression performed the best overall and had the highest ROC AUC with a good balance of precision/recall (even without tuning).
  - Highest ROC AUC & F1
- Grid search helped "level the playing field" for all the models, but Logistic Regression (simpler model) still performed the best
- Accuracy is not the best metric due to the class imbalance of the dataset. Instead, leveraging recall, precision, F1, and ROC AUC were better in evaluating the model usefulness / performance towards our goal.
- Feature selection via removing 10 of the lowest importance/indicator features helped to simplify the model without impacting performance.

---

## Future Improvements

- Adjusting the decision threshold (ex: 0.5 -> 0.3)
- Class weighting to apply a higher weight on the minority class since our dataset is so imbalanced
  - Instead of “yes”/“no” weighing the same, make misclassifying “yes” as “no” to count 5x or something
- Some sort of ranking mechanism so instead of it being a “yes”/“no” (binary!) for subscribing, it uses a predicted probability for the outcome.
  - Application: it would allow the business to look at something like Top 10% of customers that are most likely to subscribe and then reach out to those customers accordingly.

