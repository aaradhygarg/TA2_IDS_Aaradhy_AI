# Intrusion Detection System — Full Training & Evaluation Pipeline

A complete and end-to-end machine-learning pipeline built using the **NSL-KDD Intrusion Detection Dataset**.  
This project loads the NSL-KDD dataset (KDDTrain+ / KDDTest+), preprocesses it, trains multiple ML models, evaluates their performance, and saves all relevant artifacts.

---

## 📌 Features
- Automatic dataset detection
- Binary label mapping (normal vs attack)
- One-hot encoding for categorical columns
- StandardScaler + LabelEncoder
- Training Logistic Regression, Random Forest, optional XGBoost
- Confusion matrices & ROC curves
- All artifacts saved to `/content/out`

---

## 📂 Project Structure
/content/

├── KDDTrain+.txt  
├── KDDTest+.txt  
├── TA2_AI_IDS.ipynb  
└── out/  
    ├── model_logistic.joblib  
    ├── model_random_forest.joblib  
    ├── model_xgboost.joblib (optional)  
    ├── scaler.joblib  
    ├── label_encoder.joblib  
    ├── confusion_<model>.png  
    └── roc_<model>.png  

---

## 🛠 Requirements
```bash
!pip install pandas numpy scikit-learn matplotlib seaborn joblib xgboost --quiet
```

For Kaggle:
```bash
!pip install kaggle --quiet
```

---

## 📥 Downloading Dataset (Kaggle)
Upload kaggle.json:
```python
from google.colab import files
files.upload()
```

Configure:
```bash
!mkdir -p ~/.kaggle
!mv kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

Download:
```bash
!kaggle datasets download -d hassan06/nslkdd
!unzip nslkdd.zip
```

---

## ▶️ Running the Script
```bash
!python TA2_AI_IDS.ipynb
```

Outputs saved in `/content/out`.

---

## 📊 Results
- Classification reports  
- Confusion matrices  
- ROC curves + AUC  
- Saved models (`.joblib`)

---

## 💾 Save to Google Drive
```python
from google.colab import drive
drive.mount('/content/drive')
!cp -r /content/out /content/drive/MyDrive/
```

---

## 🚀 Improvements
- Pipelines & ColumnTransformer  
- SMOTE / class balancing  
- PCA or feature selection  
- SHAP or feature importance  
- More models (LightGBM, CatBoost)

---

## 📘 License
For academic & research use only.

---
