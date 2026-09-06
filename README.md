# Breast Cancer Predictor

An interactive Streamlit app that estimates whether a breast mass is **benign** or **malignant** from cell nuclei measurements taken from a fine-needle aspiration (FNA) image. Adjust the measurement sliders and watch the prediction, probabilities, and radar chart update live.

**Live app** ᯓ★ https://breast-cancer-predictor-app-64ktzwy9fybxvnlp8tgaus.streamlit.app/

---

### How it works

- The sidebar exposes 30 cell nuclei measurements (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, and fractal dimension — each as a mean, standard error, and "worst" value), pre-filled with the dataset's mean values.
- These inputs are scaled and fed into a pre-trained **Logistic Regression** model, which predicts a diagnosis (Benign / Malignant) along with class probabilities.
- A Plotly radar chart visualizes the scaled measurement profile across all three groups (mean, standard error, worst).

### Dataset

[Breast Cancer Wisconsin (Diagnostic) Data Set](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data) from Kaggle, included in this repo at `data/data.csv`.

### Project structure

```
├── app/
│   └── main.py        # Streamlit app: sidebar, radar chart, predictions
├── model/
│   ├── main.py         # Trains the model and saves model.pkl / scaler.pkl
│   ├── model.pkl        # Pre-trained Logistic Regression model
│   └── scaler.pkl       # Pre-trained StandardScaler
├── data/
│   └── data.csv         # Breast Cancer Wisconsin dataset
├── assets/
│   └── style.css        # Custom styling for the app
└── requirements.txt
```

---

### Running locally

1. Clone the repo
   ```bash
   git clone https://github.com/userthek/breast-cancer-predictor-app.git
   cd breast-cancer-predictor-app
   ```
2. Install dependencies (a virtual environment is recommended)
   ```bash
   pip install -r requirements.txt
   ```
3. Launch the app
   ```bash
   streamlit run app/main.py
   ```
4. Open the URL Streamlit prints (typically `http://localhost:8501`).

### Retraining the model

The model and scaler are already trained and saved under `model/`. To regenerate them from the dataset:

```bash
python model/main.py
```

This retrains a Logistic Regression model on `data/data.csv`, prints its accuracy and classification report, and overwrites `model/model.pkl` and `model/scaler.pkl`.

---

### Deployment

Deployed on [Streamlit Community Cloud](https://streamlit.io/cloud):
https://breast-cancer-predictor-app-64ktzwy9fybxvnlp8tgaus.streamlit.app/
