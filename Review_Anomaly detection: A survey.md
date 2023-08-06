<Paper review: "Anomaly detection: A survey." >

Chandola, Varun, Arindam Banerjee, and Vipin Kumar. "Anomaly detection: A survey." ACM computing surveys (CSUR) 41.3 (2009): 1-58.

### 한 줄 요약
💡 Outlier 종류, label에 따른 방법론 분류, domain별 paper 리뷰 잘 되어있고 citation도 엄청 많은 제일 클래식한 리뷰 페이퍼. (근데 2009년 논문이라 최신 경향은 없음)

### Review
1. Types of Outliers
   - Point Outliers
   - Contextual Outliers
   - COllective Outliers

2. Outlier detection technique
   - Supervised outlier detection
     - Assumption: Can define normal and outlier.
     - Similar with prective model for normal vs outlier 
       - Class imbalanced problem
     - Therefore, usually not considered in outlier detection field.
   - Semi-supervised outlier detection
     - Train data has labeled instances for only the normal class.
     - Build a model for the class corresponding to normal behavior, and use the model to identify the outliers in the test data.
     - More widely applicable than supervised techniques.
     - can be adapted to unsupervised mode by using a sample of the unlabeled data set as training data. Such adaptation assumes that the test data contains very few outliers and the model learn during training is robust to these few outliers.
   - Unsupervised outlier detection
     - Most widely applicable.
     - Assumption: the normal instances are far more frequent than outliers (or not, cause high false alarm rate)
3. Output of Outlier Detection
   - Outlier scores
   - Lables

나머지는 각 domain에 대한 outlier paper review.
   - Fraud Detection, Mobile Phone Fraud Detection, etc.
