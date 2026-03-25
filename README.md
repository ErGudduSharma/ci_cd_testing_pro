# CI/CD Testing Pro - COVID Prediction & S3 Sync

This is a complete Machine Learning and CI/CD project that implements automated testing, model prediction workflows, and cloud synchronization logic using **GitHub Actions** and **AWS S3**. The project models a dataset to predict COVID-19 probability (`has_covid`) while demonstrating deployment automation techniques.

## 🚀 Features

- **Machine Learning**: 
  - Imports and preprocesses the `covid_toy.csv` dataset.
  - Imputes missing values (`SimpleImputer` - `mean` strategy) for numerical data.
  - Encodes categorical values using `LabelEncoder`.
  - Standardizes the data with `StandardScaler`.
  - Trains three distinct classification models to test prediction accuracies:
    1. `LogisticRegression`
    2. `DecisionTreeClassifier`
    3. `RandomForestClassifier`

- **Continuous Integration / Continuous Deployment (CI/CD)**:
  - Automates uploading pipeline logic to Google Cloud and AWS.
  - Includes a pre-configured `s3-sync.yml` inside `.github/workflows/` that triggers on commits to the **main branch**.
  - Synchronizes all local repository files to the `cicd-testing-pro` AWS S3 bucket using securely stored `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` secrets.

## 📁 File Structure

```
ci_cd_testing_pro/
│
├── .github/workflows/  # Contains the CI/CD pipeline actions
│   └── s3-sync.yml     # Automates sync to AWS S3 bucket
├── covid_toy.csv       # Raw dataset used for the ML pipeline
├── app.py              # Main ML process flow & model training scripts
├── test.py             # Basic test script runner
├── requirements.txt    # Python Dependencies
└── README.md           # Documentation for project
```

## 🛠️ Prerequisites

To run this application locally, ensure you have Python installed and the required libraries from `requirements.txt`. 

```bash
pip install -r requirements.txt
```

**Required Libraries:**
- `numpy`
- `pandas`
- `scikit-learn`

## ⚙️ Running the Project

To run the machine learning model pipeline and view the resulting prediction accuracies for the three classifiers on your terminal, execute:

```bash
python app.py
```

## ☁️ Automating CI/CD to AWS S3

Whenever you push modifications to the `main` branch of this repository, GitHub Actions will detect the change and kick off a runner to configure AWS securely.
To make sure this functionality successfully synchronizes data with S3, you must configure the following **Secrets** in your GitHub repository's Settings under Security > Secrets and Variables > Actions:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

Check out your GitHub Actions tab to view the live sync logs!
