# Quora Question Pairs

## Business Problem

### Description
Quora is a platform for asking questions and sharing knowledge. With over 100 million monthly visitors, many questions on Quora are similarly worded, causing redundancy and inefficiency. Identifying duplicate questions helps provide instant answers to questions that have already been addressed, enhancing user experience for both seekers and writers.

**Problem Statement:**  
Identify which questions asked on Quora are duplicates of questions that have already been asked. This can help in providing immediate answers to questions that have been previously answered.

### Real-World/Business Objectives and Constraints
1. High cost of misclassification.
2. Probability of a pair of questions being duplicates is needed to set a threshold.
3. No strict latency concerns.
4. Partial interpretability is important.

## Machine Learning Problem

### Data Overview
- **File:** Train.csv
- **Columns:** qid1, qid2, question1, question2, is_duplicate
- **Size:** 60MB
- **Rows:** 404,290

### Example Data Point
| qid1  | qid2  | question1                             | question2                             | is_duplicate |
|-------|-------|---------------------------------------|---------------------------------------|--------------|
| 1     | 2     | "What is the step by step guide to invest in share market in india?" | "What is the step by step guide to invest in stock market?" | 1            |

### Mapping the Real-World Problem to an ML Problem
- **Type:** Binary classification
- **Objective:** Predict if a given pair of questions are duplicates.
- **Performance Metric:** 
  - Log-loss ([Logarithmic Loss](https://www.kaggle.com/wiki/LogarithmicLoss))
  - Binary Confusion Matrix

### Train and Test Construction
| Model                  | Vectorizer   | Train log loss | Test log loss |
|------------------------|--------------|----------------|---------------|
| Random model           | N/A          | 0.8876         | 0.8876        |
| Logistic Regression    | TF-IDF       | 0.4158         | 0.4125        |
| Linear SVM             | TF-IDF       | 0.4154         | 0.4178        |
| XGBoost (105 estimators) | TF-IDF W2V  | 0.3234         | 0.3544        |
| XGBoost (90 estimators)  | TF-IDF W2V  | 0.2949         | 0.3494        |

## Conclusion and Future Work
The project successfully predicts duplicate questions on Quora, enhancing the user experience by reducing redundancy. Future work could include:
- Implementing advanced neural network architectures.
- Further tuning of hyperparameters.
- Exploring additional feature engineering techniques.

## References
- [Kaggle Competition](https://www.kaggle.com/c/quora-question-pairs)
- [Towards Data Science Blog](https://towardsdatascience.com/identifying-duplicate-questions-on-quora-top-12-on-kaggle-4c1cf93f1c30)
