# 🎵 Music Recommendation & Prediction System

## 1. Project Overview
This project aims to build a **Machine Learning Classification Model** capable of predicting whether a user will listen to a song on **Repeat (1)** or **Not (0)**. By analyzing various audio features (such as acousticness, danceability, energy, and popularity), the system identifies patterns that contribute to a song's "replay value."

---

## 2. Dataset & Features
The dataset consists of various musical attributes for different tracks.
* **Input Features ($X$):** Numeric audio traits like `acousticness`, `danceability`, `energy`, `instrumentalness`, `liveness`, `loudness`, `speechiness`, `tempo`, etc.
* **Target Variable ($y$):** A binary classification:
    * `1`: High likelihood of repeat (Hit/Liked).
    * `0`: Low likelihood of repeat (Skip).

---

## 3. Methodology Pipeline

### A. Data Preprocessing
1.  **Cleaning:** Removed irrelevant identifiers such as `Unnamed: 0`, `track_id`, `artists`, `album_name`, and `track_name`.
2.  **Handling Missing Data:** Dropped null values and removed duplicate records to ensure data quality.

### B. Feature Engineering (The "Hit" Score)
Since the dataset did not have a direct "target" label initially, we engineered one using a weighted formula based on key success metrics:
> $$Score = (Popularity_{norm} \times 0.4) + (Danceability \times 0.3) + (Energy \times 0.3)$$

* **Thresholding:** Songs scoring in the **top 30%** (quantile > 0.7) were labeled as **1 (Repeat)**, and the rest as **0**.

### C. Data Balancing
The dataset was initially imbalanced. To prevent the model from being biased toward the majority class (0), we used **Downsampling (Resample)** to match the number of minority class samples, resulting in a perfectly balanced 50/50 dataset.

---

## 4. Model Architecture
* **Algorithm:** [Random Forest Classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
* **Hyperparameters:**
    * `n_estimators`: 100 (Number of trees)
    * `max_depth`: 15 (Tree depth to capture complex patterns)
* **Scaling:** Applied `StandardScaler` to normalize feature distributions, ensuring the model treats all audio features equally.

---

## 5. Performance & Results
The model was evaluated on a 20% test set.
* **Final Accuracy:** **~97.79%**
* **Evaluation Metrics:** The Confusion Matrix indicates minimal misclassifications, and the Feature Importance plot highlights which audio attributes contribute most to a song's success.

---

## 6. Real-time Prediction
A custom function `predict_new_song()` was implemented to accept raw audio features of a new track and output:
1.  **Prediction:** Repeat vs. No Repeat.
2.  **Confidence Score:** The probability percentage of the prediction.
