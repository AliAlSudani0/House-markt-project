# 🏡 King County Housing Market — Exploratory Data Analysis  
### *A Data Science Project for Real-Estate Investment Insights*

---

## 📌 1. Project Overview
This project explores the **King County (Seattle) Housing Dataset** to understand what drives property prices and how different home features impact value.  
Through Exploratory Data Analysis (EDA), we evaluate three hypotheses and provide insights tailored to a real-estate investment client seeking profitable opportunities.

The analysis focuses on:
- Identifying key price drivers  
- Understanding the impact of renovation, floors, and location  
- Evaluating house characteristics across the region  
- Transforming data findings into clear business recommendations  

---

## 🧑‍💼 2. Client Background & Goals
The client is a property investor looking for **data-backed guidance** on:

- Whether renovations increase property value  
- What types of homes offer the best returns  
- Which neighborhoods have larger or higher-value properties  
- How to prioritize purchases and improvements

Our EDA directly answers these questions.

---

## 🗂️ 3. Dataset Overview

- **Source:** King County House Sales dataset  
- **Rows:** 21,597  
- **Features:** 21  
- **Time Period:** 2014–2015 (house sale dates)  
- **Region:** Seattle and surrounding zipcodes  

Key variables include:
- Price, bedrooms, bathrooms, sqft living, grade, condition  
- Latitude & longitude  
- Floors, renovation year  
- Zipcode  

Dataset stored locally due to `.gitignore` protection.

---

## 🔧 4. Data Cleaning Summary

Minimal and defensible cleaning was performed to avoid distorting the dataset.

### ✔ Renovation data  
`yr_renovated` has many missing values → **not imputed**  
A new feature **renovated_flag** (1 = has renovation year) was created instead.

### ✔ View  
Small number of missing values (≈0.3%) → filled using **mode**.

### ✔ Basement & Waterfront  
Missing values left as-is (not required for hypotheses).

### ✔ Feature Engineering  
New variables added:

- `house_age`  
- `price_per_sqft`  
- `bedrooms_per_floor`  
- `bedrooms_per_1000_sqft`  

These enhanced the depth of analysis without altering original data integrity.

---

## ❓ 5. Research Questions

1. **Does renovation affect house prices?**  
2. **Do homes with more floors have more bedrooms?**  
3. **Does house size vary across different geographic locations?**

---

## 📐 6. Hypotheses

### **Hypothesis 1 — Renovation & Price**  
Renovated houses tend to have higher prices.

### **Hypothesis 2 — Floors & Bedrooms**  
Homes with more floors contain more bedrooms.

### **Hypothesis 3 — Geography & House Size**  
House size varies significantly based on geographic location.

---

# 📊 7. Analysis & Results

---

## ⭐ Hypothesis 1: Renovation vs Price  
### **Result: Not Supported**

Renovated houses do **not** show higher average prices than non-renovated ones.  
This is partly because renovation records are incomplete and not reliable indicators of true renovation quality.

**Insight:**  
Renovation *year* is not a meaningful predictor of price. Actual renovation quality matters more, but this dataset cannot measure it.

---

## ⭐ Hypothesis 2: Floors vs Bedrooms  
### **Result: Not Supported**

Analysis shows:
- Bedrooms do **not** increase with the number of floors  
- Bedroom density per 1,000 sqft is stable  
- Many 1-floor homes have more bedrooms than 2-floor homes  

But we discovered something important:

### 💡 Additional Insight  
Homes with **more floors tend to have higher quality grade and higher price**,  
not more bedrooms.  
This reveals that **grade (quality)** is the real driver—not the number of floors.

---

## ⭐ Hypothesis 3: Location & House Size  
### **Result: Supported**

Geographic analysis shows:
- Some zipcodes contain significantly larger homes  
- Top zipcodes by home size include **98039, 98040, 98075**  
- Map visualizations confirm geographic clustering of large homes

**Insight:**  
Location meaningfully influences house size, and thus price potential.

---

## 📈 8. Price Driver Analysis (Correlation)

Correlation shows:

| Feature | Correlation with Price |
|--------|------------------------|
| **sqft_living** | 0.70 |
| **grade** | 0.67 |
| **bathrooms** | 0.53 |

### Key takeaway:
**Home size and construction quality are the strongest predictors of price**,  
far more than renovation year or number of floors.

A boxplot of **price by grade** strongly confirms this trend.

---

# 💡 9. Key Insights for the Client

### ✔ Renovation records are unreliable  
Renovated vs non-renovated homes do not differ in price.

### ✔ Floors do not add bedrooms  
Bedroom counts depend on **house size**, not floors.

### ✔ Floors correlate with quality  
Homes with more floors tend to have higher *grade*, which increases price.

### ✔ Location strongly influences house size  
Premium zipcodes contain larger houses and higher market value.

### ✔ The best investment strategy  
Improve **grade** (quality upgrades, remodeling, finishes)  
→ this yields the highest return on investment.

---

# 🧭 10. Recommendations

### 🟦 For Investors
- Prioritize homes with higher **grade** (8+) or upgrade the grade through renovation  
- Look for opportunities in high-value zipcodes (98039, 98040, 98075)  
- Evaluate deals using **price per sqft**  
- Do not rely solely on “renovated” status  
- Choose properties with strong size/quality potential  

### 🟩 For Sellers
- Upgrade kitchen, bathrooms, or materials to boost grade  
- Emphasize home size and quality in listings  
- Renovation year alone will not increase perceived value  

---

# 📁 11. Repository Structure
├── EDA.ipynb
├── README.md
├── requirements.txt
├── charts/
│   ├── floors_vs_bedrooms.png
│   ├── bedroom_density.png
│   ├── renovated_vs_non.png
│   ├── price_by_grade.png
│   ├── correlation_heatmap.png
│   └── zipcode_largest_homes.png
└── data/
└── (dataset not included; protected by .gitignore)

---

# 🔧 12. Environment Setup 

To run the notebook locally:

```bash
pyenv local 3.11.3
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt