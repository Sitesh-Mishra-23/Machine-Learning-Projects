# 🌱 Crop Recommendation System

A machine learning web app that recommends the most suitable crop to grow based on soil nutrients and climate conditions.

Built with Python, Scikit-learn, and Streamlit.

---

## 🚀 Live Demo

> _Add your Streamlit Cloud / Hugging Face link here_

---

## 📌 Features

- Recommends the best crop from **22 crop classes** based on user inputs
- Toggle between **Random Forest** and **Logistic Regression** models
- Live **accuracy badge** for each model
- Interactive **sliders** for all 7 soil and climate features
- Clean dark forest-green themed **Streamlit UI**
- End-to-end **sklearn Pipeline** with StandardScaler

---

## 🧠 Models Used

| Model | Accuracy |
|---|---|
| Random Forest | ~99% |
| Logistic Regression | ~96% |

> Trained on `Crop_recommendation.csv` — 2,200 rows, 22 crop classes.

---

## 📊 Input Features

| Feature | Description | Unit |
|---|---|---|
| N | Nitrogen content in soil | mg/kg |
| P | Phosphorus content in soil | mg/kg |
| K | Potassium content in soil | mg/kg |
| Temperature | Average temperature | °C |
| Humidity | Relative humidity | % |
| pH | Soil pH value | 0–14 |
| Rainfall | Annual rainfall | mm |

---

## 🗂️ Project Structure

```
crop-recommendation/
│
├── app.py                  # Streamlit UI
├── train_model.py          # Model training script
├── rf_model.pkl            # Saved Random Forest model
├── lr_model.pkl            # Saved Logistic Regression model
├── Crop_recommendation.csv # Dataset
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation & Setup

**1. Clone the repository**
```bash
git clone https://github.com/your-username/crop-recommendation.git
cd crop-recommendation
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Train the models (generates .pkl files)**
```bash
python train_model.py
```

**4. Run the Streamlit app**
```bash
streamlit run app.py
```

---

## 📦 Requirements

```
scikit-learn
streamlit
pandas
numpy
joblib
```

---

## 📁 Dataset

- **Source:** [Kaggle — Crop Recommendation Dataset](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset)
- **Rows:** 2,200
- **Classes:** 22 crops (rice, wheat, maize, mango, cotton, etc.)
- **Features:** 7 soil and climate parameters

---

## 🙋 Author

**Sitesh Mishra**
B.Tech ECE @ BPIT, New Delhi | 2023–2027

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Sitesh%20Mishra-blue?logo=linkedin)](https://www.linkedin.com/in/sitesh-mishra)

---


