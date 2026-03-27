# Prognostics and Health Management of Power Transformers (BMP Project)

## Overview
This project focuses on data-driven monitoring and fault diagnosis of power transformers using machine learning and statistical techniques. The objective is to identify anomalies, detect faults early, and improve transformer reliability.

I have primarily contributed to the following three major components:
1. Outlier Detection in Oil Temperature Data  
2. Fault Diagnosis using Rogers Ratio and Random Forest  
3. Data Preprocessing using Hampel Filter and Kalman Smoothing  

---

## 1. Outlier Detection (Oil Temperature Dataset)

### Objective
Detect abnormal operating conditions in transformers by analyzing oil temperature behavior relative to load patterns.

### Approach

#### Feature Engineering
- Load Magnitudes:
  - P_high, P_mid, P_low
- Rolling statistics:
  - 6h, 12h, 24h windows

#### Rare Load Detection (DBSCAN)
- Clustering used to identify rare operating states  
- Approximately 3.44% of data points detected as rare load conditions  

#### Expected Temperature Modeling
- Model: Ridge Regression  
- Best window: 24h  
- Metrics:
  - MAE ≈ 6.48  
  - R² ≈ 0.106  

#### Anomaly Definition
A point is considered anomalous if:
- It belongs to a rare load cluster (DBSCAN), and  
- It has high prediction residual  

### Results
- Rare Load Points: 599  
- High Residual Points: 856  
- True Anomalies: 15 (0.09%)

### Interpretation
- True anomalies may indicate degradation or abnormal operation  
- Model errors suggest seasonal drift or the need for retraining  

---

## 2. Fault Diagnosis (DGA Dataset)

### Objective
Classify transformer faults using Dissolved Gas Analysis (DGA).

### Feature Engineering
- Rogers Ratios:
  - R1 = C2H2 / C2H4  
  - R2 = CH4 / H2  
  - R3 = C2H4 / C2H6  
- Additional Feature:
  - TotalGas  


### Method 1: Rogers Ratio (Rule-Based)
- Classical threshold-based classification  
- Categories:
  - Partial Discharge (PD)  
  - Arcing  
  - Low, Medium, and High Temperature Overheating  

#### Limitation
- Many samples classified as "Unknown"  
- Hard thresholds limit flexibility  


### Method 2: Random Forest Classifier
- Model: Random Forest (200 trees)  
- Train-Test Split: 80/20 (Stratified)  
- Preprocessing: StandardScaler  

#### Performance
- Accuracy: 84.7%  
- Strong recall:
  - High Temperature Overheating: 100%  
  - Low Temperature Overheating: 95%  
- Weaker performance:
  - Partial Discharge: 67%  


### Comparison
| Method           | Accuracy | Coverage | Flexibility |
|------------------|----------|----------|-------------|
| Rogers Ratio     | 92.6%    | Low      | No          |
| Random Forest    | 84.7%    | High     | Yes         |

### Interpretation
- Rogers Ratio performs well when rules apply but lacks coverage  
- Random Forest provides better generalization across unseen data  

---

## 3. Data Preprocessing (Lancaster DGA Dataset)

### Objective
Clean noisy time-series data while preserving meaningful signals.


### Hampel Filter (Outlier Detection)
- Based on Median Absolute Deviation (MAD)  
- Outlier condition:
  |x - median| > nσ × 1.4826 × MAD


### Kalman Filtering Pipeline

#### Step 1: Detect Outliers
- Rolling Z-score (window = 25)  
- Threshold: |z| > 3.5  

#### Step 2: Replace Outliers
- Mark detected points as missing  
- Apply SARIMAX (AR(1) model)  
- Use Kalman smoothing to estimate corrected values  


### Evaluation Metrics
- Variance Reduction: Indicates noise suppression  
- Correlation (Original vs Corrected): Measures signal preservation  
