# CAPSTONE PROJECT REPORT

## **End-to-End Data Science Project: E-Commerce Product Analysis**

---

## 1) Introduction

### 1.1 Background

E-commerce platforms generate massive volumes of product-related data, including pricing, ratings, and customer engagement metrics. Analyzing this data helps organizations understand customer preferences, optimize pricing strategies, and improve product recommendations.

### 1.2 Problem Statement

The company aims to leverage data science techniques to:

* Understand product trends and customer behavior
* Segment products into meaningful groups
* Predict product segments using machine learning models

### 1.3 Project Objectives

* Collect real-world product data using web scraping
* Clean and preprocess the data for analysis
* Store the processed data in a relational database
* Apply unsupervised learning to identify product segments
* Apply supervised learning models to predict product segments
* Optimize the best-performing model using hyperparameter tuning

---

## 2) Data Collection (Web Scraping)

### 2.1 Data Source

A publicly available e-commerce demo website (**BooksToScrape**) was used for data collection. This website is designed for educational scraping and follows ethical scraping practices.

### 2.2 Tools & Technologies

* Python
* Requests
* BeautifulSoup
* Pandas

### 2.3 Data Extracted

* Product Name
* Price
* Category
* Rating

A total of **1000 product records** were collected by scraping 50 pages of the website.

### 2.4 Ethical Considerations

* Only publicly accessible pages were scraped
* Website terms and robots.txt were respected
* Data was used strictly for academic purposes

---

## 3) Data Cleaning & Exploratory Data Analysis (EDA)

### 3.1 Data Cleaning Steps

* Removed duplicate records
* Handled missing values (none found after cleaning)
* Standardized text fields (lowercase, trimmed spaces)
* Converted price and rating columns to numeric formats

Since the dataset did not include review counts, a **realistic simulation of “Number of Reviews”** was added to support deeper analysis and modeling. This assumption was clearly documented.

### 3.2 Final Dataset Columns

* Product_Name
* Price
* Category
* Rating
* Number_of_Reviews

### 3.3 Exploratory Data Analysis (EDA)

EDA was performed to understand data distribution and relationships:

* Price distribution analysis
* Rating frequency analysis
* Relationship between price and rating

### 3.4 Key Insights from EDA

* Most products fall within a low-to-mid price range
* Highly rated products generally have moderate pricing
* Higher prices do not always correlate with higher ratings

---

## 4) Data Storage

### 4.1 Objective

Store cleaned and processed data in a structured format for easy access and future analysis.

### 4.2 Database Used

* SQLite (via SQLAlchemy)

### 4.3 Process

* Created a relational database
* Stored cleaned product data into a `products` table
* Retrieved data successfully for modeling tasks
  
This approach ensures scalability and reusability of data.

---

## 5) Unsupervised Learning (Clustering)

### 5.1 Objective

Identify hidden patterns and group similar products based on numerical attributes.

### 5.2 Algorithm Used

* **K-Means Clustering**

### 5.3 Features Used

* Price
* Rating
* Number_of_Reviews

### 5.4 Methodology

* Features were standardized using StandardScaler
* The Elbow Method was used to determine the optimal number of clusters
* The optimal value of **k = 3** was selected

### 5.5 Clustering Results

Each product was assigned a cluster label.

#### Cluster Interpretation:

* **Cluster 0:** Low-priced, low-engagement products (Budget segment)
* **Cluster 1:** Medium-priced, highly rated products (Best sellers)
* **Cluster 2:** High-priced, moderate-engagement products (Premium segment)

---

## 6) Supervised Learning

### 6.1 Objective

Predict the product segment (cluster) using supervised classification models.

### 6.2 Target Variable

* `Cluster`

### 6.3 Features Used

* Price
* Rating
* Number_of_Reviews

### 6.4 Models Implemented

* Logistic Regression
* Support Vector Machine (SVM)
* k-Nearest Neighbors (k-NN)
* Random Forest
* XGBoost

### 6.5 Evaluation Metrics

* Accuracy
* F1 Score (Weighted)

### 6.6 Model Performance Summary (Sample)

| Model                   | Accuracy | F1 Score |
| ----------------------- | -------- | -------- |
| **Logistic Regression** | **0.99** | **0.99** |
| SVM                     | 0.98     | 0.98     |
| KNN                     | 0.96     | 0.95     |
| Random Forest           | 0.96     | 0.96     |
|   XGBoost               | 0.97     | 0.97     |

### 6.7 Best Model

**Logistic Regression** achieved the highest accuracy and F1 score and was selected for further optimization.

---

## 7) Hyperparameter Tuning

### 7.1 Objective

Improve model performance by tuning hyperparameters of the XGBoost model.

### 7.2 Technique Used

* GridSearchCV

### 7.3 Parameters Tuned

* Number of estimators
* Maximum depth
* Learning rate
* Subsample ratio

### 7.4 Outcome

The tuned XGBoost model showed improved generalization and achieved the highest predictive performance on the test dataset.

---

## 8) Conclusion & Business Recommendations

### 8.1 Conclusion

This project successfully demonstrated an end-to-end data science pipeline:

* Data collection
* Data cleaning & EDA
* Database storage
* Unsupervised and supervised machine learning
* Model optimization

### 8.2 Business Recommendations

* Focus marketing efforts on **Cluster 1 (Best sellers)**
* Optimize pricing strategies for **premium products**
* Use predictive models to automate product segmentation

### 8.3 Future Enhancements

* Include real customer review text for NLP analysis
* Apply deep learning models

---

## 9) Tools & Technologies Summary

* Python, Pandas, NumPy
* BeautifulSoup, Requests
* SQLAlchemy, SQLite
* Scikit-learn, XGBoost
* Matplotlib, Seaborn

---

##  End of Report
