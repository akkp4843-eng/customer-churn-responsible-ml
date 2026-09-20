# ML Risk Register

| Risk | Potential impact | Mitigation |
|---|---|---|
| Small dataset | Model performance may not generalize to real customers. | Collect a larger and more representative dataset before real-world deployment. |
| False positive | A customer may be incorrectly identified as likely to churn, causing unnecessary retention actions. | Monitor false positives and require human review before important actions. |
| False negative | A customer who is actually likely to churn may be missed. | Monitor recall and false negatives and review model performance regularly. |
| Data leakage | The model may appear more accurate than it really is. | Only use information that would be available at the time the prediction is made. |
| Privacy risk | Customer information could be exposed or misused. | Restrict access and protect customer-level data. |
| Bias or poor representation | The model may perform differently for customer groups that are not well represented in the data. | Use representative data and perform fairness analysis when relevant group information is available. |
| Model degradation | Model performance may decrease when customer behaviour changes over time. | Monitor performance and retrain or replace the model when necessary. |
| Automated decision misuse | Customers could be unfairly affected by an incorrect prediction. | Use predictions as decision support and keep human review for important decisions. |
| Incorrect interpretation | Users may treat a prediction as a fact rather than a risk estimate. | Clearly communicate that predictions are probabilistic and require appropriate interpretation. |