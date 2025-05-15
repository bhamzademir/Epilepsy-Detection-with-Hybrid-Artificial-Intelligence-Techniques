# 🧠 Epilepsy Detection with Hybrid Artificial Intelligence Techniques

![EEG Banner](images/eeg_banner.png)

> A hybrid machine learning pipeline for automatic epileptic seizure detection using EEG signals and advanced feature engineering techniques.

---

## 📌 Table of Contents

- [Abstract](#abstract)
- [Methodology](#methodology)
  - [Signal Processing](#signal-processing)
  - [Feature Extraction & Normalization](#feature-extraction--normalization)
  - [Feature Selection](#feature-selection)
  - [Model Training & Evaluation](#model-training--evaluation)
- [Results](#results)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [How to Run](#how-to-run)
- [Project Structure](#project-structure)
- [Citation](#citation)

---

## 🧬 Abstract

Epilepsy is a neurological disorder caused by abnormal brain activity. Early and accurate detection of epileptic seizures significantly improves patients' treatment processes. This project presents a hybrid AI-based system that processes EEG signals using wavelet transforms, extracts robust statistical features, applies advanced feature selection methods, and classifies seizure patterns using various ML/DL models.

📚 **Keywords:** Signal Processing, Feature Engineering, AI Techniques, EEG, Epileptic Seizure Detection

---

## 🧪 Methodology

### 🔹 Signal Processing
- **Dataset:** [University of Bonn EEG Dataset](https://epileptologie-bonn.de/cms/front_content.php?idcat=193&lang=3)
- **Technique:** Stationary Wavelet Transform (SWT)
- **Parameters Tuned:**
  - Window sizes: `256`, `512`, `1024`
  - Wavelets: `haar`, `db5`, `sym6`
  - Decomposition levels: `1-5`

### 🔹 Feature Extraction & Normalization
- Extracted 20+ statistical features from each signal:
  - Mean, Std, Entropy, Energy, Skewness, Kurtosis, RMS, L1/L2 Norms, ZCR, etc.
- Features normalized using **Min-Max scaling** to [0,1]

### 🔹 Feature Selection
Applied four selection techniques:
- RFE (Wrapper)
- mRMR (Filter)
- PCA (Dim. Reduction)
- ICA (Component Decomposition)

### 🔹 Model Training & Evaluation
- Models used: `SVM`, `Random Forest`, `Logistic Regression`, `ANN`, `LSTM`, `XGBoost`, `Gradient Boost`, `Decision Trees`
- Hyperparameter tuning with **GridSearchCV**
- Evaluation metrics:
  - Accuracy, Precision, Recall, F1, AUC, Specificity, Sensitivity

---

## 📈 Results

| Model            | Feature Selector | Accuracy (%) | Wavelet | Window Size | Level |
|------------------|------------------|--------------|---------|--------------|--------|
| SVM              | ICA              | 98.9         | haar    | 1024         | 3      |
| Random Forest    | RFE              | 98.7         | haar    | 1024         | 4      |
| Logistic Regression | PCA           | 96.5         | haar    | 1024         | 3      |
| ANN              | ICA              | 98.5         | haar    | 1024         | 4      |
| XGBoost          | mRMR             | 99.33        | haar    | 256          | 3      |
| LSTM             | RFE              | 97.4         | db5     | 256          | 3      |
| Decision Trees   | mRMR             | 94.1         | haar    | 1024         | 4      |

📊 Detailed comparisons can be found in `results/performance_summary.xlsx`

---

## 🔍 Key Findings

- Best overall performance: **XGBoost with mRMR-selected features** (99.33%)
- Wavelet type `haar` and window size `1024` were optimal in most cases.
- `RFE` and `mRMR` perform best with fewer features, while `PCA`/`ICA` outperform as feature count increases.
- Simple models like **Logistic Regression** still yield strong results with less complexity.

---

## 🛠️ Technologies Used

| Category        | Stack                                         |
|-----------------|-----------------------------------------------|
| Languages       | Python                                        |
| Libraries       | NumPy, Pandas, Scikit-learn, XGBoost, Keras   |
| Tools           | Jupyter Notebook, Matplotlib, Seaborn         |
| Concepts        | Wavelet Transform, Feature Selection, ML, DL  |

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/bedirhan23/epilepsy-detection-hybrid-ml.git
cd epilepsy-detection-hybrid-ml

# Install required packages
pip install -r requirements.txt

# Run pipeline (example)
python src/train_model.py --model xgboost --feature_method mrmr --wavelet haar --window_size 256 --level 3

📖 Citation
Demir, H., et al. (2024, Nov). Comparing Performances of Different ML Algorithms Based on Feature Selection Techniques for Epileptic Seizure Detection. ODSIE 2024, Istanbul, Turkey.

🙌 Acknowledgments
This project is funded by TÜBİTAK, The Scientific and Technological Research Council of Turkey.

