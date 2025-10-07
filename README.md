# Malicious URL Detection

**Repository:** https://github.com/Yash-Bhisekar/Malicious-URL-Detection

## Project Overview

A simple machine learning pipeline to detect malicious URLs (e.g., phishing, malware, defacement) using lexical and statistical features extracted from URLs. The project trains two models—Logistic Regression and Decision Tree—and provides an ensemble prediction by averaging their predicted probabilities.

## Contents

* `malicious_phish.csv` — dataset (CSV with at least two columns: `url`, `type`)
* `main.py` — training, evaluation and saving models (example name)
* `models/` — directory where trained models and preprocessors are saved

  * `logistic_model.pkl`
  * `decision_tree_model.pkl`
  * `scaler.pkl`
  * `label_encoder.pkl`
  * `feature_list.pkl`
* `predict.py` — script / function to predict a single URL (optional)
* `README.md` — this file

> **Note:** If your filenames differ, update the instructions below accordingly.

## Requirements

* Python 3.8+
* Recommended: create a virtual environment

### Python packages

* pandas
* numpy
* scikit-learn
* joblib
* matplotlib  (optional, for plots)
* seaborn     (optional, for confusion matrix heatmap)

Install with:

```
pip install -r requirements.txt
```

## Setup (one-time)

1. Clone the repository.
2. Create and activate a virtual environment.
3. Install the required dependencies.

## Dataset

Place your dataset CSV file (`malicious_phish.csv`) in the project root (or update the path in `main.py`). The CSV must contain at least these columns:

* `url` — the URL string
* `type` — the label (e.g., `benign`, `phishing`, `malware`, `defacement`)

## How to run (Train + Evaluate + Save models)

1. Ensure `malicious_phish.csv` is present.
2. Run the training script (example `main.py`).
3. The script will:

   * Load the dataset
   * Extract features from URLs (lexical + entropy + keyword indicators)
   * Split into train/test sets
   * Scale features (for Logistic Regression)
   * Train Logistic Regression and Decision Tree
   * Evaluate models (prints F1 score, confusion matrix, classification report)
   * Save trained models and preprocessing objects to `models/`

## How to run evaluation only

If you have saved models and want to evaluate on new test data, modify a script to:

* Load saved models using `joblib.load`
* Load the test CSV, extract features using the same extraction function
* Apply scaler (for Logistic Regression) and predict
* Use `sklearn.metrics` to compute F1 score and confusion matrix

## How to predict a single URL (interactive)

Run the prediction script, which:

* Loads saved models and preprocessing objects
* Extracts features from the input URL
* Applies scaler and predicts probabilities from both models
* Averages probabilities (ensemble) and prints final class and confidence

## Output interpretation

* **F1 Score (weighted):** single-number summary that balances precision and recall across classes (useful for imbalanced data).
* **Confusion Matrix:** detailed class-wise true/false positives/negatives. Visualize with a heatmap for easier inspection.

## Tips & Notes

* Ensure the same feature extraction code (and order of feature columns) is used during training and inference.
* If you add new features, retrain models and update `feature_list.pkl`.
* For better results consider adding host-based features (WHOIS, domain age), URL embeddings, or sequence models.

## License & Contact

* License: Choose a license (e.g., MIT) and add a `LICENSE` file if needed.
* Contact: Your Name (Yash) — add email if you want to share.

---


