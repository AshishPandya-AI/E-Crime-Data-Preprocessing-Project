
# 🚨 E-Crime Data Preprocessing & Profiling Project

This project focuses on comprehensive **exploratory data analysis (EDA)** and **data preprocessing** of an E-Crime dataset using Python. The dataset contains over 50,000 records and a wide variety of both **numerical and categorical attributes**. The goal is to prepare the data for future modeling by performing attribute classification, outlier detection, missing value handling, statistical profiling, and dimensionality reduction.

---

## 📌 Project Overview

- **Dataset**: E-Crime Incident Data (CSV format)
- **Total Records**: ~50,000+
- **Attributes**: 15+ diverse attributes
- **Tools Used**: Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy
- **Notebook**: `DE_Project_Ashish.ipynb`
- **Author**: Ashish Pandya

---

## 🎯 Project Objectives

- Identify and classify each attribute based on its **analytical type**.
- Perform detailed **data visualization** for each attribute and combinations.
- Detect and handle **missing values**, **bad data**, and **outliers**.
- Run **statistical analysis** to evaluate feature importance.
- Apply **correlation analysis** to remove redundant attributes.
- Document the **data profile** for every final attribute.

---

## 🧠 Attribute Type Classification

The dataset contains both **numerical (ratio-scale)** and **categorical (nominal/ordinal)** attributes.

### 🔢 Numerical Attributes (Ratio-Scale)

| Attribute              | Description                                |
|------------------------|--------------------------------------------|
| `Longitude`            | Geographic coordinate                      |
| `Latitude`             | Geographic coordinate                      |
| `Total Incidents`      | Dropped – only 1 unique value              |
| `Number of Witnesses`  | Count of witnesses per crime               |
| `Crime Severity Score` | Composite score assigned to crime severity |

### 🔤 Categorical Attributes

| Attribute         | Type     | Description                           |
|------------------|----------|---------------------------------------|
| `CrimeDate`       | Nominal  | Date of the crime                     |
| `CrimeTime`       | Nominal  | Time of occurrence                    |
| `CrimeCode`       | Nominal  | Coded classification of crime type   |
| `Location`        | Nominal  | General area of occurrence            |
| `Description`     | Nominal  | Textual description of crime          |
| `Inside/Outside`  | Nominal  | Whether the crime occurred indoors or outdoors |
| `Weapon`          | Nominal  | Weapon used in the crime              |
| `Post`            | Nominal  | Police post assigned                  |
| `District`        | Nominal  | Police district                       |
| `Neighborhood`    | Nominal  | Community name                        |
| `Location 1`      | Nominal  | Lat/Long location text field          |
| `Premise`         | Ordinal  | Property type where crime occurred    |
| `Month`, `Day`, `Year` | Derived fields from `CrimeDate`          |

---

## 📈 Attribute Visualization

Every attribute in the dataset has been visualized using appropriate techniques:
- **Histograms** and **Boxplots** for numerical attributes
- **Bar charts** and **Countplots** for categorical attributes
- **Heatmaps** for correlation analysis
- **Grouped bar plots** and **pairwise visualizations** for multi-attribute insights

Due to the volume of graphs, screenshots are not provided here — but all plots are available inside the notebook (`DE_Project_Ashish(F).ipynb`).

---

## 🧹 Data Preprocessing – Phase 1

### ✅ Missing Value Summary

| Attribute       | Missing % | Action Taken / Reason                |
|----------------|------------|--------------------------------------|
| Weapon          | 64.15%     | Retained for real-world relevance   |
| Post            | 0.13%      | Minor → kept or imputed             |
| District        | 0.03%      | Minor → kept as-is                  |
| Neighborhood    | 0.82%      | Minor → retained                    |
| Location 1      | 0.60%      | Kept as-is                          |
| Premise         | 6.08%      | Medium → retained or imputed        |

---

### 🧪 Outlier Handling

- Applied **IQR** and **Z-score** for detection
- Fixed outliers in:
  - `Number of Witnesses`: to improve consistency and reduce skew
  - `Latitude`: cleaned invalid entries to fix map-related issues

---

## 🔁 Feature Transformation

- Mapped month names to numeric format for better sorting and analysis:
```python
reverse_month_map = { 'January': 1, ..., 'December': 12 }
df['Month'] = df['Month'].map(reverse_month_map)
```

- Parsed date-time features
- Standardized categories like `Inside/Outside`
- Dropped: `Total Incidents` due to no variance (only 1 unique value)

---

## 📊 Statistical Profiling

- Calculated:
  - Central tendencies: mean, median, mode
  - Spread: std deviation, IQR
  - Shape: skewness, kurtosis
- Identified high-importance features:
  - 🔥 `Post`, `Crime Severity Score`, `Number of Witnesses`, `Day`
- Identified low-value or redundant:
  - ❄️ `Longitude`, `Latitude`, `Year`, `Missing_Weapon`

---

## 🔄 Correlation Analysis

- Used heatmaps and pairwise plots
- Found redundancy between:
  - `District` & `Post`
  - `Latitude` & `Location 1`
- Removed up to 3 attributes to reduce noise

---

## 🧾 Final Attribute Profile

| Attribute             | Type        | Status       | Notes                                  |
|----------------------|-------------|--------------|----------------------------------------|
| CrimeDate            | Nominal     | Parsed       | Used to extract Month, Day, Year       |
| CrimeTime            | Nominal     | Retained     | No missing                             |
| CrimeCode            | Nominal     | Retained     | Frequency encoded                      |
| Location             | Nominal     | Retained     | Text normalization applied             |
| Description          | Nominal     | Retained     | Cleaned text                           |
| Inside/Outside       | Nominal     | Cleaned      | Standardized values                    |
| Weapon               | Nominal     | Kept         | Despite 64% missing                    |
| Post                 | Nominal     | Important    | Minor missing handled                  |
| District             | Nominal     | Dropped      | Redundant with `Post`                  |
| Neighborhood         | Nominal     | Retained     | Low missing                            |
| Premise              | Ordinal     | Retained     | Minor missing handled                  |
| Latitude             | Ratio       | Retained     | Outliers cleaned                       |
| Longitude            | Ratio       | Retained     | Low importance                         |
| Number of Witnesses  | Ratio       | Cleaned      | Outliers capped                        |
| Crime Severity Score | Ratio       | Important    | Retained                               |
| Month                | Ordinal     | Transformed  | From `CrimeDate`                       |
| Day                  | Ordinal     | Important    | From `CrimeDate`                       |
| Year                 | Ordinal     | Retained     | Low importance                         |

---

## 🗂 Folder Structure

```
E-Crime-Data-Preprocessing-Project/
│
├── dataset/
│   └── Data_E_crime_dataset_Project.csv
│
├── notebook/
│   └── DE_Project_Ashish.ipynb
│
├── README.md
└── .gitignore
```

---

## 🔍 Key Outcomes

- Fully cleaned, transformed, and statistically validated dataset
- Visualized and profiled all attributes
- Logical justification for all drops, fixes, and transformations
- Final dataset is model-ready and reusable
- Covers essential data engineering skills: profiling, cleansing, outlier & correlation analysis

---

## 👨‍💻 Author

**Ashish Pandya**  
📘 Data Analytics | EDA & Preprocessing Focus  
📍 Regina, SK, Canada  
🔗 GitHub: [github.com/AshishPandya-AI](https://github.com/AshishPandya-AI)

---

## 📃 License

This project is open-source and available under the MIT License for academic and research use.
