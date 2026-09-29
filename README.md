# Improving Classification Accuracy in Corrupted ECG Signals: An Adaptive Filtering Approach

## Overview

Electrocardiogram (ECG) signals are widely used for the analysis and diagnosis of cardiovascular disorders. However, ECG recordings are often contaminated by noise, which can significantly affect signal quality and reduce the performance of machine learning-based classification systems.

This project investigates the effect of controlled noise on ECG classification and evaluates whether adaptive filtering techniques can recover classification performance from corrupted signals.

Controlled noise ranging from **+10 dB to -10 dB** was introduced into ECG signals under three different conditions:

1. Noise added to both training and testing data
2. Noise added to training data only
3. Noise added to testing data only

Multiple machine learning classifiers were evaluated under these conditions, followed by the application of adaptive filtering techniques for ECG denoising.

---

## Objectives

The main objectives of this project were to:

* Investigate the effect of noise on ECG classification accuracy.
* Compare the performance of different machine learning classifiers under noisy conditions.
* Evaluate adaptive filtering techniques for ECG signal denoising.
* Determine which filtering technique provides the greatest improvement in classification performance.
* Analyze the robustness of ECG classification systems under different noise distributions between training and testing data.

---

## Machine Learning Models

The following classification algorithms were evaluated:

* Decision Tree
* Discriminant Analysis
* Naive Bayes
* K-Nearest Neighbors (KNN)
* Ensemble Methods
* Neural Network

Among the evaluated models, **Neural Networks, Decision Trees, and K-Nearest Neighbors** demonstrated the most consistent classification performance across the tested noise conditions.

---

## Adaptive Filtering Techniques

Five adaptive filtering approaches were investigated for ECG denoising:

* Wiener Filter
* Least Mean Squares (LMS)
* Recursive Least Squares (RLS)
* Steepest Descent Filter
* Kalman Filter

The filters were applied to noisy ECG signals before classification to evaluate whether denoising could recover the classification performance lost due to noise.

---

## Experimental Setup

Noise was introduced at signal-to-noise ratios (SNRs) ranging from **+10 dB to -10 dB**.

Three experimental scenarios were considered:

### Scenario 1 — Noise in Training and Testing Data

Both the training and testing ECG signals were corrupted with controlled noise.

### Scenario 2 — Noise in Training Data Only

Noise was introduced into the training data while the testing data remained clean.

### Scenario 3 — Noise in Testing Data Only

The training data remained clean while noise was introduced into the testing data.

This setup allowed the effect of different training/testing noise distributions to be investigated.

---

## Results

In the absence of noise, the Neural Network classifier achieved an accuracy of **75.7%**.

At **-10 dB**, the accuracy decreased to:

| Condition                   | Accuracy |
| --------------------------- | -------: |
| Noise in training & testing |    60.0% |
| Noise in training only      |    60.0% |
| Noise in testing only       |    72.7% |

The results demonstrate that severe noise can substantially reduce ECG classification performance, particularly when the training data is corrupted.

### Performance After Kalman Filtering

After applying Kalman-filter-based denoising, the Neural Network achieved:

| Condition                   | Before Filtering | After Kalman Filtering |
| --------------------------- | ---------------: | ---------------------: |
| Noise in training & testing |            60.0% |                  72.7% |
| Noise in training only      |            60.0% |                  78.7% |
| Noise in testing only       |            72.7% |                  75.7% |

The Kalman filter produced the greatest improvement among the evaluated adaptive filtering techniques.

Across the noisy conditions, Kalman-filter-based denoising improved classification accuracy by an average of approximately **11.5 percentage points**, with the largest improvement of **18.7 percentage points** observed when noise was introduced into the training data only.

---
### Arrhythmia ECG

<img width="460" height="245" alt="dsdfs" src="https://github.com/user-attachments/assets/67fc4f91-36cf-4a96-826c-1d84d368fd47" />


### Congestive Heart Failure (CHF) ECG

<img width="465" height="248" alt="noisy signal" src="https://github.com/user-attachments/assets/b41a457f-7651-4beb-b4c6-e6568af3ff01" />


### Normal Sinus Rhythm (NSR) ECG

<img width="458" height="253" alt="clean" src="https://github.com/user-attachments/assets/44bc5e76-be45-44e8-a506-d198a92d864f" />

## Methodology

The overall workflow of the project was:

```text
ECG Dataset
     |
     v
Preprocessing
     |
     v
Controlled Noise Injection
(+10 dB to -10 dB)
     |
     +-----------------------------+
     |                             |
     v                             v
Noisy ECG Signals          Clean ECG Signals
     |                             |
     v                             |
Adaptive Filtering                |
     |                             |
     +-------------+---------------+
                   |
                   v
        Feature Extraction /
        Classification
                   |
                   v
       Machine Learning Models
                   |
                   v
        Accuracy Evaluation
                   |
                   v
       Comparative Analysis
```

---

## Key Findings

The experiments showed that:

* Increasing noise levels can significantly reduce ECG classification accuracy.
* Classification performance depends on whether noise is introduced into the training data, testing data, or both.
* Neural Networks, Decision Trees, and KNN showed relatively stable performance compared with the other evaluated classifiers.
* Adaptive filtering can recover a substantial portion of the classification performance lost due to noise.
* Among the five evaluated filtering approaches, the **Kalman filter provided the greatest improvement in classification accuracy** in the conducted experiments.

---

## Technologies Used

* MATLAB
* Machine Learning
* Digital Signal Processing
* ECG Signal Processing
* Adaptive Filtering
* Neural Networks

---

## Project Structure

```text
adaptive-filtering-ecg-classification/
│
├── data/
│   └── README.md
│
├── preprocessing/
│   ├── preprocessing.py
│   └── noise_generation.py
│
├── filters/
│   ├── wiener_filter.py
│   ├── lms_filter.py
│   ├── rls_filter.py
│   ├── steepest_descent.py
│   └── kalman_filter.py
│
├── models/
│   ├── decision_tree.py
│   ├── knn.py
│   ├── naive_bayes.py
│   ├── neural_network.py
│   └── ensemble.py
│
├── experiments/
│   ├── noise_experiments.py
│   └── filtering_experiments.py
│
├── results/
│   ├── figures/
│   └── tables/
│
├── notebooks/
│   └── ECG_Analysis.ipynb
│
├── requirements.txt
└── README.md
```

---

## Conclusion

This project demonstrates the impact of noise on machine learning-based ECG classification and investigates adaptive filtering as a method for improving robustness.

The experimental results indicate that **Kalman filtering can substantially improve classification accuracy for corrupted ECG signals**, particularly under severe noise conditions. The findings highlight the potential of combining digital signal processing techniques with machine learning to improve the reliability of automated ECG analysis systems.

## Research Focus

This project combines three areas:

**Digital Signal Processing + Machine Learning + Biomedical Signal Analysis**

and explores how signal-processing techniques can improve the reliability of machine learning models when working with noisy physiological signals.


