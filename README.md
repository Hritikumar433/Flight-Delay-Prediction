# ✈️ Flight Delay Prediction

End-to-end ML pipeline for predicting flight delays using **4.5M+ flight records** with optimized data processing and GPU-accelerated models.

---

## 📌 Overview
This project covers:
- Data ingestion from multiple large CSVs  
- Conversion to **Parquet** for efficiency  
- Memory-safe cleaning using **PyArrow (chunked processing)**  
- Feature engineering (time, calendar, statistical encodings)  
- Baseline + tuned ML models  

---

## ⚙️ Pipeline

**1. Data Processing**
- Merged 7 CSV files → 4.5M rows  
- Converted to Parquet (faster + smaller)  
- Cleaned in chunks (200k rows)

**2. Feature Engineering**
- Temporal: `IsWeekend`, `MonthPart`  
- Time: `DepHour`, `IsPeakDep`  
- Flight: `IsLongHaul`  
- Target Encoding: airline + airport delay history  

**3. Filtering**
- Removed cancelled/diverted flights  
- Dropped missing critical values  
- Final dataset: **~4.4M rows, ~22 features**

---

## 🤖 Models

### 🌲 Random Forest (GPU - cuML)
- MAE: ~22.35  
- RMSE: ~41.44  

### ⚡ XGBoost (Baseline)
- MAE: ~21.79  
- RMSE: ~40.17  

### 🚀 Tuned XGBoost (Best)
```python
{
  "learning_rate": 0.04,
  "max_depth": 8,
  "min_child_weight": 10,
  "n_estimators": 800
}
````

**Performance:**

* MAE: **~16.43**
* RMSE: ~43.91

---

## 📊 Insights

* ±5 min: **70% accuracy**
* ±10 min: **80% accuracy**
* ±15 min: **84% accuracy**

**Error by severity:**

* Small delays → well predicted
* Large delays → high error

📌 Flight delays are **highly noisy**, limiting R² performance.

---

## 🛠 Tech Stack



## 🚀 Run

```bash
pip install pandas numpy pyarrow scikit-learn xgboost cuml matplotlib seaborn
jupyter notebook
```

---

## 📌 Key Takeaways

* Efficient data handling is critical at scale
* Feature engineering drives performance
* Extreme delays remain hard to predict

---
