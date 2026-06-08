# 🤖 CFPB Complaint Intelligence

> 🏦 An intelligent NLP-powered complaint classification platform that automates the categorization of consumer financial complaints using Machine Learning and Natural Language Processing.

---

# 📌 Overview

CFPB Complaint Intelligence is an end-to-end Machine Learning system that analyzes consumer financial complaints and automatically classifies them into multiple categories.

The platform leverages Natural Language Processing (NLP), ensemble machine learning models, and domain-specific business rules to assist organizations in understanding customer grievances and prioritizing high-risk complaints.

### 🎯 Prediction Targets

* 🏦 Product Category
* 📂 Sub-Product Category
* ⚠️ Complaint Issue
* 🚨 Priority Level

### 💼 Business Value

* Faster complaint triaging
* Reduced manual categorization effort
* Improved prioritization of critical complaints
* Better customer issue tracking
* Data-driven operational decision making

---

# 📊 Dataset

This project utilizes complaint records published by the Consumer Financial Protection Bureau (CFPB), a U.S. government agency responsible for collecting and maintaining consumer complaints related to financial products and services.

### Dataset Overview

| Attribute     | Value                                       |
| ------------- | ------------------------------------------- |
| 🏛️ Source    | Consumer Financial Protection Bureau (CFPB) |
| 🌎 Domain     | Financial Services                          |
| 📝 Data Type  | Consumer Complaint Text                     |
| 🎯 Task       | Multi-Class Text Classification             |
| 📂 Categories | Product, Sub-Product, Issue, Priority       |
| 📄 Format     | Unstructured Text                           |

### 🔗 Official Dataset Source

https://www.consumerfinance.gov/data-research/consumer-complaints/

### Dataset Note

The complete CFPB dataset contains a large volume of complaint records spanning multiple financial products and services.

For this project, a filtered and preprocessed subset was used to:

* Improve training efficiency
* Reduce computational requirements
* Focus on relevant complaint categories
* Enable faster experimentation and deployment

---

# ✨ Key Features

## 🧠 Intelligent Classification

* Multi-class complaint categorization
* Product prediction
* Sub-product prediction
* Issue prediction
* Priority level prediction

## ⚙️ NLP Processing Pipeline

* Text preprocessing and cleaning
* spaCy lemmatization
* TF-IDF vectorization
* Domain-specific feature engineering
* Class balancing using SMOTE

## 📊 Interactive Analytics

* Real-time complaint analysis
* Prediction confidence visualization
* Category breakdown insights
* Interactive dashboards
* User-friendly interface

## 🚀 Production-Oriented Design

* Voting Ensemble architecture
* Model persistence using Pickle
* Streamlit deployment
* Fast inference pipeline
* Scalable workflow design

---

# 🧠 Model Architecture

The project utilizes a Voting Ensemble strategy to improve classification robustness and reduce individual model bias.

### Ensemble Components

* LinearSVC
* Logistic Regression
* Multinomial Naive Bayes
* Random Forest

### NLP Pipeline

1. Text Cleaning
2. Tokenization
3. Stopword Removal
4. spaCy Lemmatization
5. TF-IDF Vectorization
6. Ensemble Classification

### Optimization Techniques

* TF-IDF Feature Engineering
* SMOTE Class Balancing
* Domain-Specific Rule Logic
* Ensemble Voting Strategy

---

# 📈 Model Performance

| Metric         | Score |
| -------------- | ----- |
| Accuracy       | 84.6% |
| Macro F1 Score | 74.8% |

### Why Macro F1?

Since complaint categories are imbalanced, Macro F1 Score was used to evaluate model performance across all classes equally rather than being dominated by majority categories.

The achieved Macro F1 Score demonstrates strong generalization across diverse complaint classes.

---

# 🔬 Machine Learning Pipeline

## 1️⃣ Data Collection

* CFPB Consumer Complaint Database
* Complaint narratives and metadata

## 2️⃣ Text Preprocessing

* Lowercasing
* Punctuation removal
* Stopword removal
* Lemmatization

## 3️⃣ Feature Engineering

* TF-IDF Vectorization
* Vocabulary Optimization
* Sparse Feature Generation

## 4️⃣ Class Balancing

* SMOTE Oversampling
* Minority Class Enhancement

## 5️⃣ Model Training

* LinearSVC
* Logistic Regression
* MultinomialNB
* Random Forest

