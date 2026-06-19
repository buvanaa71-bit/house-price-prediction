# 🎓 Viva Questions & Answers + Interview Q&A
## Project: House Price Prediction — Predictive Analytics

---

## PART 1: VIVA QUESTIONS (20 Questions)

---

### Q1. What is Predictive Analytics?
**A:** Predictive Analytics is the use of historical data, statistical algorithms, and machine learning techniques to predict future outcomes. It identifies patterns in past data to make data-driven forecasts. In this project, we used historical house features to predict future sale prices.

---

### Q2. Why did you choose Linear Regression for this project?
**A:** Linear Regression is ideal because:
- House prices have an approximately linear relationship with features like sqft_living
- It is interpretable — we can see exactly how each feature affects price
- It is fast to train and serves as a strong baseline model
- The output (price) is a continuous numerical value, which suits regression perfectly

---

### Q3. What is the difference between MAE, MSE, and RMSE?
**A:**
- **MAE (Mean Absolute Error):** Average of absolute differences between actual and predicted values. Easy to interpret — same unit as price (USD).
- **MSE (Mean Squared Error):** Average of squared differences. Penalizes large errors more heavily. Unit is price².
- **RMSE (Root Mean Squared Error):** Square root of MSE. Brings units back to price (USD). More sensitive to outliers than MAE.
- **Relationship:** RMSE ≥ MAE always; if RMSE >> MAE, there are large outlier errors.

---

### Q4. What does R² (R-Squared) mean?
**A:** R² measures the proportion of variance in the target variable (price) that is explained by the model. 
- R² = 1.0 → perfect model
- R² = 0.87 → the model explains 87% of price variance
- R² = 0 → the model is no better than predicting the mean
- R² can be negative if the model is worse than predicting the mean

---

### Q5. What is the purpose of the Train-Test Split?
**A:** The train-test split separates data into:
- **Training set (80%):** Used to train (teach) the model — it learns patterns from this data
- **Test set (20%):** Used to evaluate model performance on **unseen** data
This prevents **overfitting** (memorizing training data) and gives an honest measure of real-world performance. We used `random_state=42` for reproducibility.

---

### Q6. What is Feature Engineering? What features did you create?
**A:** Feature Engineering is the process of creating new input features from existing ones to improve model performance. We created:
- `price_per_sqft` = price / sqft_living
- `total_rooms` = bedrooms + bathrooms
- `condition_index` = (80 − house_age)/80 + floors × 0.1
These derived features capture relationships not directly present in the raw data.

---

### Q7. How did you handle missing values? Why median and not mean?
**A:** We used **median imputation** — replacing NaN values with the median of that column. We chose median over mean because:
- Median is **robust to outliers** — a few very expensive/cheap houses won't skew it
- Mean is pulled by extreme values; for skewed distributions like house prices, median is more representative
For categorical columns, mode (most frequent value) would be appropriate.

---

### Q8. What is a Correlation Heatmap and what did it tell you?
**A:** A Correlation Heatmap is a color-coded matrix showing pairwise correlation coefficients between all numerical features. Values range from -1 to +1:
- **+1** = perfect positive correlation (both increase together)
- **-1** = perfect negative correlation (one increases as other decreases)
- **0** = no linear relationship
In our project, `sqft_living` showed the highest positive correlation with `price`, while `house_age` showed a negative correlation.

---

### Q9. What is an outlier? How did you detect them?
**A:** An outlier is a data point that differs significantly from other observations. We used the **IQR (Inter-Quartile Range) method**:
- IQR = Q3 − Q1
- Lower bound = Q1 − 1.5 × IQR
- Upper bound = Q3 + 1.5 × IQR
- Any value outside these bounds is flagged as an outlier
We chose to **keep** outliers because they represent genuine luxury or very small homes, not data errors.

---

### Q10. What is the difference between supervised and unsupervised learning?
**A:**
- **Supervised Learning:** The model is trained on labeled data (input + correct output). Our project is supervised — we provide house features AND their actual prices. The model learns the mapping.
- **Unsupervised Learning:** No labels. The model finds hidden patterns itself (e.g., clustering similar houses together).
- **Examples:** Supervised → Regression, Classification. Unsupervised → K-Means, PCA.

---

### Q11. What is overfitting and underfitting?
**A:**
- **Overfitting:** The model memorizes training data too well but fails on new data. High training accuracy, low test accuracy. Too complex a model.
- **Underfitting:** The model is too simple to capture patterns. Poor accuracy on both training and test data.
- **Ideal:** A balanced model with similar train/test performance.
- **Detection:** Compare train R² vs test R². Large gap = overfitting.

---

