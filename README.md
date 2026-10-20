# Computational Modelling of Artificial Taste Perception Using Explainable Machine Learning

## 📌 Project Overview

This project aims to develop a computational taste-prediction system inspired by **Electronic Tongue (E-Tongue) technology**. It uses Machine Learning (ML) techniques to predict the taste profiles of chemical compounds from their SMILES molecular representations.

The system classifies compounds into five basic taste categories: **Sweet, Salty, Sour, Bitter, and Umami**. It also explores Explainable Artificial Intelligence (XAI) to help interpret the features influencing model predictions.

The project combines molecular feature extraction, machine learning, model evaluation, and an interactive application to demonstrate computational taste prediction.

## 🎯 Objectives

- Develop a machine-learning-based system for chemical taste prediction.
- Convert SMILES molecular representations into numerical molecular descriptors.
- Build separate classification models for five basic taste categories.
- Compare multiple machine learning algorithms and evaluate their performance.
- Explore Explainable AI using SHAP to understand model predictions.
- Provide an interactive interface for taste prediction and visualization.

## 🧪 Taste Categories

The system considers five basic taste categories:

- **Sweet** – associated with sweet-tasting compounds.
- **Salty** – associated with salty-tasting compounds.
- **Sour** – associated with acidic taste.
- **Bitter** – associated with bitter-tasting compounds.
- **Umami** – associated with savoury taste.

The model predicts taste-category scores for a chemical compound based on its extracted molecular features.

## ⚙️ Project Workflow

1. **Dataset Preparation:** Load and clean the chemical-taste dataset.
2. **Data Preprocessing:** Remove conflicting labels and duplicate molecular structures.
3. **Feature Extraction:** Convert SMILES strings into numerical descriptors using a custom SMILES featurizer.
4. **Model Development:** Train separate binary classifiers for the five taste categories.
5. **Algorithm Comparison:** Compare different classification algorithms using cross-validation.
6. **Model Evaluation:** Evaluate performance using ROC-AUC, accuracy, precision, recall, and F1-score.
7. **Explainable AI:** Explore SHAP-based feature explanations for model interpretability.
8. **Prediction:** Use the trained models to estimate taste-category probabilities for new SMILES inputs.
9. **Application:** Present predictions through the project's application interface.

## 🧠 Machine Learning Algorithms

The project compares the following algorithms:

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Random Forest
- Extra Trees
- Gradient Boosting
- HistGradientBoosting

Based on the recorded cross-validation ROC-AUC comparisons, **Random Forest** was selected for the five taste-category models.

## 📊 Dataset

The project uses a prepared chemical-taste dataset containing molecular SMILES representations and taste labels.

The dataset preparation process includes:

- Removing invalid or conflicting records.
- Removing duplicate canonical SMILES.
- Extracting numerical descriptors from molecular representations.
- Preparing separate binary labels for each taste category.

After preprocessing, the dataset contained **2,987 molecular records**.

The resulting class distribution is imbalanced, particularly for the Salty and Sour categories. Therefore, evaluation metrics such as recall, precision, and F1-score are important alongside accuracy.

## 🔬 Molecular Feature Extraction

A custom SMILES featurization script extracts 33 numerical descriptors from molecular representations. These include features related to:

- SMILES string length
- Atom counts and elemental composition
- Approximate molecular weight
- Bond counts and types
- Branches and ring structures
- Aromatic symbols
- Charges and elemental ratios

These descriptors are used as inputs to the trained machine learning models.

**Note:** The current implementation uses custom, approximate descriptors rather than a complete RDKit-based molecular fingerprint pipeline.

## 📈 Model Evaluation

The following table presents the recorded cross-validation results for the selected Random Forest models.

| Taste Category | ROC-AUC | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|---:|
| Salty | 0.989 | 0.995 | 0.667 | 0.250 | 0.364 |
| Sweet | 0.945 | 0.879 | 0.858 | 0.825 | 0.841 |
| Umami | 0.970 | 0.964 | 0.793 | 0.695 | 0.741 |
| Bitter | 0.931 | 0.860 | 0.867 | 0.860 | 0.863 |
| Sour | 0.961 | 0.986 | 0.625 | 0.306 | 0.411 |

*These are recorded cross-validation results, not guaranteed performance on unseen real-world samples.*

The high accuracy values for Salty and Sour should be interpreted carefully because these categories contain relatively few positive examples. Their low recall and F1-scores indicate that the models miss a substantial proportion of positive examples.

## 💡 Explainable AI (XAI)

The project explores **SHAP (SHapley Additive exPlanations)** to help explain the contribution of input features to model predictions.

SHAP can help investigate:

