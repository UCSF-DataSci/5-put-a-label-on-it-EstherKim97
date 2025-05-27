# Assignment 5: Health Data Classification Results

This file contains your manual interpretations and analysis of the model results from the different parts of the assignment.

## Part 1: Logistic Regression on Imbalanced Data

### Interpretation of Results

In this section, provide your interpretation of the Logistic Regression model's performance on the imbalanced dataset. Consider:

- Which metric performed best and why?
- Which metric performed worst and why?
- How much did the class imbalance affect the results?
- What does the confusion matrix tell you about the model's predictions?

ANALYSIS:
The metric that performed best is AUC (0.9084), as it reflects the model’s ability to distinguish between classes despite the imbalance. While accuracy is the highest at 91.68%, it’s misleading because it’s driven by correct predictions of the majority class. The metric that performed worst is recall (0.3007). The model failed to identify 70% of actual positive cases, which is critical in imbalanced settings.
The class imbalance skewed results with high accuracy while lowering recall and F1 score (0.4135). The confusion matrix shows that 100 out of 143 positives were missed, indicating the model is biased toward predicting the majority (negative) class.

## Part 2: Tree-Based Models with Time Series Features

### Comparison of Random Forest and XGBoost

In this section, compare the performance of the Random Forest and XGBoost models:

- Which model performed better according to AUC score?
- Why might one model outperform the other on this dataset?
- How did the addition of time-series features (rolling mean and standard deviation) affect model performance?

ANALYSIS:
XGBoost performed better than Random Forest, with a higher AUC score (0.9956 vs. 0.9758). One reason is that XGBoost tends to handle imbalanced data better and have better control over misclassified cases.
XGBoost also learns patterns more efficiently by building trees sequentially, which helps it capture complex relationships in the data.

Adding time-series features gave both models additional temporal information. This helped the models to better understand recent trends, leading to more accurate predictions.

## Part 3: Logistic Regression with Balanced Data

### Improvement Analysis

In this section, analyze the improvements gained by addressing class imbalance:

- Which metrics showed the most significant improvement?
- Which metrics showed the least improvement?
- Why might some metrics improve more than others?
- What does this tell you about the importance of addressing class imbalance?

ANALYSIS:

After fixing the class imbalance, all metrics increased to perfect scores (1.0000). The biggest improvements were in recall and F1 score—recall went from 0.3007 to 1.0000, and F1 score from 0.4135 to 1.0000. That means the model went from missing most of the positive cases to catching all of them.

Accuracy and AUC improved the least, but  they were already high previously with accuracy of 0.9168 and AUC of 0.9084.
Some metrics, like recall, are more affected by imbalance because they depend on how well the model finds the minority class. Once the imbalance was handled, the model stopped missing positives. This shows that handling with class imbalance is important. 

## Overall Conclusions

Summarize your key findings from all three parts of the assignment:

- What were the most important factors affecting model performance?
- Which techniques provided the most significant improvements?
- What would you recommend for future modeling of this dataset?

ANALYSIS:

The most important factor that affected model performance was class imbalance. In the original results, models had high accuracy but missed many positive cases.

After applying SMOTE to reduce the class imbalance, recall and F1 score improved significantly. This confirmed that balancing the classes was essential for the model to properly detect the minority class. Adding time-based features also improved performance, especially for XGBoost.

For future modeling, other methods can be applied to reduce class imbalance. Also, for handling missing data, instead of removing rows with missing values, other methods like imputation or more advanced approaches could be explored. It would also be helpful to use time-series more complex data.