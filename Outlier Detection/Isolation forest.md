# Isolation Forest
💡**Original Paper의 `anomaly score`를 어떻게 구하는지 살펴보고, `sklearn.ensemble.IsolationForest`의 `score_samples()` and `decision_function()`로 `anomaly score` 구해보기**🔥
  
#Outlier detection methods #unsupervise
- Original Paper: Liu, Fei Tony, Kai Ming Ting, and Zhi-Hua Zhou. "Isolation forest." 2008 eighth ieee international conference on data mining. IEEE, 2008.
- paper: https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=4781136&casa_token=C-cPukAgOK4AAAAA:TZzyoAuwhBlDAcMhK0C6QX7bd0tJCg55h8DVRjR-h0_ENVmT4DKCy-5E02OZWI5NUEOmQEN4XA&tag=1
- python: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html#sklearn.ensemble.IsolationForest.decision_function

## Original paper
### Anomaly Score
- iTrees의 PathLength $h(x)$의 평균을 $c(n)$로 normalize한 값을 사용하는데,
- 0~1로 표현하고 싶어서 anomaly score of x given n $s(x, n) = 2^{(sth)}$으로 정의함
  <img width="503" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/058a99db-f27a-4197-9fab-048932195777">
  <img width="506" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/755f1c73-5c40-4aea-af17-fd682e2d2e7a">

**구분 방법**  
1과 가까울수록 outlier, 0과 가까울수록 inlier, 0.5 기준으로 나누게 되어있음 (contamination 고려해진 분포에 대해 0.5로 나누면 됨)
  
## `sklearn.ensemble.IsolationForest` 중심으로
### score_samples(X)
Original paper의 `anomaly score`의 opposite(음수) 버전
**구분 방법**  
-1과 가까울수록 outlier, 0과 가까울수록 inlier, -0.5 기준으로 나눔

### decision_function(X)
Original paper의 anomaly score의 분포를 가지고 있는데 범위가 다른 것. (음양의 방향도 다름)
sklearn api처럼 나누기 위해서 -1과 1사이로 만들어졌고, 나누는 기준은 0임 (0.5가 아니라 0인 이유는 offset_을 빼줘서 조정해줌)
**구분 방법**  
-1과 가까울수록 outlier, 1과 가까울수록 inlier 기준으로 나누기

### `score_samples(X)`랑 `decision_function(X)` 비교
- `decision_function()` = `score_samples()` - `offset_`
- `offset_`: `contamination`='auto'면 0.5로 고정. 0.5가 아닌 다른 수라면 고정된건 아님 (분포 조정을 위해 필요한듯)
  Offset used to define the decision function from the raw scores.
  (in sklearn documents)
  We have the relation: decision_function = score_samples - offset_. offset_ is defined as follows.
  When the contamination parameter is set to “auto”, the offset is equal to -0.5 as the scores of inliers are
  close to 0 and the scores of outliers are close to -1. When a contamination parameter different than “auto” is provided,
  the offset is defined in such a way we obtain the expected number of outliers (samples with decision function < 0) in training.
  
### `score_samples(X)`랑 `decision_function(X)` 그래프로 비교해보기
- 범위는 다르지만 분포는 같음.  
- 음수로 씌워서 original paper의 표현과 같게 만들어줌
- contamination='auto'일 때 
  ![image](https://github.com/juyeon999/Paper_review/assets/132811616/a928d271-ce14-4467-87c3-b4568176a9fe)
  
  ``` python
  d=3
  s=1050
  data = make_gaussian_data(d, s, min_distance=1, seed=2345)
  
  X = np.array(data.iloc[:, :-1])
  y = np.array(data.iloc[:, -1])
  clf = IsolationForest(n_estimators=100, max_samples=256, contamination='auto')
  y_pred = clf.fit(X).predict(X)
  
  score = -clf.score_samples(X)
  dec = -clf.decision_function(X)
  
  # cutoff가 저게 맞나? -> 맞음
  sum(score > -clf.offset_), sum(dec > 0), sum(y_pred == -1) # (87, 87, 87)
  ```
- contamination='0.05'일때
   score_samples에서 cutoff는 `self.offset_`임  
  ![image](https://github.com/juyeon999/Paper_review/assets/132811616/46efe8ca-6b4c-4a2a-99fb-3c1f8e326505)

  
  

### Reference
- score_sample, decision_function 차이가 뭐고 offset_은 뭔가용??  
  https://stackoverflow.com/questions/68061530/what-is-the-difference-between-decision-function-and-score-samples-in-isolation