### Q12. Why did you encode categorical variables?
**A:** Machine Learning algorithms can only process numerical data. Categorical variables like `location` (Urban/Suburban/Rural) and `school_rating` are text. We used **Label Encoding** (from scikit-learn's `LabelEncoder`) to convert them to integers (0, 1, 2). An alternative is **One-Hot Encoding**, which creates binary columns for each category — better when there is no inherent order.

---

### Q13. What do the coefficients of Linear Regression tell you?
**A:** Each coefficient shows how much the predicted price changes for a **one-unit increase** in that feature, holding all others constant. For example:
- `sqft_living` coefficient = 70 → adding 1 sq ft increases predicted price by $70
- `house_age` coefficient = −1,500 → each year of age decreases predicted price by $1,500
- The sign indicates direction (+ = price goes up, − = price goes down)

---

### Q14. What is the residual plot and what should it look like?
**A:** A residual plot shows `(Actual − Predicted)` on the Y-axis vs Predicted values on the X-axis. 
- **Ideal pattern:** Random scatter around the zero line (no systematic pattern)
- **Red flag:** Funnel shape = heteroscedasticity (variance increases with price)
- **Red flag:** Curved pattern = the relationship isn't actually linear
In our model, residuals were roughly randomly distributed, indicating a good fit.

---

### Q15. What is the purpose of `random_state=42` in the code?
**A:** `random_state` is a seed for the random number generator. Setting it to any fixed number (42 is a convention) ensures that:
- The train-test split is the **same every time** you run the code
- Results are **reproducible** — others can get identical results
- Debugging is easier — you can compare outputs across runs
Without it, each run could give slightly different splits and different metric values.

---

### Q16. What is the difference between regression and classification?
**A:**
- **Regression:** Predicts a **continuous numerical value** (e.g., house price = $350,000)
- **Classification:** Predicts a **category/class** (e.g., house is "Expensive" / "Affordable")
House price prediction is a regression problem because the output can be any value, not a fixed category.

---

### Q17. What other algorithms could you have used instead of Linear Regression?
**A:** Several alternatives exist for regression tasks:
- **Decision Tree Regressor** — non-linear, interpretable tree structure
- **Random Forest Regressor** — ensemble of decision trees, more accurate
- **Gradient Boosting / XGBoost** — state-of-the-art performance on tabular data
- **Support Vector Regression (SVR)** — works well for smaller datasets
- **Neural Networks** — powerful but requires more data and tuning
We chose Linear Regression as a beginner-friendly baseline.

---

### Q18. What is the difference between `fit()`, `predict()`, and `transform()` in scikit-learn?
**A:**
- **`fit(X, y)`** — trains the model on training data, learns parameters (weights)
- **`predict(X)`** — uses learned parameters to make predictions on new data
- **`transform(X)`** — applies a learned transformation (e.g., scaling, encoding) — used in preprocessing, not in models directly
- **`fit_transform(X)`** — fits AND transforms in one step (convenience method)

---

### Q19. Why do we use Box Plots for outlier detection?
**A:** Box Plots visually display the distribution of data through 5 key statistics:
- **Minimum, Q1, Median, Q3, Maximum** (the "five-number summary")
- The box spans Q1 to Q3 (the IQR)
- The **whiskers** extend to 1.5 × IQR beyond Q1 and Q3
- Any point **beyond the whiskers** is shown as an individual dot = outlier
They make it instantly visual to spot extreme values in each feature.

---

### Q20. What improvements would make this project production-ready?
**A:** To move this from a student project to production:
1. **Real data** — scrape or use Kaggle's real housing datasets
2. **Feature scaling** — Standardization/Normalization for better convergence
3. **Cross-validation** — K-Fold CV for more reliable performance estimates
4. **Model comparison** — evaluate multiple algorithms side by side
5. **Hyperparameter tuning** — GridSearchCV / RandomizedSearchCV
6. **Pipeline** — scikit-learn Pipeline to prevent data leakage
7. **Deployment** — Streamlit app or REST API (FastAPI/Flask)
8. **Monitoring** — track model drift over time with new data

---

## PART 2: INTERVIEW QUESTIONS & ANSWERS

---

### IQ1. Walk me through your data science project end-to-end.
**A:** "I built a house price prediction model using Python. I started by generating a realistic 1,000-record dataset since real-world internet access was unavailable. I then cleaned the data — handling 3-4% missing values with median imputation and removing 15 duplicate rows. During EDA, I visualized distributions, correlations, and category effects using histograms, heatmaps, and box plots. I engineered three new features including a condition index and total rooms. I trained a Linear Regression model on 80% of data, evaluated it on 20%, achieving R²=0.87 and RMSE≈$42K. The model was then used to predict prices for 5 hypothetical houses."

---

### IQ2. How do you evaluate if a regression model is good enough?
**A:** I look at multiple metrics together:
- **R² > 0.80** → generally considered good for real estate
- **RMSE relative to mean price** — RMSE/mean should be < 15%
- **Residual plot** — should show no systematic patterns
- **Business context** — for a $300K average home, a $30K error may be acceptable or not depending on use case
I also compare against a baseline (e.g., predicting the mean for everyone) to ensure the model actually adds value.

---

### IQ3. What would you do if your model had very high training accuracy but low test accuracy?
**A:** That's a classic sign of **overfitting**. I would:
1. Increase the amount of training data
2. Apply regularization (Ridge/Lasso regression for linear models)
3. Reduce model complexity (fewer features or simpler model)
4. Use cross-validation instead of a single train-test split
5. Apply feature selection to remove noise features

---

### IQ4. How would you handle a dataset with 40% missing values in one column?
**A:** It depends on the column's importance:
- If it's a **key predictor** → try advanced imputation (KNN Imputer, IterativeImputer) or create a "missing" indicator feature
- If it has **low correlation** with the target → consider dropping the column entirely
- For categorical columns → add a "Unknown" category
- **Never** blindly drop rows when 40% are missing — you'd lose too much data

---

### IQ5. What is the difference between Ridge and Lasso Regression?
**A:** Both are regularized versions of Linear Regression that add a penalty term to prevent overfitting:
- **Ridge (L2):** Adds penalty = λ × Σ(coefficients²). Shrinks all coefficients toward zero but never to exactly zero. Good when all features contribute.
- **Lasso (L1):** Adds penalty = λ × Σ|coefficients|. Can shrink coefficients to exactly zero — performs automatic feature selection.
- **ElasticNet:** Combination of both Ridge and Lasso.
In this project, plain Linear Regression was sufficient, but Ridge/Lasso would be next steps.

---

### IQ6. How would you deploy this model as a web application?
**A:** I would:
1. Save the trained model using `joblib.dump(model, 'model.pkl')`
2. Build a REST API with **FastAPI** or **Flask** — accepts house features as JSON, returns predicted price
3. Create a simple frontend using **Streamlit** (pure Python — no HTML/JS needed)
4. Containerize with **Docker** for consistent deployment
5. Host on **Heroku, AWS, or Google Cloud Run**
6. Add monitoring to track prediction drift over time

---

### IQ7. What is data leakage and how do you prevent it?
**A:** Data leakage occurs when information from the test set (or future data) "leaks" into the training process, giving falsely optimistic results. Examples:
- Fitting a scaler on ALL data before splitting → test statistics influence training normalization
- Including post-event features (e.g., final sale price components as a feature)
**Prevention:**
- Always split FIRST, then fit preprocessing on training data only
- Use scikit-learn's `Pipeline` to enforce this automatically
- Carefully audit all feature creation steps

---

### IQ8. How would you explain this model to a non-technical stakeholder?
**A:** "Our model learns from 1,000 past home sales. It found that the most important factors driving price are: home size, location, and school quality. Once trained, it can estimate the price of any new home in about a millisecond. It's right within about $42,000 on average — not perfect, but it's a strong starting point that helps buyers and sellers negotiate more fairly. Think of it like a very experienced appraiser who has studied 1,000 past sales."

---

### IQ9. What is cross-validation and why is it better than a single train-test split?
**A:** Cross-validation (CV) — specifically K-Fold CV — divides data into K equal folds. The model is trained K times, each time using K-1 folds for training and 1 for testing. Final score = average across all K runs. **Why it's better:**
- More reliable estimate of model performance — less sensitive to one "lucky" or "unlucky" split
- Makes use of all data for both training and testing
- Standard practice is 5-fold or 10-fold CV
- In scikit-learn: `cross_val_score(model, X, y, cv=5, scoring='r2')`

---

### IQ10. What is the bias-variance tradeoff?
**A:** Every ML model faces a tradeoff between two sources of error:
- **Bias:** Error from overly simplistic assumptions (underfitting). A linear model assuming a non-linear relationship has high bias.
- **Variance:** Error from sensitivity to fluctuations in training data (overfitting). A very complex model has high variance.
- **Goal:** Find the sweet spot with low bias AND low variance
- **Linear Regression** tends to have high bias (assumes linearity) but low variance
- **Deep Neural Networks** tend to have low bias but high variance (need lots of data + regularization)

---

*These questions cover core concepts that will arise in both academic viva examinations and technical interviews for Data Science and ML roles.*
