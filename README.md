# Smart URL Safety Checker

**Detect phishing links before they detect you.**

Smart URL Safety Checker is a machine-learning-powered web application that analyzes a submitted URL and predicts whether it is likely to be legitimate or phishing. Built with Python and Flask, it combines URL-based feature extraction with a trained classifier and presents the prediction through a lightweight web interface.

> **Important:** This project provides a machine-learning risk prediction, not a guarantee that a URL is safe. Do not enter credentials or sensitive information on a website based only on this tool's result.

## Screenshots

### Home page

![Smart URL Safety Checker home page](image/Screenshot 2025-07-15 102832.png)

### Example prediction

![Smart URL Safety Checker prediction result](screenshots/url-checker-result.png)

## Features

- **Real-time URL prediction:** Submit a URL and view the model's classification in the web interface.
- **URL feature analysis:** Uses 30+ URL-based features, such as URL length, special-character patterns, and domain-related indicators, as implemented in the feature-extraction pipeline.
- **Machine learning:** Evaluates multiple classification algorithms and includes an XGBoost model.
- **Simple web UI:** Flask backend with HTML and CSS for URL input and result display.
- **Model evaluation:** Compares classifiers using accuracy and supports further evaluation with precision, recall, F1-score, and a confusion matrix.

## Model Performance

The following accuracy values are from the project's reported evaluation. Results depend on the dataset, feature extraction, train/test split, and evaluation setup.

| Model | Accuracy |
|---|---:|
| XGBoost | 97.0% |
| K-Nearest Neighbors (KNN) | 95.9% |
| Decision Tree | 95.8% |
| Logistic Regression | 93.4% |
| Naive Bayes | 60.5% |

**Best reported model:** XGBoost, with approximately **97% accuracy**.

## Tech Stack

| Area | Technologies |
|---|---|
| Language | Python |
| Web application | Flask, HTML, CSS |
| Machine learning | XGBoost, scikit-learn |
| Data processing | pandas, NumPy |
| Evaluation and visualization | Matplotlib, Seaborn |
| Development | Jupyter Notebook / Google Colab, VS Code |
| Version control | Git, GitHub |

## How It Works

1. The user enters a URL in the web interface.
2. The application processes the URL using the project's feature-extraction logic.
3. The extracted features are passed to the saved machine-learning model.
4. The model predicts the URL class.
5. Flask displays the prediction to the user.

The prediction is only as reliable as the training data, extracted features, and evaluation process. A high accuracy score on a test set does not guarantee correct predictions for every real-world URL.

## Project Structure

```text
Smart-URL-safety-checker/
├── app.py                    # Flask application and prediction route
├── ml(1).ipynb               # Model training and evaluation notebook
├── phishing_model.pkl        # Serialized trained model
├── phishing_site_data.csv    # Dataset used for model development
├── README.md                 # Project documentation
├── templates/
│   └── index.html             # URL input and prediction interface
├── static/
│   └── style.css              # Page styling
└── screenshots/
    ├── url-checker-home.png   # Application home page
    └── url-checker-result.png # Example prediction result
```

> Keep the screenshot paths and filenames above consistent with the files committed to your repository. If your actual repository uses different filenames, update this tree accordingly.

## Getting Started

### Prerequisites

- Python 3.9 or a compatible Python version supported by your installed dependencies
- Git (optional, for cloning the repository)

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd Smart-URL-safety-checker
```

Replace `<your-repository-url>` with your repository's Git URL.

### 2. Create and activate a virtual environment

**Windows (Command Prompt):**

```bat
python -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

Install the libraries used by your application and notebook:

```bash
pip install flask pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
```

If the repository has a `requirements.txt`, prefer installing from it:

```bash
pip install -r requirements.txt
```

### 4. Run the application

From the project root, run:

```bash
python app.py
```

Open the local address printed in the terminal, commonly `http://127.0.0.1:5000/`.

**Before running:** Ensure `app.py` loads `phishing_model.pkl` from the expected path and uses the same feature order and preprocessing that were used during training. The notebook, model, and inference code must agree on the feature schema.

## Evaluation

The project compares multiple models, with XGBoost achieving the highest reported accuracy in the current results. For a stronger and more reproducible evaluation, report the test-set size and split strategy, and include precision, recall, F1-score, and the confusion matrix. For phishing detection, recall for phishing URLs and false-positive rates are particularly important because accuracy alone can hide costly mistakes.

## Possible Improvements

- Add a `requirements.txt` with pinned, tested dependency versions.
- Add unit tests for URL feature extraction and prediction handling.
- Validate malformed URLs and handle missing or unexpected features gracefully.
- Display a confidence or risk score only if it is calibrated and supported by the model.
- Evaluate on a separate, newer dataset to test generalization to previously unseen URLs.
- Add a REST API or browser extension after validating model performance and security.
- Deploy behind HTTPS and add input validation, logging, and rate limiting before public use.

## Resume-Ready Project Description

**Smart URL Safety Checker | Python, Flask, XGBoost, scikit-learn, pandas**

- Built a Flask web application that classifies submitted URLs as potentially legitimate or phishing using a machine-learning pipeline and 30+ URL-based features.
- Compared multiple classifiers and achieved **97% reported test accuracy with XGBoost**; evaluated alternatives including Decision Tree, KNN, Logistic Regression, and Naive Bayes.
- Developed a lightweight HTML/CSS interface for real-time URL submission and prediction.

Only retain the 97% figure if it matches your actual held-out test results. Be ready to explain the dataset, train/test split, feature extraction, evaluation metrics, and how the Flask app loads and uses the saved model.

## Repository Notes

- Do not commit secrets, credentials, or local environment files.
- If the dataset is large or has redistribution restrictions, document its source and provide download instructions instead of committing it.
- Add a license only if you have chosen terms for reuse.

## Disclaimer

This project is intended for educational and research purposes. Its predictions can be wrong and should not be treated as a definitive security verdict. Use established security tools and safe browsing practices when evaluating suspicious links.
