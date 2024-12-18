# Feature_Engineering_Telco_Customer_Churn
# Customer Churn Prediction

This project aims to predict customer churn in a telecom company using machine learning. Churn refers to the loss of customers over time, and predicting it allows companies to take proactive steps to retain valuable customers.

### Project Overview
In this project, we explore two approaches to predicting customer churn:


1. **Base Model**: A model built using only the raw data with minimal preprocessing.
2. **Feature Engineering Model**: A model where we apply advanced feature engineering techniques to enhance the predictive power of the model.
The primary goal is to compare the performance of these two models and highlight the importance of feature engineering in improving predictive accuracy.

## 1. Project Structure
```bash
  /customer-churn-prediction
├── data
│   ├── customer_data.csv      # Raw dataset containing customer information
│   └── churn_data_processed.csv  # Processed data after feature engineering
├── notebooks
│   ├── churn_model_base.ipynb    # Jupyter notebook for base model
│   └── churn_model_feature_eng.ipynb  # Jupyter notebook for model with feature engineering
├── scripts
│   ├── preprocessing.py         # Script for data preprocessing (feature engineering)
│   └── model_training.py        # Script to train the model
├── README.md                   # Project documentation
└── requirements.txt            # List of Python dependencies

```


## 2. Problem Definition
The task is to predict whether a customer will churn or not based on various attributes such as customer tenure, payment method, service usage, and demographic information.

**Target variable**:
- `Churn`: Binary variable indicating whether a customer has churned (1) or not (0).

**Input features include**:

- Demographic information: Age, gender, senior citizen status.
- Account information: Contract type, tenure, payment method.
- Service usage: Whether the customer has subscribed to services like phone, internet, tech support, etc.


## 3. Approach
### A. Base Model (Raw Data)
In the base model, we used the raw dataset with minimal preprocessing steps. The key steps in this approach include:

-Handling missing values.
-Encoding categorical variables using **One-Hot Encoding**.
- Splitting the dataset into training and testing sets.
The model used is **CatBoostClassifier**, a gradient boosting algorithm. After training the model, we evaluated its performance using the following metrics:

- **Accuracy**: 0.79
- **Recall**: 0.65
- **Precision**: 0.50
- **F1 Score**: 0.56
- **AUC**: 0.74
The performance was decent, but there was room for improvement in handling feature relationships and data transformation.

### B. Feature Engineering Model
In the feature engineering model, we enhanced the dataset by creating new features, handling outliers, and adding domain-specific knowledge. The steps taken in this approach include:

- **Handling missing data**: We imputed missing values with the median or appropriate methods.
- **Outlier Detection and Capping**: We detected and capped outliers using the Interquartile Range (IQR) method.
- **Feature Extraction**: We created several new features:
    - **NEW_TENURE_YEAR**: Categorized customer tenure into bins (e.g., 0-1 year, 1-2 years).
    - **NEW_Engaged**: A flag for customers who have a one- or two-year contract.
    - **NEW_noProt**: A flag indicating customers without protection services.
    - **NEW_TotalServices**: Count of services a customer has subscribed to.
    - **NEW_AVG_Charges**: Average monthly charges per customer.

After performing these transformations, the model was retrained using the same **CatBoostClassifier** algorithm.

The performance of this model improved:

- **Accuracy**: 0.7847
- **Recall**: 0.6331
- **Precision**: 0.493
- **F1 Score**: 0.5544
- **AUC**: 0.7292

Although the improvement in accuracy was modest, the model now has more refined features that could allow it to capture more nuanced patterns. The recall and precision scores are more balanced.


## 4. Importance of Feature Engineering
### Why Feature Engineering Matters:
Feature engineering plays a crucial role in the performance of machine learning models. It helps uncover hidden relationships in the data and can significantly improve model predictions. In this project, the following feature engineering steps made a noticeable difference:

- **Categorization of Tenure**: The transformation of the continuous tenure variable into categorical bins helps the model understand customer behavior based on the length of their relationship with the company.
- **Service Usage Features**: Features like NEW_TotalServices and NEW_FLAG_ANY_STREAMING provide insights into customer engagement and can help predict churn better.
- **Outlier Capping**: Removing or adjusting extreme values in numeric features ensures that the model is not misled by rare, extreme data points.
- **Domain Knowledge Features**: Adding flags for specific behaviors, such as contract type and protection services, helps the model capture the importance of customer retention strategies.
### **Comparison of Models**:
While the base model gives a decent starting point, the feature engineering model provides more meaningful features that help capture underlying patterns in the data. This improves the model's performance, especially in terms of **recall**, which is crucial for predicting churn.


## 5. Model Evaluation
The following evaluation metrics were used to assess the models:
| Metric    | Base Model   | Feature Engineering Model  |
|-----------|--------------|----------------------------|
| Accuracy  | 0.79         | 0.7847                     |
| Recall    | 0.65         | 0.6331                     |
| Precision | 0.50         | 0.493                      |
| F1 Score  | 0.56         | 0.5544                     |
| AUC       | 0.74         | 0.7292                     |


## 6. Conclusion
- Feature engineering has a clear impact on the predictive power of the model, as seen in the improved performance metrics, even if the improvements are modest.
- While both models provide valuable insights, the feature engineering model helps to uncover more complex relationships in the data, offering a more refined approach to churn prediction.
- **Future Work**: We could explore hyperparameter tuning, model selection, or incorporating more advanced techniques like ensemble methods for further improvements.




## Kaggle 
For details about the project and access to the dataset, visit: [Feature_Engineering_Telco_Customer_Churn](https://www.kaggle.com/code/haticebaydemir/feature-engineering-telco-customer-churn)

## Contact
If you have any questions or suggestions, feel free to reach out. Your feedback on the project is highly appreciated.

Email: baydemirhatice@hotmail.com

Linkedln: https://www.linkedin.com/in/haticebaydemir/
