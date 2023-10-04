# Deep isolation forest for anomaly detection
Xu, Hongzuo, et al. "Deep isolation forest for anomaly detection." *IEEE Transactions on Knowledge and Data Engineering* (2023).

## 1. 기본 컨셉
Deep isolation forest
DIF constructs an ensemble of representations derived from deep neural networks, and simple axis-parallel isolation is operated upon new data spaces to build iTrees in the forest. 
Instead of following the deep ensemble framework that combines independently trained neural networks, we use an ensemble of random representations produced by optimisation-free neural networks that only require simple casual initialisation. 
Each feature in the newly projected representation space is based on non-linear interactions among a number of original features, meaning that axis-parallel partitions of new space can form effective non-linear cuts in the original space.

## 2. 문제
iForest가 axis-parallel하가 partitioning해서 particularly on datasets with high-dimensional/non-linearseparable data spaces에서는 high false negative error 보임  
<img width="516" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/96284327-d105-4ff8-b0ef-1de3f0c8cb8a">
        
## 3. 해결
The key idea in DIF is to harness the strong representation power of neural networks to map the original data into a group of new data spaces, 
and non-linear isolation can be easily achieved by performing simple axis-parallel partitions upon these newly created data spaces (equivalent to nonlinear partition on subspaces of varying sizes in the original data space).  
<img width="521" alt="image" src="https://github.com/juyeon999/Paper_review/assets/132811616/7c34a118-ed81-40f9-9b75-866790335d3f">
