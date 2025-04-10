# 🧠 Cybersecurity Intrusion Detection Using ANN and Machine Learning Models

## 📁 Project Overview
The goal of this project is to detect cyber intrusions within a network using both traditional machine learning models and Artificial Neural Networks (ANNs). By analyzing labeled data of network activity, the project explores the classification performance of several models to identify the most suitable method for effective intrusion detection.

## 📊 Dataset Details
**Source:** `cybersecurity_intrusion_data.csv`

**Target Variable:** `attack_detected` (binary – 1 for intrusion, 0 for no intrusion)

**Features:** A mix of numerical and categorical variables including:
- `protocol`
- `service`
- `flag`
- `encryption_used`
- Various numerical network statistics

## 🔧 Preprocessing Steps
1. Dropped the `session_id` column as non-informative
2. Handled missing values using mode imputation
3. Encoded categorical variables using `LabelEncoder`
4. Standardized numerical features using `StandardScaler`

## ⚙️ Methodology

### 1. Data Preparation
- Loaded dataset using pandas
- Cleaned data by:
  - Removing irrelevant columns
  - Imputing missing values
  - Applying Label Encoding on categorical features
  - Standardizing numerical columns

### 2. Data Splitting
Used `train_test_split()` to create:
- 80% training data
- 20% testing data

## 🤖 Machine Learning Models Compared
Three traditional models were trained and evaluated:

| Model                | Final Test Accuracy (%) |   F1-Score   | Notes                                      |
|----------------------|-------------------------|--------------|--------------------------------------------|
| Decision Tree        | 83.38                   | 81.70        | Fast training but high risk of overfitting |
| Logistic Regression  | 74.58                   | 70.48        | Good for linearly separable data           |
| SVM                  | 88.10                   | 85.38        | Robust, good for non-linear data           |

## 🧠 Artificial Neural Network (ANN)
Built using Keras with hyperparameter tuning.

### 🔨 Architecture:
- **Input Layer:** Neurons = number of features
- **Hidden Layers:**
  - Varied configurations (1-2+ layers)
  - Swish activation
  - Dropout and Batch Normalization
- **Output Layer:**
  - Single neuron with sigmoid activation
    
### Model Architectures Tested:
1. **ANN Without Dropout**
   - Plain feedforward network
   - Risk of overfitting on training data
#### 🔍 Problem Identified
The initial ANN model **without dropout** showed clear signs of overfitting:

| Metric               | Training Data | Validation Data | Gap    |
|----------------------|---------------|-----------------|--------|
| Accuracy             | 98.99%        | 82.1%           | +16.8% |

2. **ANN With Dropout (0.2-0.5 rate)**
   - Added Dropout layers between hidden layers
   - Better generalization to unseen data
     
| Metric               | Training Data | Validation Data | Gap    |
|----------------------|---------------|-----------------|--------|
| Accuracy             | 89.7%         | 88.89%          | 0.81%  |  

✅ **Key Improvements with Dropout**
- Reduced overfitting gap from 16.8% → 0.81%
- More stable validation performance
- Better generalization to unseen attack patterns
     
### 🧪 Hyperparameters Tuned:
- Batch Size: 16, 32, 64, 128, 256
- Optimizer: Adam, SGD, RMSprop, Adagrad
- Epochs: 300 

## 📈 Model Evaluation Metrics
All models evaluated using:
- Training Accuracy
- Validation Accuracy

## 📊 Final Accuracy Comparison

| Model                         | Validation Accuracy (%) | Optimizer Used | Notes                              |
|-------------------------------|-------------------------|----------------|------------------------------------|
| Decision Tree Classifier      | 83.38                   | N/A            | Fast but risk of overfitting       |
| Logistic Regression           | 74.58                   | N/A            | Good for linear problems           |
| SVM                           | 88.10                   | N/A            | Effective but slower               |
| ANN (Adam Optimizer)          | 88.89                   | Adam           | Best accuracy ✅                   |
| ANN (RMSprop Optimizer)       | 88.78                   | RMSprop        | Slightly behind Adam               |
| ANN (SGD Optimizer)           | 83.60                   | SGD            | Lower performance                  |
| ANN (Adagrad Optimizer)       | 85.48                   | SGD            | Lower performance, Underfitting    |

## 📦 Batch Size vs Accuracy (ANN Comparison)

| Batch Size | Validation Accuracy (%) | Notes                              |
|------------|-------------------------|------------------------------------|
| 16         | 85.48                   | Slower and underfitting            |
| 32         | 87.68                   | Lower Accuracy, less stable        |
| 64         | 88.21                   | Slight dip, underfitting           |
| 128        | 88.57                   | Faster but less stable             |
| 256        | 88.85                   | Fastest, higher accuracy           |

## 📌 Conclusion
The study demonstrates that:
1. **ANNs outperform traditional ML models with accuracy of 88.89%** for intrusion detection when properly tuned
2. **Adam optimizer achieved highest accuracy (88.85%)**
3. **Batch size 256 provided optimal balance** between speed and accuracy
4. ANN's ability to model complex relationships makes it ideal for cybersecurity applications
