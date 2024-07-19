# ML Algorithm Training Methodology

# First Pass

## Total List of Features(Peptide Descriptors) in the Dataset:

(see file "peptide_features.csv")

"Length, MW, Charge, ChargeDensity, pI, InstabilityInd, Aromaticity, AliphaticInd, BomanInd, HydrophRatio, max/mean moment, global descriptor, autocovariance, BLOSUM1, BLOSUM2, BLOSUM3, BLOSUM4, BLOSUM5, BLOSUM6, BLOSUM7, BLOSUM8, BLOSUM9, BLOSUM10, A, R, N, D, C, Q, E, G, H, I, L, K, M, F, P, S, T, W, Y, V, O, U, B, Z, J, X, crosscovariance, pp1, pp2, pp3, F1, F2, F3, F4, F5, F6, Afreq, Rfreq, Nfreq, Dfreq, Cfreq, Qfreq, Efreq, Gfreq, Hfreq, Ifreq, Lfreq, Kfreq, Mfreq, Ffreq, Pfreq, Sfreq, Tfreq, Wfreq, Yfreq, Vfreq, Ofreq, Ufreq, Bfreq, Zfreq, Jfreq, Xfreq, autocorrelation, cross covariance, AboderinHydrophobicity, AbrahamLeoHydrophobicity, K1, K2, K3, K4, K5, K6, K7, K8, K9, K10, mswhim1, mswhim2, mswhim3, E1, E2, E3, E4, E5"

## Number of Features: 107

### Features Selected for Classification Model (10):

(see file "selectedfeatureset.csv")

'BLOSUM1', 'BomanInd', 'F1', 'E1', 'K4', 'pp1', 'global descriptor', 'AbrahamLeoHydrophobicity', 'AboderinHydrophobicity', 'HydrophRatio'

### Optimization Techniques Used:

Cross Validation to ensure equal presence of both classes of data in the training and testing data
Shuffling data to induce randomness for better classification
Oversampling of data to reduce any class imbalance
Feature selection to create the most effective algorithm for classification (see file "Feature Importance Plot.png" for feature importance ranking).  

## Winning Classification Algorithm: Quadratic Discriminant Analysis

Details: Without Cross Validation

Best Iteration: 4-Fold Cross Validation (see file "Results.png")

Performance Metrics:


Recall: 78.19%
AUC Score: 71.01%
F1 Score: 69.67%
Precision: 62.82%


# Second Pass

## Total List of Selected Features (Peptide Descriptors) in the Dataset:

(see file "selectedfeatureset4.csv")

['BomanInd', 'Cfreq', 'Charge', 'W', 'BLOSUM1', 'MW', 'Yfreq', 'Efreq', 'mswhim2', 'Mfreq', 'Nfreq', 'Aromaticity', 'Dfreq', 'F3', 'H', 'Qfreq', 'L', 'Ifreq', 'Kfreq', 'BLOSUM4', 'BLOSUM6', 'Ffreq', 'Gfreq', 'Tfreq', 'Vfreq', 'Sfreq']

## Number of Features: 26


### Feature Selection Method Used:
​This time around I tried the SULOV (Search for Uncorrelated List Of Variables) method (see file 'SULOV Method.png'), which removes highly correlated features in the dataset. This removes confusion and ambiguity when relating features with the label (in our case the hemolytic/non-hemolytic category).

## Classification Optimization Techniques Used:

Cross Validation to ensure equal presence of both classes of data in the training and testing data
Shuffling data to induce randomness for better classification
Oversampling of data to reduce any class imbalance
Feature selection through SULOV to create the most effective algorithm for classification (see file "Feature Importance Plot.png" for feature importance ranking).  

## Winning Classification Algorithms:
​
### 1. Light Gradient Boosting Classifier

Best Iteration: 1-Fold Cross Validation
Performance Metrics:


Accuracy: 84.85%
Recall: 84.68%
AUC Score: 92.21%
F1 Score: 84%
Precision: 83.33%


### 2. Gradient Boosting Classifier
​Best Iteration: Tuned Model with early stopping, 1-Fold Cross Validation

Performance Metrics:


Accuracy: 84.47%
Recall: 86.29%
AUC Score: 91.38%
F1 Score: 83.92%
Precision: 81.68%


### 3. Extra Trees Classifier

Details: With Cross Validation

Best Iteration: 9-Fold Cross Validation

Performance Metrics:


Accuracy: 85.55%
Recall: 82.93%
AUC Score: 89.29%
F1 Score: 84.30%
Precision: 85.71%


### 4. Random Forest Classifier

Details: With Cross Validation

Best Iteration: 4-Fold Cross Validation

Performance Metrics:


Accuracy: 85.61%
Recall: 80.49%
AUC Score: 91.42%
F1 Score: 83.90%
Precision: 87.61%

Progress Made Since the First Pass:

If you contrast these results with the previous ones, there is a marked improvement. The first pass yielded performance metric values barely crossing the 70% threshold. This time, we are comfortably getting results in the 80-90% threshold.

This is also evident when we observe the decision boundaries for all the algorithms (see files with the suffix 'Decision Boundary.png'). There is a much clearer decision boundary forming here than with the previous data set.

Further Proposals

I propose that we can get even better results if we get more data, and, as you informed earlier, less overlapping data. This will help the classification algorithms better understand the parameters they need to tune to get near 100% accuracy. I believe we can do further data augmentation and optimization to get better results with this data.

I can help with the extraction of data if I can get the names of different sources as well.

I believe we have made good progress and can expect much better results in the future.

Once we have pushed the classification performance to comfortably over 90-95%, I can construct a program that will automatically classify any peptide and we can put that tool online.
