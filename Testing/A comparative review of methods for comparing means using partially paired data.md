# 논문 리뷰: A comparative review of methods for comparing means using partially paired data
**주제: 부분적 쌍체 검정(partially paired data) 방법**

Guo, Beibei, and Ying Yuan. "A comparative review of methods for comparing means using partially paired data." Statistical methods in medical research 26.3 (2017): 1323-1340.

## 배경
- 두 집단의 평군을 비교하는 테스팅을 진행할 때, 실험 디자인이나 결측치 때문에 불가피하게 부분적 쌍체 데이터를 얻게된다.
- 부분적 쌍체 데이터(Partially paired data)란 paired and unpaired observations의 combination이다.
 <img width="835" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/99f400a8-7e03-4404-8bbc-ba16e7ae1d7f">

- 부분적 쌍체 데이터를 검정하기 위한 9개의 방법론을 비교하고자 한다.
  - 비교 기준: effect size, sample sizes, correlations between the paired variables 등을 고려한 다양한 시나리오 하에서의 성능  
  - 비교 대상: two-sample t-test, paired t-test, corrected z-test, weighted t-test, pooled t-test,
    optimal pooled t-test, multiple imputation method, mixed model approach, modified maximum likelihood estimate.

## 결론
아래의 경우에 따라 우세한 테스트 방법론이 다름. 그 결과는 다음과 같음.  
- Sample size 충분하고 데이터가 정규분포를 따를 때, test based on the modified maximum likelihood estimator
- Sample size 충분하고 데이터가 정규분포를 따르지 않을 때, optimal pooled t-test
- Sample size 충분하지 않고(작고) 두 변수 모두 결측치가 있을 때, optimal pooled t-test
- Sample size 충분하지 않고(작고) 한 변수만 결측치가 있을 때, paired t-test
  
## 부분적 쌍체 데이터 검정하는 방법들
### 1. 단순한 방법들
**1. 부분적 쌍체 데이터 독립이라고 가정하고 independent t-test 하기**
- 장점: 모든 데이터를 사용할 수 있음.
- 단점: paired measurement에 대한 correlation을 무시하게 되서 1종 오류와 분산 추정에 있어서 편향을 줌.

**2. 쌍체가 아닌 관측치들을 버리고, 쌍체인 관측치로만 paired t-test 수행하기**
- 대부분의 통계 프로그램이 사용하는 방식
- 장점: 1종 오류 지킬 수 있음.
- 단점: 데이터의 일부를 버리기 때문에 정보의 손실이 있음.

### 2. Pooled t-test
Paired observations에서 얻은 pre-post 평균 차이의 검정 통계량과 Unpaired observations에서 얻은 pre평균과 post 평균 차이에 대한 검정 통계량을 합쳐서 쓰는(Pooled) 방법.

<img width="670" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/bdda4c47-bc8a-4f9f-b22b-bd501965c0f7">

### 3. Optimal pooled t-test
Pooled t-test처럼 paired observations and unpaired observations의 검정 통계량을 합쳐서 쓰는 방법인데, 두 검정 통계량에 다른 가중치를 줘서 사용하는 방식.
동일한 가중치를 줘서 사용한다면[1], pre-post 차이를 검정하는데에 가장 최적의 통계적 검정력을 가지지는 않는다.  
이에 가장 검정력을 준다고 알려져있는, inversely proportional to the variances of the estimates에 따라 가중치를 주는 방법.

<img width="670" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/21c71b81-843e-48e0-a78a-76b51d36f163">


### References
[1] Samawi HM and Vogel R. Notes on two sample tests for partially correlated (paired) data. Journal of Applied Statistics 2013; 41: 109–117. 8. Satterthwaite FE. An approxi
