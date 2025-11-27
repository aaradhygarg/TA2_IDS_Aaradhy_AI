# NSL-KDD Intrusion Detection — Full Training & Evaluation Pipeline

This project builds a complete intrusion-detection pipeline using the **NSL-KDD dataset** (KDDTrain+ / KDDTest+).  
It preprocesses the dataset, trains multiple machine-learning models, evaluates them, and saves all artifacts (models, plots, scalers, encoders) for later use.

---

## 📌 Features
- Automatic detection of dataset files (`KDDTrain+.txt`, `KDDTest+.txt`, or `.csv`)
- Preprocessing:
  - Binary label mapping (`normal` vs `attack`)
  - One-hot encoding for categorical features (`protocol_type`, `service`, `flag`)
  - Scaling numeric features with `StandardScaler`
  - Label encoding (`LabelEncoder`)
- Training:
  - Logistic Regression  
  - Random Forest  
  - Optional XGBoost (if installed)
- Evaluation:
  - Classification report  
  - Confusion matrix (saved as PNG)  
  - ROC curve + AUC score  
- Artifacts saved to `/content/out`:
  - Trained models (`.joblib`)
  - Plots (`.png`)
  - Preprocessors (`scaler.joblib`, `label_encoder.joblib`)

---

## 📂 Project Structure
