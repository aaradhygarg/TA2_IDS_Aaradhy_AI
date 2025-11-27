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
/content/
├── KDDTrain+.txt
├── KDDTest+.txt
├── your_script.py
└── out/
├── model_logistic.joblib
├── model_random_forest.joblib
├── model_xgboost.joblib (if installed)
├── scaler.joblib
├── label_encoder.joblib
├── confusion_<model>.png
└── roc_<model>.png


---

## 🛠 Requirements

Install required dependencies (for Google Colab):

``bash
!pip install pandas numpy scikit-learn matplotlib seaborn joblib xgboost --quiet


For Kaggle download:

!pip install kaggle --quiet

📥 Downloading the Dataset (NSL-KDD) — Kaggle Method

Upload your kaggle.json to Colab:

from google.colab import files
files.upload()


Configure Kaggle:

!mkdir -p ~/.kaggle
!mv kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json


Download NSL-KDD:

!kaggle datasets download -d hassan06/nslkdd
!unzip nslkdd.zip


The dataset files (KDDTrain+.txt, KDDTest+.txt) should now be in your working directory.

▶️ Running the Script

Run your .py file in Colab:

!python your_script.py


Or copy the entire script to a Colab cell and execute it.

The script will:

Load dataset

Preprocess features

Train models

Save confusion matrices & ROC curves

Save trained models and scalers

All outputs will be stored in:

/content/out

📊 Results & Outputs

For each model, you will get:

Classification Report (printed)

Confusion Matrix → saved as:
confusion_logistic.png, confusion_random_forest.png, ...

ROC Curve + AUC → saved as:
roc_logistic.png, roc_random_forest.png, ...

Serialized model → model_<name>.joblib

These files can be downloaded or copied to Google Drive.

💾 Saving Outputs to Google Drive (Optional)

Uncomment and run inside your script:

from google.colab import drive
drive.mount('/content/drive')
!cp -r /content/out /content/drive/MyDrive/

⚠️ Common Issues
❌ SyntaxError: invalid syntax when installing packages

In Colab, all pip installs must start with !

✅ Correct:

!pip install pandas


❌ Wrong:

pip install pandas

❌ FileNotFoundError: KDDTrain+.txt not found

Place the dataset files in the same directory, or re-run the Kaggle download.

Check with:

!ls

🚀 Improvements to Try

Use Pipeline + ColumnTransformer to combine preprocessing + model

Handle class imbalance using:

class_weight='balanced'

SMOTE / undersampling

Try better models:

Gradient boosting (XGBoost, LightGBM, CatBoost)

Use feature importance or SHAP explainability

Reduce dimensionality using PCA or hashing for service column
