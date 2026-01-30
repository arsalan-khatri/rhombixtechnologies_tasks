# 🐦 Twitter Sentiment Analysis - Rhombix Technologies Task 2

### Developed by: Arsalan Khatri
**Position:** AI/ML Intern  
**Project:** Sentiment Analysis of 1.6 Million Tweets  
**Education:** AI Engineer (SMI University, 2025 Graduated)

---

## Project Overview
This project is part of my internship at Rhombix Technologies. The goal is to build a machine learning model capable of classifying the sentiment of tweets as either **Positive** or **Negative**. This analysis helps in understanding public opinion and brand perception on social media.

---

## Dataset Information
The project uses the **Sentiment140** dataset. 
* **Note:** Due to GitHub's file size limit (100MB), the raw CSV dataset (227MB) is not uploaded here.
* **Download Source:** [Kaggle - Sentiment140 Dataset](https://www.kaggle.com/datasets/kazanova/sentiment140)
* **Setup:** Place the `training.1600000.processed.noemoticon.csv` file inside a folder named `/data` in your local directory to run the notebook.

---

## Technical Workflow
* **Preprocessing:** * Removal of URLs, Mentions (@), and special characters.
    * Stopwords removal using NLTK.
    * Word Stemming using **PorterStemmer**.
* **Feature Extraction:** Used **TF-IDF Vectorizer** (50,000 features) to convert text into numerical data.
* **Algorithm:** **Logistic Regression** was chosen for its high efficiency and accuracy in binary text classification.
* **Deep Learning (Optional):** Integration with **BERT (RoBERTa)** for context-aware sentiment detection.

---

## Key Features
* **Scalability:** Trained on 1.6 million tweets.
* **Deployment Ready:** The trained model and vectorizer are saved as `.pkl` files for real-time integration.
* **Insights:** Visualized the top 10 words that trigger positive and negative sentiments.

---

## Results
* **Accuracy:** ~77.77%
* **Precision/Recall:** Balanced performance across both positive and negative classes.
