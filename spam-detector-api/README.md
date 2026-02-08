# 📩 Spam Message Detector API (ML + FastAPI)

## 🚀 Project Overview

Spam messages and fraud texts are common and users often cannot quickly determine whether a message is safe.
This project builds a Machine Learning based Spam Detector and exposes it as a FastAPI web service so messages can be checked instantly through an API.

The system uses TF-IDF text vectorization and a Naive Bayes classifier to predict whether a message is **spam** or **ham (not spam)**.

---

## 🎯 Problem Statement

Users receive suspicious SMS messages but lack a quick automated way to verify if they are spam or legitimate.

---

## 💡 Solution

We built a lightweight ML pipeline that:

* Processes SMS text
* Converts text → numerical features using TF-IDF
* Classifies messages using Naive Bayes
* Serves predictions through a FastAPI endpoint
* Provides interactive API testing via Swagger UI

---

## 🧠 ML Approach

* Text preprocessing with TF-IDF Vectorizer
* Stopword removal
* Multinomial Naive Bayes classifier
* Pipeline used for clean training + inference
* Model saved using joblib

---

## 🏗️ Architecture Diagram

```
User Message
     ↓
FastAPI /predict endpoint
     ↓
Loaded ML Pipeline
(TF-IDF + Naive Bayes)
     ↓
Spam / Ham Prediction
     ↓
JSON Response
```

---

## 📁 Project Structure

```
spam-detector-api/
│
├── app/
│   ├── main.py
│
├── model/
│   ├── train.py
│   └── model.pkl
│
├── data/
│   └── spam.csv
│
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repo

```
git clone <your-repo-url>
cd spam-detector-api
```

### 2️⃣ Create Virtual Environment

```
python -m venv venv
venv\Scripts\activate
```

### 3️⃣ Install Dependencies

```
pip install -r requirements.txt
```

---

## 🏋️ Train Model

```
cd model
python train.py
```

This generates:

```
model/model.pkl
```

---

## ▶️ Run API Server

From project root:

```
uvicorn app.main:app --reload
```

Open browser:

```
http://127.0.0.1:8000/docs
```

---

## 🧪 Test Example

Endpoint:

```
/predict
```

Example input:

```
Congratulations! You won a free iPhone. Click now!
```

Example output:

```
{
  "input": "...",
  "prediction": "spam"
}
```

---

## 🔍 Code Explanation (High Level)

**train.py**

* Loads dataset
* Cleans columns
* Splits train/test
* Builds TF-IDF + Naive Bayes pipeline
* Trains model
* Saves model.pkl

**main.py**

* Loads saved model
* Creates FastAPI app
* Defines prediction endpoint
* Returns JSON response

---

## 📌 Future Improvements

* Add probability score
* Add web frontend UI
* Add model retraining endpoint
* Add database logging
* Deploy to cloud

---

## 👨‍💻 Author

Deepak — AI/ML Project Series (One Day One Project)

---
