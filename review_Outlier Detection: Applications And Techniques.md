<Paper review: Outlier Detection: Applications And Techniques >

Singh, Karanjit, and Shuchita Upadhyaya. "Outlier detection: applications and techniques." International Journal of Computer Science Issues (IJCSI) 9.1 (2012): 307.

## 한 줄 요약
Outlier 종류, label에 따른 방법론 분류, domain별 paper 리뷰는 잘 되어 있으나 옛날 논문이다.

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
