# 🧠 Cybersecurity Intrusion Detection Using ANN and Machine Learning Models

## 📁 Project Overview

The project seeks to identify cyber intrusions within a network through different machine learning models, such as Artificial Neural Networks (ANN). The models are trained on a labeled dataset of the network's activity and compared based on their performance measures. The overall aim is to determine the most suitable model for effective intrusion detection.

---

## 📊 Dataset

- **Source:** CSV file (assumed to be pre-downloaded).
- **Target Variable:** `attack_detected` – Binary label indicating presence or absence of intrusion.
- **Features:** Mixture of numerical and categorical variables, including `protocol`, `service`, `encryption_used`, etc.
- **Preprocessing:**
  - Dropped the `session_id` column (non-informative).
  - Imputed missing values using mode.
  - Applied Label Encoding to categorical variables.
  - Used StandardScaler to normalize numerical features.

---

## ⚙️ Methodology

### 1. **Data Preparation**
- Loaded the CSV into a Pandas DataFrame.
- Identified and filled missing values.
- Encoded categorical variables using `LabelEncoder`.
- Scaled numeric columns with `StandardScaler`.

### 2. **Data Splitting**
- Used `train_test_split()` to create an 80/20 split for training and testing.

### 3. **Machine Learning Models Used**
- **Decision Tree Classifier**
- **Logistic Regression**
- **Support Vector Machine (SVM)**

These models were trained on the same dataset and evaluated using common performance metrics.

### 4. **Artificial Neural Network (ANN)**
- Built using **Keras Sequential API**.
- Different configurations (hidden layers, batch sizes, optimizers) were experimented with.
- Plots were generated to visualize the accuracy trend across training epochs.
- Hyperparameter tuning was performed on:
  - **Batch size**
  - **Optimizers**: `Adam`, `SGD`, `RMSprop`, etc.

---

## 📈 Model Evaluation

### Metrics Considered:
- **Training Accuracy**
- **Validation Accuracy**
- **F1-score**

### Comparison Approach:
- Trained all models on the same dataset split.
- Compared their performance visually using plots and programmatically via accuracy scores.
- Best ANN model selected based on maximum validation accuracy.

---

## ✅ Results Summary

| Model               | Performance Notes                         |
|---------------------|-------------------------------------------|
| Decision Tree       | Quick to train but can overfit            |
| Logistic Regression | Good baseline, limited on non-linear data |
| SVM                 | Performs well with right kernel, slower   |
| ANN (Keras)         | Tunable, best results with optimizer tuning and batch size variation |

---

## 📌 Conclusion

The project demonstrates that **ANNs**, when properly tuned, can outperform traditional machine learning models for cybersecurity intrusion detection. The flexibility of deep learning models allows them to learn complex patterns in data, which is especially useful in high-dimensional cybersecurity datasets.

---
