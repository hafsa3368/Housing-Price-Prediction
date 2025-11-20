# 🏡 California Housing Price Prediction

Machine Learning Regression Project

## 📌 **Project Summary**

This project predicts **median house values** using the California Housing dataset. The goal is to build a complete end-to-end machine learning workflow including data preprocessing, feature engineering, modeling, and evaluation.

The dataset contains key features such as population, total rooms, median income, latitude/longitude, and ocean proximity. After cleaning and transforming the data, multiple regression models were explored, including **Linear Regression** and **Random Forest Regressor** (with GridSearchCV tuning).

The final model provides reliable prediction performance and demonstrates the ability to work with real-world noisy data.

---

## 🚀 **Key Steps in the Project**

### **1. Data Cleaning**

* Handled missing values using **median imputation**
* Converted categorical column `ocean_proximity` using **One-Hot Encoding**
* Ensured all column names were **string type** to prevent pipeline errors
* Removed any rows containing NaN after transformation

### **2. Feature Engineering**

Created additional helpful features:

* `bedroom_ratio = total_bedrooms / total_rooms`
* `household_rooms = total_rooms / households`

These features improved the model’s predictive performance.

### **3. Preprocessing Pipeline**

Used **ColumnTransformer** to combine:

* StandardScaler for numerical features
* SimpleImputer (median)
* OneHotEncoder for categorical features

This created a consistent, reproducible preprocessing workflow.

### **4. Model Training**

Models trained:

* **Linear Regression**
* **RandomForestRegressor**
* **GridSearchCV** for hyperparameter tuning

### **5. Model Evaluation**

Evaluated using:

* R² Score
* Mean Squared Error (MSE)
* Test set performance after scaling
* Comparison of default vs tuned Random Forest

---

## ⚠️ **Challenges Faced During the Project**

### **1. Non-numeric column errors**

The dataset contained categorical values such as `'INLAND'`, `'NEAR BAY'`, etc.
Scaling failed with:

```
ValueError: could not convert string to float
```

**Fix:** Used OneHotEncoder inside a preprocessing pipeline.

---

### **2. Column type mismatch**

Error:

```
TypeError: input has ['int','str'] feature names
```

**Cause:** Mixed integer and string column names.
**Fix:** Converted all column names:

```python
train_data.columns = train_data.columns.astype(str)
```

---

### **3. NaN Values After Transformation**

Even after preprocessing, some transformed arrays still had NaN values causing:

```
ValueError: Input contains NaN
```

**Fix:** Checked each stage and ensured imputation happened before scaling.

---

### **4. Inconsistent Train/Test Sizes**

Got error from GridSearchCV:

```
ValueError: Found input variables with inconsistent numbers of samples
```

**Cause:** Using scaled X with unscaled y or vice versa.
**Fix:** Repeated the same train-test split and ensured preprocessing applied consistently.

---

### **5. Pipeline Import Errors / NameErrors**

Example:

```
NameError: name 'GridSearchCV' is not defined
```

**Fix:** Clean imports at the top:

```python
from sklearn.model_selection import GridSearchCV
---

## 📝 **Conclusion**

This project demonstrates the complete ML lifecycle:

* Cleaning real-world data
* Building advanced preprocessing pipelines
* Training and tuning regression models
* Handling common machine-learning errors
* Ensuring reproducible, scalable code

Just tell me **“Make GitHub README fully”** and I’ll generate the complete file.
