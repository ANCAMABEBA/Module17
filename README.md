# Module17 - Comparing Classifiers
## Summary of Findings

This project builds and evaluates machine learning models to predict **marketing campaign success** (whether a client subscribes to a term deposit) using a dataset from UC Irvine Machine Learning Repository, containing marketing campaigns data from a Portuguese banking institution. Because the target class is imbalanced, we emphasized business-aligned evaluation beyond accuracy, including **PR-AUC** and **Top-K targeting metrics**.

### Key Results
- **Accuracy is misleading** in this imbalanced setting: baseline-style models can achieve high accuracy while failing to identify any subscribers.
- A tuned **Random Forest** model provided the strongest business value:
  - **Test PR-AUC (Average Precission):** ~0.40, substantially better than the baseline positive rate (0.11), ranking true subscribers above non-subscribers
  - **Top 10% targeting (Precision@10%):** ~0.48, conversion rate among the 10% customers with the highest predicted subscription probability.
  - **Lift@10%:** ~4.26× vs the baseline subscription rate (~0.11), indicating a significant uplift in conversion rate among the 10% highest-scored customers.

### Business Insights (Actionable Levers)
Model explainability and segment analysis highlight that campaign success is driven primarily by:
- **Timing (`month`)**: subscription rates vary materially by month, suggesting campaign timing and prioritization matter (best months are March, September and October)
- **Prior campaign outcome (`poutcome`)**: customers with previous campaign **success** have substantially higher conversion propensity.
- **Recency (`pdays`)**: recent contacts (e.g., within 7–30 days) show much higher conversion rates than never-contacted customers.

While **banking client attributes** (e.g., `age`, `job`, `education`, `marital`, `housing`, `loan`, `default`) contribute some signal—most notably **`age`**—they were generally **less predictive** than campaign context/history variables, suggesting that **behavioral and timing features** are more impactful for targeting decisions.

These insights support a practical targeting strategy: **rank customers by predicted probability and focus outreach on the top-scored segment**, improving conversion while reducing wasted calls.

### Notebook
- Full analysis and experiments are available here: **[Jupyter Notebook Link](<ACM_ComparingClassifiers_17.ipynb>)**
### Dataset
- Data set is available here: **[Dataset Link](<bank-additional-full.csv>)**
