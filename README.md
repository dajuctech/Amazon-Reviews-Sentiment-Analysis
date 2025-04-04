# Amazon Reviews Sentiment Analysis

This project develops a deep learning solution to classify Amazon review sentiments. The workflow involves data downloading, text cleaning and preprocessing, tokenization, model construction with bidirectional LSTMs, and evaluation. The process transforms raw review text and summaries into numerical sequences to train a neural network that distinguishes positive from negative reviews.

---

## 1. Environment Setup

- **Library Installation:**  
  The code installs necessary libraries including:
  - `keras`, `gdown` for data download and model building.
  - `nltk`, `BeautifulSoup`, and other packages for text cleaning and tokenization.
  
- **Data Downloading:**  
  The dataset (AmazonReviews.csv) is downloaded from Google Drive using `gdown`.

---

## 2. Data Loading and Exploration

- **Dataset Overview:**  
  The Amazon reviews dataset is loaded into a DataFrame, providing an initial glimpse of the review text, sentiment scores, and summaries.
  
- **Data Cleaning:**  
  Duplicate entries and missing rows are removed. Sentiment scores are converted into binary labels (e.g., scores below a threshold become negative, others positive).

---

## 3. Text Preprocessing

- **Text Cleaning:**  
  HTML tags, punctuation, and unwanted characters are removed using BeautifulSoup and regular expressions.  
  Contractions (e.g., "can't" → "cannot") are expanded using a predefined mapping.
  
- **Summary Processing:**  
  Review summaries are similarly cleaned and padded with start and end tokens.
  
- **Length Analysis:**  
  Histograms of review and summary word counts are used to determine optimal maximum sequence lengths for further processing.

---

## 4. Tokenization and Sequence Padding

- **Tokenization:**  
  A tokenizer is created to limit the vocabulary size based on word frequency, and it is fitted on the cleaned review text.
  
- **Sequence Conversion:**  
  Text reviews are converted into integer sequences and then padded to a uniform maximum length for input into the model.

---

## 5. Model Building and Training

- **Model Architecture:**  
  The model is built using:
  - An embedding layer (non-trainable) to convert words into dense vectors.
  - Two bidirectional LSTM layers with dropout to capture context in both directions.
  - Dense layers with L1 regularization, followed by a sigmoid output layer for binary classification.
  
- **Compilation and Training:**  
  The model uses the Adam optimizer and binary cross-entropy loss. Early stopping is applied to prevent overfitting, and training progress is monitored via accuracy and loss curves.

---

## 6. Evaluation and Visualization

- **Model Evaluation:**  
  The trained model is evaluated on a validation set, and its accuracy is reported.
  
- **Performance Visualization:**  
  Training and validation curves for accuracy and loss are plotted to visualize the learning progress over epochs.

---

## Conclusion

This project presents a complete pipeline for sentiment analysis of Amazon reviews using deep learning. The approach from data cleaning and tokenization to model training with bidirectional LSTMs demonstrates how to effectively transform raw text into actionable sentiment predictions. The modular design allows for easy adjustments to improve performance or adapt the methodology to other text classification challenges.