- Which molecular descriptors influence a prediction.
- How individual features contribute to a model output.
- How model behaviour can be interpreted beyond a predicted label.

The availability of explanations depends on the installed dependencies and the successful execution of the SHAP analysis.

## 🛠️ Technologies Used

- **Programming Language:** Python
- **Machine Learning:** Scikit-learn
- **Data Processing:** Pandas, NumPy
- **Model Persistence:** Joblib / Pickle
- **Explainable AI:** SHAP
- **Application Interface:** Streamlit
- **Data Visualization:** Matplotlib
- **Development Environment:** Jupyter Notebook

## 📁 Project Structure

```text
computational-taste-prediction/
│
├── app/
│   ├── app.py
│   └── app_taste_prediction.py
│
├── datasets/
│   ├── ChemTastesDB_cleaned_full.csv
│   └── ChemTastesDB_5basic_tastes_ML_ready.csv
│
├── models/
│   └── taste_models/
│       ├── salty_model.pkl
│       ├── sweet_model.pkl
│       ├── umami_model.pkl
│       ├── bitter_model.pkl
│       ├── sour_model.pkl
│       ├── taste_feature_columns.pkl
│       └── taste_models_info.json
│
├── notebooks/
│   ├── 04_chemtastesdb_five_taste_models_shap.ipynb
│   └── 05_algorithm_comparison_all_models.ipynb
│
├── results/
│   └── taste_model_comparison_report.md
│
├── smiles_featurizer.py
├── prepare_training_data.py
├── train_taste_models.py
├── predict_taste.py
├── requirements.txt
├── README.md
└── .gitignore
```

*This is a representative structure. Keep the actual paths and filenames from your project, particularly if your application uses relative paths.*

## 🚀 Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/computational-taste-prediction.git
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Navigate to the project directory

```bash
cd computational-taste-prediction
```

### 3. Create a virtual environment (recommended)

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

Ensure that `requirements.txt` includes the dependencies required by your actual application.

## ▶️ Running the Application

If your Streamlit application is `app_taste_prediction.py` inside the `app` folder, run the command from the project root:

```bash
streamlit run app/app_taste_prediction.py
```

If you use `app.py` instead, run:

```bash
streamlit run app/app.py
```

Use the command corresponding to your intended application entry point. The trained model files and datasets must be available at the paths expected by the code.

## 🔮 Making a Prediction

The current computational prediction workflow accepts a SMILES representation of a chemical compound.

1. Provide a valid SMILES string.
2. Extract the numerical molecular descriptors.
3. Load the trained taste-category models.
4. Calculate the predicted probability for each taste category.
5. Display the taste scores and the dominant predicted category.

The results represent model predictions based on the training data; they are not a guarantee of how a person would perceive the compound.

## 🔌 Hardware Integration Status

The project is inspired by Electronic Tongue technology. The current trained taste classifiers use molecular descriptors extracted from SMILES representations.

**Physical sensor readings such as pH and TDS are not currently the trained models' direct input features.** Connecting an ESP32 and chemical sensors to the interface does not, by itself, enable direct taste prediction from those sensor readings. That functionality would require a compatible sensor-data collection process and a separately trained and validated model.

## ⚠️ Limitations

- The model depends on the quality, coverage, and class distribution of the prepared dataset.
- Salty and Sour categories have relatively few positive examples.
- Custom molecular descriptors are approximate and may not capture all relevant chemical properties.
- Cross-validation results may differ from performance on independent real-world data.
- SHAP analysis depends on the successful execution of the explanation workflow.
- Physical Electronic Tongue sensor-based taste prediction requires further integration and validation.

## 🔮 Future Enhancements

- Improve molecular representation using RDKit descriptors and molecular fingerprints.
- Expand the dataset, especially for underrepresented taste categories.
- Evaluate models on an independent test dataset.
- Improve recall for minority taste categories.
- Integrate SHAP explanations into the application.
- Collect calibrated readings from chemical sensors and develop a dedicated sensor-based prediction model.
- Validate predictions using appropriate reference measurements and controlled experiments.

## 👩‍💻 Project Information

**Project Title:** Computational Modelling of Artificial Taste Perception Using Explainable Machine Learning Inspired by Electronic Tongue Technology

**Domain:** Artificial Intelligence, Machine Learning, Explainable AI, Computational Chemistry

**Project Type:** Final-Year Academic Project

## 📜 Disclaimer

This project is an academic machine-learning prototype for computational taste prediction. Its outputs should not be treated as definitive sensory assessments, food-safety evaluations, or medical advice.

## ⭐ Acknowledgements

This project was developed as part of a final-year academic project exploring machine learning, molecular feature extraction, and Explainable AI for taste prediction.
