# 1. Introduction
# 2. Related work
## 2.1. The unreasonable effectiveness of random neural networks
- Random neural network is
    - all or some of the connections are left untrained after their random initialization.
- This allows
    - efficient training process, (compared to fully trained architectures)
    - extracting useful feature representations
- There are different hypotheses on how random neural networks can extract useful information
    1. connections with kernel machines and Gaussian processes [13]
    2. effect of random transformations in metric space [14]
        - random NN increasing the angles of the points from the different classes.
- History
    - Single hidden
        - RVFLs (Random Vector Functional-links)
        - the weighted sum of randomly extracted features and then optimized by l2 regularized least squares.
    - Deeper architectures (multiple layers)
        - insight of a deep NN in the initial stages of training
        - The effect of the architecture in performance. (since the weights are untrained)
        - CNN can extract enough structural information to perform image denosing, image classification [22, 23] etc.
    - Random projections for anomaly detection tasks [9, 30-33]
## 2.2. Sparsity in neural networks
- In this paper, the high sparsity rate of the neural networks is important features.
- Sparsity gives efficiency in computational cost.
## 2.3. Online anomaly detection.
- Neural network based approaches typically outperform other approaches, especially on rich input data (images, audio, vide) [51]. The most common approaches are base pm deep variational autoencoders, Generative Adversarial Networks or Transformers.
    - But very high computational cost.
- The author is more interested in the continuous learning for edge device.

# 3. Approach
- Process of calculating anomaly score;
![Untitled](https://github.com/juyeon999/Paper_review/assets/132811616/478572bf-4479-43bb-8acd-53a9d4732126)  
- Meaning of random weights
    - The sparse random neural network **projects the input datapoint to a high dimensional feature space**. Even though the weights of the neural network are initialized randomly, this transformation improves the separability of the input data [14].
- Method of making random weights (= the way of initializing the nn)
    - Randomly: $\sim Unif(-1, 1)$
    - Sparsity: $\sim Bernoulli(p)$

# 4. Experiments
## Setting
### Benchmark dataset
- MNIST, FashionMNIST, CIFA10
### Preprocessing
- Common methodology in anomaly detection literature. Since each dataset contains then labeled classes,
- Train: Normal (one class)
- Test:  Normal (one class) + Abnormal (from other classes)
### Detailed model architecture
- For the bigger dataset, CIFAR10, use more neurons per layer.
![Untitled (1)](https://github.com/juyeon999/Paper_review/assets/132811616/93ffcdf0-bbb6-4080-a685-1c1e6e54377d)
## 4.1. Anomaly detection performance
- Performance on general case; train only normal case and test normal and abnormal cases.
- Comparison targets:
    - Baseline approaches: Local Outlier factor (LOF), Isolation Forests (IF), One-Class SVMs (OC-SVM) and PCA(?)
    - SOTA approaches: GAN, VAE etc based Deep learning models
- This method obtains anomaly detection performance that is comparable to the baseline methods and SOTA deep learning based approaches.
## 4.2. Impact of sparsity and layer size
- Sensitive analysis for hyperparams which are sparsity and layer size.
- False positivity have a large impact on anomaly detection systems since they typically require further analysis by a human expert.
- First, larger layer size increase the networks capacity to extract features from the data.
- Second, the sparsity rate however has a more complex relation with the final AUC score.
    - as the layer size increase, we can see that the model can tolerate a higher sparsity rate. **⇒ DPNN과는 다른 의미로!!**
## 4.3. Online learning
- Time cost
## 4.4. Robustness against noisy training data
- Sensitive analysis for contamination of data itself.
- Result
    - As expected the anomaly detection performance decreases as the frequency of anomalous samples in the training data increases.
    - **Not all methods are equally sensitive however.**
- As fraction of noise training samples increase, the performance still consistency then they have robustness.
## 4. 5. Performance in the limited data setting
- Limitation in data size

# 5. Evaluation on higher resolution data
# 6. Evaluation on time series data
# 7. Conclusion and future work

# References
**Random CNN in image classification**

[13] A. Daniely, R. Frostig, Y. Singer, Toward deeper understanding of neural networks: The power of initialization and a dual view on expressivity, Adv. Neural Inf. Process. Syst. 29 (2016).

[14] R. Giryes, G. Sapiro, A.M. Bronstein, Deep neural networks with random Gaussian weights: A universal classification strategy? IEEE Trans. Signal Process. 64 (13) (2016) 3444–3457.

**Random projection**

[30] M. Bauw, S. Velasco-Forero, J. Angulo, C. Adnet, O. Airiau, Deep random projection outlyingness for unsupervised anomaly detection, 2021, arXiv preprint arXiv:2106.15307.
[31] P. Navarro-Esteban, J.A. Cuesta-Albertos, High-dimensional outlier detection using random projections, TEST 30 (4) (2021) 908–934.
[32] S.M. Erfani, M. Baktashmotlagh, S. Rajasegarar, S. Karunasekera, C. Leckie, R1SVM: a randomised nonlinear approach to large-scale anomaly detection, in: Proceedings of the AAAI Conference on Artificial Intelligence, Vol. 29, No. 1, 2015.
[33] T. de Vries, S. Chawla, M.E. Houle, Density-preserving projections for large-scale local anomaly detection, Knowl. Inf. Syst. 32 (1) (2012) 25–52
