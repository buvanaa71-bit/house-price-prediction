# 🏠 House Price Prediction — Predictive Analytics Using Historical Data

> **Internship Project** | AI & Data Science | Linear Regression with Python

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Problem Statement](#-problem-statement)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Tech Stack](#-tech-stack)
- [How to Run](#-how-to-run)
- [Results](#-results)
- [Visualizations](#-visualizations)
- [Future Scope](#-future-scope)
- [References](#-references)

---

## 🎯 Project Overview

This project demonstrates **Predictive Analytics** using historical housing data to build a **Linear Regression** model that predicts house sale prices. The project covers the complete Data Science pipeline:

```
Data Generation → Cleaning → EDA → Feature Engineering → Model Training → Evaluation → Prediction
```

---

## ❓ Problem Statement

> *"Can we accurately predict the sale price of a house based on its physical characteristics, location, and surrounding amenities?"*

Real estate pricing is complex and influenced by dozens of factors. This project uses Machine Learning to automate price estimation, helping buyers, sellers, and agents make data-driven decisions.

---

## 📊 Dataset

| Property         | Value                                      |
|------------------|--------------------------------------------|
| Source           | Synthetically generated (realistic)        |
| Records          | 1,000                                      |
| Features         | 10 input features + 1 target               |
| Missing Values   | Injected (3–4%) for cleaning practice      |
| Duplicates       | 15 injected for cleaning practice          |

### Features

| Column           | Type       | Description                            |
|------------------|------------|----------------------------------------|
| `sqft_living`    | Numerical  | Living area in square feet             |
| `bedrooms`       | Numerical  | Number of bedrooms                     |
| `bathrooms`      | Numerical  | Number of bathrooms (incl. 0.5 baths)  |
| `house_age`      | Numerical  | Age of house in years                  |
| `lot_size`       | Numerical  | Total land area in sq ft               |
| `floors`         | Numerical  | Number of floors                       |
| `garage`         | Numerical  | Number of garage spaces                |
| `location`       | Categorical| Urban / Suburban / Rural               |
| `school_rating`  | Categorical| Poor / Average / Good / Excellent      |
| **`price`**      | **Target** | **House sale price in USD**            |

---

## 📁 Project Structure

```
house_price_project/
│
├── house_price_prediction.py    ← Main Python notebook (all 23 cells)
├── README.md                    ← This file
├── Project_Report.docx          ← 8–10 page professional report
├── Presentation.pptx            ← 12-slide PowerPoint
├── viva_and_interview_QA.md     ← 20 Viva + Interview Q&A
│
└── output_charts/               ← Auto-generated when you run the code
    ├── outlier_boxplots.png
    ├── histograms.png
    ├── correlation_heatmap.png
    ├── scatter_plots.png
    ├── boxplots_category.png
    ├── actual_vs_predicted.png
    ├── regression_line.png
    ├── trend_graph.png
    └── feature_importance.png
```

---

## 🛠 Tech Stack

| Library       | Version  | Purpose                              |
|---------------|----------|--------------------------------------|
| Python        | 3.8+     | Core programming language            |
| pandas        | 1.5+     | Data manipulation                    |
| numpy         | 1.23+    | Numerical operations                 |
| matplotlib    | 3.6+     | Basic plotting                       |
| seaborn       | 0.12+    | Statistical visualizations           |
| scikit-learn  | 1.1+     | ML model, train-test split, metrics  |

---

## ▶️ How to Run

### Option A — Google Colab (Recommended for Beginners)

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Upload Notebook**
3. Upload `house_price_prediction.py`
4. Click **Runtime → Run All**
5. All charts will display inline ✅

### Option B — Jupyter Notebook (Local)

```bash
# Step 1: Install required libraries
pip install pandas numpy matplotlib seaborn scikit-learn

# Step 2: Launch Jupyter
jupyter notebook

# Step 3: Open house_price_prediction.py and run all cells
```

### Option C — Run as Python Script

```bash
python house_price_prediction.py
```

> All charts are automatically saved as `.png` files in the working directory.

---

## 📈 Results

| Metric | Value       | Interpretation                              |
|--------|-------------|---------------------------------------------|
| MAE    | ~$30,000    | Average prediction is off by ~$30K          |
| MSE    | ~$1.8B      | Penalized squared error                     |
| RMSE   | ~$42,000    | Error in price units (USD)                  |
| **R²** | **~0.87**   | **Model explains ~87% of price variance**   |

---

## 📊 Visualizations

The notebook generates **9 publication-quality charts**:

1. 📦 **Box Plots** — Outlier detection for all numerical features
2. 📊 **Histograms** — Distribution of each feature
3. 🌡️ **Correlation Heatmap** — Feature relationships
4. 🔵 **Scatter Plots** — Feature vs. Price with trend lines
5. 📦 **Category Box Plots** — Price by Location and School Rating
6. 🎯 **Actual vs Predicted** — Model accuracy scatter
7. 📉 **Residuals Plot** — Error distribution
8. 📏 **Regression Line** — Visual of linear relationship
9. 📈 **Trend Graph** — Historical + future price projection

---

## 🔮 Future Scope

| Enhancement             | Technology              |
|-------------------------|-------------------------|
| Advanced ML models      | Random Forest, XGBoost  |
| Real-world dataset      | Kaggle (Ames / Seattle) |
| Feature expansion       | Crime rate, Walk Score  |
| Hyperparameter tuning   | GridSearchCV            |
| Web deployment          | Streamlit / Flask       |
| API service             | FastAPI + Docker        |

---

## 📚 References

1. Scikit-learn Documentation — https://scikit-learn.org/stable/
2. Pandas Documentation — https://pandas.pydata.org/docs/
3. Seaborn Documentation — https://seaborn.pydata.org/
4. Kaggle House Prices Dataset — https://www.kaggle.com/c/house-prices-advanced-regression-techniques
5. James, G. et al. (2021). *An Introduction to Statistical Learning*. Springer.
6. Géron, A. (2022). *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow*. O'Reilly.

---

## 👤 Author

**[Your Name]**  
AI & Data Science Intern  
[Your Institution / Company]  
[your.email@example.com]

---

*Built with ❤️ for learning purposes. Feel free to fork, modify, and learn!*