## 6️⃣ Ensemble Learning

Predictions from multiple classifiers are combined using a Voting Ensemble to improve stability and classification performance.

---

# 🎯 Project Outcomes

## Business Outcomes

✅ Faster complaint triaging

✅ Reduced manual categorization effort

✅ Improved prioritization of high-risk complaints

✅ Better customer issue tracking

## Technical Outcomes

✅ Multi-class NLP classification pipeline

✅ Ensemble machine learning architecture

✅ TF-IDF feature engineering workflow

✅ Streamlit deployment

✅ Real-world financial services dataset

---

# 🛠️ Technology Stack

| Layer             | Technologies            |
| ----------------- | ----------------------- |
| Programming       | Python                  |
| Machine Learning  | Scikit-Learn            |
| NLP               | spaCy, TF-IDF           |
| Class Balancing   | SMOTE                   |
| Ensemble Learning | Voting Classifier       |
| Frontend          | Streamlit               |
| Deployment        | Streamlit Cloud, Docker |

---

# 🏃‍♂️ Execution Walkthrough (Run Locally)

Follow the steps below to set up, train, and run the CFPB Complaint Intelligence platform on your local machine.

## 1️⃣ Download Required Resources

Download the project resources:

* 📊 **Raw Dataset (`complaints.csv`)**
  https://drive.google.com/file/d/1yPyi5YCKh1wbtJxauktORltpZxALejh7/view?usp=drive_link

* 🧠 **Pre-trained Models (`trained_models.zip`)** *(Optional — skip training if using these models)*
  https://drive.google.com/file/d/1Bd6d2cnyLH5AQ7gSngn6H1DK3dgzlTrb/view?usp=drive_link

Create the required directory structure:

```text
data/
└── processed/
```

Place your processed dataset inside:

```text
data/processed/post_f_engg_data.csv
```

Ensure the dataset contains a `text` column holding complaint descriptions.

---

## 2️⃣ Setup the Environment

Create and activate a virtual environment:

```bash
python -m venv .venv
```

### Windows

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
source .venv/bin/activate
```

Install project dependencies:

```bash
pip install -r requirements.txt
```

Download the spaCy English language model:

```bash
python -m spacy download en_core_web_sm
```

---

## 3️⃣ Data Preprocessing

Generate cleaned text features and TF-IDF representations:

```bash
python src/data/preprocess.py
```

This step:

* Cleans complaint text
* Applies NLP preprocessing
* Generates TF-IDF features
* Creates training-ready datasets
* Saves the vectorizer for inference

---

## 4️⃣ Train Classification Models

Train all complaint classification models:

### Product Classifier

```bash
python src/models/train_product.py
```

### Sub-Product Classifier

```bash
python src/models/train_subproduct.py
```

### Issue Classifier

```bash
python src/models/train_issue.py
```

### Priority Classifier

```bash
python src/models/train_priority.py
```

After training, model artifacts (`.pkl` files) will be saved in the `models/` directory.

---

## 5️⃣ Launch the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

The application will be available at:

```text
http://localhost:8501
```

Open the URL in your browser and begin analyzing consumer financial complaints in real time.

---

## 6️⃣ Alternative: Use Pre-Trained Models

If you downloaded `trained_models.zip`:

1. Extract all model files into the `models/` directory.
2. Skip the training step.
3. Launch the application directly:

```bash
streamlit run app.py
```

This allows you to use the platform immediately without retraining the models.

---

# 📁 Project Structure

```text
.
├── app.py
├── models/
├── src/
│   ├── data/
│   │   └── preprocess.py
│   ├── models/
│   │   ├── train_product.py
│   │   ├── train_subproduct.py
│   │   ├── train_issue.py
│   │   └── train_priority.py
│   └── utils/
│       └── text_utils.py
├── data/
│   └── processed/
├── requirements.txt
├── Dockerfile
└── README.md
```

---

# 🚀 Future Enhancements

* Transformer-Based Classification (BERT, RoBERTa)
* Explainable AI (SHAP, LIME)
* Multi-Language Complaint Analysis
* Active Learning Pipeline
* Real-Time Complaint Monitoring Dashboard

---

# 👨‍💻 Author

Developed as an NLP and Machine Learning project focused on consumer complaint intelligence, automated categorization, and financial services analytics.

---

# 📜 License

This project is intended for educational, research, and portfolio purposes.
