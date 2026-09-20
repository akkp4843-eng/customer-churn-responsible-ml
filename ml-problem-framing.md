# ML Problem-Framing Memo

## 1. Problem

The business wants to identify customers who may be at risk of leaving the service.

The machine-learning system is designed to support customer-retention teams by providing a churn-risk prediction.

## 2. Decision to support

The prediction may help the customer-retention team decide which customers may need additional support or retention attention.

The model should only support the decision. It must not automatically cancel services, deny benefits, or penalize customers.

Important customer decisions should include human review.

## 3. Prediction target

The model predicts customer churn.

The target variable is `churned`:

- `1` = customer churned
- `0` = customer did not churn

## 4. Unit of observation

One row represents one customer.

Therefore, the unit of observation is an individual customer record.

## 5. Input features

The model uses:

- `tenure_months`
- `support_tickets`
- `monthly_spend_inr`
- `last_login_days`
- `plan_type`

The `customer_id` field is excluded because it is only an identifier.

## 6. Non-ML baseline

A simple rule-based approach can be used as a baseline.

For example, customers who have not logged in for a specified number of days could be flagged for review.

The ML model should provide useful improvement over such a simple rule before it is considered for real-world use.

## 7. Why ML is being considered

Machine learning can combine multiple customer characteristics instead of relying on only one manually selected rule.

The model can use information about customer tenure, support activity, spending, login activity, and subscription plan to estimate churn risk.

However, the current dataset contains only 12 records, so it is not sufficient for reliable real-world deployment.

## 8. False-positive cost

A false positive occurs when the model predicts that a customer will churn but the customer does not actually churn.

Possible consequences include unnecessary retention communication, wasted resources, or unwanted offers.

False positives should therefore be monitored.

## 9. False-negative cost

A false negative occurs when the model predicts that a customer will not churn but the customer actually churns.

Possible consequences include missing an opportunity to provide appropriate customer support and potentially losing the customer.

False negatives should therefore also be monitored.

## 10. Human review

Model predictions should be treated as risk indicators rather than facts.

Human review should occur before important customer-retention actions are taken.

## 11. Monitoring

The model should be monitored using:

- Accuracy
- Precision
- Recall
- F1 Score
- False positives
- False negatives

Performance should be checked regularly as new customer data becomes available.

## 12. Rollback conditions

Model use should be stopped or reviewed if:

- Performance decreases significantly.
- Data quality problems are discovered.
- Data leakage is detected.
- Unexpected bias or fairness concerns are identified.
- Predictions become unreliable.

A validated previous process or model should be used while the issue is investigated.

## 13. Baseline model results

A Logistic Regression model was trained using the available customer churn dataset.

The dataset contained 12 records.

The data was divided into:

- 9 training records
- 3 testing records

The test results were:

- Accuracy: 66.67%
- Precision: 50%
- Recall: 100%
- F1 Score: 66.67%

The confusion matrix was:

```text
[[1 1]
 [0 1]]
