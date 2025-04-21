# feature-selection

# HW 12: Feature Selection  
**Output:** HTML Document  

---

## 📘 Objective

The goal of this assignment is to implement a **feature selection algorithm** for linear regression modeling. The algorithm identifies an optimal subset of predictors (independent variables) from a given dataset to maximize the model's **adjusted R²**, improving model performance while avoiding overfitting.

---

## 🧠 Methodology

We use a **greedy forward selection** approach based on adjusted R². The algorithm iteratively selects predictors that, when added to the model, improve the adjusted R² the most. The process continues until no further improvement is found.

---

### 📊 Dataset

- The dataset `auto.csv` contains car-related data.
- The target variable is `price`.
- Predictors include all columns **except**:  
  - `"X"` (index column)  
  - `"make"` (categorical name of the vehicle)  
  - `"price"` (dependent variable)

---

### 🚀 Algorithm Steps

1. **Initialize**:
   - `sp` (selected predictors) as an empty list.
   - `predictors` as all valid independent variables.

2. **Iterate**:
   - For each round:
     - Loop through all predictors not in `sp`.
     - For each candidate `p`, compute adjusted R² for the model using `sp + p`.
     - Select the predictor that gives the highest adjusted R².
   - If the new model’s adjusted R² is greater than the previous one, **add** `p` to `sp`.
   - Otherwise, **terminate** the selection process.

3. **Output**:
   - Print the ordered list of selected predictors.
   - Optionally, run and display the summary of the final linear model using these predictors.

---

## 🧪 Implementation Notes

- We use the `reformulate()` function to **dynamically build formulas** for `lm()`:
  ```r
  reformulate(termlabels = c("weight", "length"), response = "price")
  ```
- The function `optimize()` is recursive, simplifying the logic of repeated selection and model evaluation.

---

## ✅ Output Example

Expected selected predictors:
```r
[1] "weight"       "foreign"      "length"       "displacement" "headroom"     "turn"
```

Final model:
```r
lm(price ~ weight + foreign + length + displacement + turn, data = auto)
```

---

## 🧩 Dependencies

- `tidyverse`
- `ggplot2`

---

## 📎 Files

- `HW12_FeatureSelection.Rmd`
- `auto.csv` *(Must be in the working directory)*

---
