# Responsible Data Card

## Dataset purpose

This dataset is intended to support customer churn analysis and prediction.

The dataset may help identify customers who are more likely to stop using a service, so that appropriate customer-support or retention actions can be considered.

The model must not be used to automatically cancel services, deny benefits, penalize customers, or make important customer decisions without appropriate human review.

## Provenance and permission

This is a small customer churn training dataset provided as part of the task for responsible machine-learning baseline modeling.

The dataset contains customer-level information including tenure, support tickets, monthly spending, last login activity, subscription plan, and churn status.

The dataset should only be used for the intended educational and modeling purpose. Access to customer-level information should be restricted to authorized users.

Because the dataset contains customer-related information, privacy and responsible data handling should be considered before using it in a real-world system.

## Population and representation

The dataset represents customers using a service with different subscription plans and usage characteristics.

The dataset contains 12 customer records:
- 7 customers did not churn.
- 5 customers churned.

This corresponds to approximately 58.33% non-churned customers and 41.67% churned customers.

The dataset is very small and may not represent the complete customer population. Therefore, model results should not automatically be generalized to all customers.

A larger and more diverse dataset would be required before using the model for real-world decision-making.

## Features and target

### Features

- `customer_id`: Unique identifier for each customer. It is excluded from model training because it is an identifier rather than a useful predictive feature.
- `tenure_months`: Number of months the customer has been using the service.
- `support_tickets`: Number of support tickets raised by the customer.
- `monthly_spend_inr`: Customer's monthly spending in Indian rupees.
- `last_login_days`: Number of days since the customer's last login.
- `plan_type`: Customer's subscription plan, such as Basic, Standard, or Pro.

### Target

- `churned`: Target variable indicating whether the customer churned. A value of `1` indicates churn and `0` indicates no churn.

### Leakage risks

Information that becomes available only after a customer has already churned must not be used as an input feature because it could cause data leakage and unrealistic model performance.

The `customer_id` column is not used as a predictive feature.

### Sensitive attributes and proxies

The dataset does not explicitly contain common sensitive attributes such as gender, religion, caste, or ethnicity.

However, additional customer attributes should be reviewed before real-world deployment because some variables could act as indirect proxies for sensitive characteristics.

## Quality checks

The dataset contains 12 rows and 7 columns.

Missing-value check:
- No missing values were found in the dataset.

Duplicate check:
- No duplicate rows were found.

Class balance:
- Churned: 5 customers (41.67%)
- Not churned: 7 customers (58.33%)

Plan distribution:
- Basic: 5 customers
- Standard: 4 customers
- Pro: 3 customers

The observed numerical ranges were reviewed:
- `tenure_months`: 1 to 30
- `support_tickets`: 0 to 5
- `monthly_spend_inr`: 499 to 1499
- `last_login_days`: 1 to 30

No missing or duplicate records were found. Because the dataset is very small, statistical conclusions about outliers are limited.

For model evaluation, the dataset was split into:
- Training set: 9 records
- Testing set: 3 records

The split used stratification on the target variable to preserve the churn/non-churn class distribution.

## Risks and safeguards

### Bias

The dataset is very small and may not represent all customer groups. Model performance should therefore be evaluated carefully before any real-world deployment.

### Privacy

Customer-level information should only be accessed by authorized users and should not be unnecessarily exposed.

### Misuse

The prediction should support human decision-making rather than automatically determining whether a customer receives or loses a service.

### False positive risk

A false positive occurs when the model predicts that a customer will churn when the customer actually does not churn.

In this test set, there was 1 false positive.

A false positive could result in unnecessary customer-retention actions or wasted resources.

### False negative risk

A false negative occurs when the model predicts that a customer will not churn when the customer actually churns.

In this test set, there were 0 false negatives.

False negatives are important because a genuine churn risk may be missed.

### Safeguards

Important customer decisions should include human review.

The model should be monitored regularly for performance degradation and unexpected errors.

If the model becomes unreliable, automated use should be stopped and the previous decision process or a validated model should be restored.

## Intended evaluation

The machine-learning model is evaluated against a simple baseline approach.

A Logistic Regression model was trained for binary churn classification.

The dataset was divided into 9 training records and 3 testing records.

The following metrics were evaluated:

- Accuracy: 66.67%
- Precision: 50%
- Recall: 100%
- F1 Score: 66.67%

The confusion matrix was:

```text
[[1 1]
 [0 1]]

 This corresponds to:

- True Negative (TN): 1
- False Positive (FP): 1
- False Negative (FN): 0
- True Positive (TP): 1

Both false-positive and false-negative errors should be monitored because they have different consequences.

Calibration should be considered if the model's predicted probabilities are used for decision-making.

Fairness analysis should be performed if relevant demographic or sensitive-group information becomes available.

Error analysis should examine incorrect predictions to understand when and why the model fails.

Because the dataset contains only 12 records, these evaluation results should be treated as an educational baseline and not as evidence of real-world model performance.