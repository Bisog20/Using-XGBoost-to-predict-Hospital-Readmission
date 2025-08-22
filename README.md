# 🏥 Predicting Hospital Readmissions Using Hierarchical XGBoost

Hospital readmissions within 30 days are costly for healthcare systems and risky for patients.  
This project explores whether machine learning can **predict if a patient will be readmitted within 30 days, after 30 days, or not at all**, using a **hierarchical classification approach with XGBoost**.  

---

## 📊 Dataset
- **Source:** [Diabetes 130-US hospitals dataset (UCI Repository)](https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+readmission)  
- **Size:** 100,000+ hospital admissions across 130 US hospitals (1999–2008)  
- **Target Variable:** Readmission status:  
  - `<30` → readmitted within 30 days  
  - `>30` → readmitted after 30 days  
  - `NO` → not readmitted  

🔑 **Features include:**  
- Demographics (age, gender, race)  
- Medical history (diagnoses, comorbidities)  
- Hospitalization details (admission type, discharge disposition, number of visits)  
- Medications (changes in insulin, number of prescriptions)  

---

## 🏗 Methodology

This project uses a **two-stage hierarchical classification strategy**:

1. **Stage 1 – Binary Classification**  
   Predict whether the patient will be readmitted (Yes/No).  

2. **Stage 2 – Multi-class Classification**  
   If "Yes", classify into `<30 days` or `>30 days`.  

This approach helps address **class imbalance** and separates the high-risk patients more clearly.  

---

## ⚙️ Model
- **Algorithm:** XGBoost (Extreme Gradient Boosting)  
- **Evaluation Metrics:** Accuracy, Precision, Recall, F1-score, Confusion Matrix  

---

## 📈 Results

### Classification Report
| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| `<30` | 1.00 | 1.00 | 1.00 | 3425 |
| `>30` | 0.62 | 0.51 | 0.56 | 10644 |
| `NO`  | 0.71 | 0.80 | 0.75 | 16461 |
| **Accuracy** |       |       | **0.72** | 30530 |
| **Macro Avg** | 0.78 | 0.77 | 0.77 | 30530 |
| **Weighted Avg** | 0.73 | 0.72 | 0.72 | 30530 |

✅ **Strengths**  
- Very high accuracy in detecting `<30 days` readmissions (most critical class).  
- Reasonably good performance for distinguishing `NO` readmissions.  

⚠️ **Challenges**  
- Overlap between `>30 days` and `NO` categories reduced precision.  
- Dataset imbalance contributed to skewed results.  

---

## 🔍 Interpretation
- The model shows **high reliability in identifying patients at risk of readmission within 30 days**, which is crucial for preventive care and cost reduction.  
- However, predicting between `>30 days` and `NO` is less accurate, meaning hospitals might need additional data (e.g., follow-up visits, lifestyle factors).  

---

## 🚧 Limitations
- Dataset is **imbalanced** (far fewer `<30 days` cases compared to others).  
- Limited to **diabetes patients only**.  
- Real-world hospital data may include unobserved confounders not in this dataset.  

---

## 💡 Future Work
- Apply **SMOTE or class-weight adjustments** to handle imbalance.  
- Add **temporal features** (time between admissions).  
- Use **Explainable AI tools (SHAP, LIME)** to understand model decisions.  
- Expand to **multi-disease datasets** for broader generalization.  

---

