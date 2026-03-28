# 🛒 SmartCart — E-commerce Customer Segmentation System

An end-to-end **Unsupervised Machine Learning** project that segments e-commerce customers into distinct groups based on their income, spending behavior, and purchase patterns — enabling targeted marketing strategies.

---

## 📌 Problem Statement

E-commerce businesses struggle to personalize marketing for thousands of customers. This project uses clustering techniques to identify **4 distinct customer segments**, helping businesses tailor campaigns, optimize budgets, and improve ROI.

---

## 📂 Dataset

| Feature | Description |
|---|---|
| `Income` | Annual household income |
| `Year_Birth` | Customer's birth year |
| `Education` | Education level |
| `Marital_Status` | Marital status |
| `Kidhome` / `Teenhome` | Number of kids/teens at home |
| `Dt_Customer` | Date of enrollment |
| `Recency` | Days since last purchase |
| `MntWines`, `MntFruits`, etc. | Amount spent on product categories |
| `NumWebPurchases`, `NumStorePurchases`, etc. | Purchase channel counts |
| `NumWebVisitsMonth` | Monthly website visits |
| `Response` | Response to last marketing campaign |

**Size:** 2,240 customers × 22 features

---

## 🔧 Tech Stack

- **Python 3**
- **Pandas** — data manipulation
- **Matplotlib / Seaborn** — EDA & visualization
- **Scikit-learn** — preprocessing, PCA, KMeans, Agglomerative Clustering
- **Kneed** — automatic elbow point detection

---

## 🚀 Project Pipeline

```
Raw CSV → EDA → Data Cleaning → Feature Engineering → Encoding → Scaling → PCA → Clustering → Insights
```

### 1. 🔍 Exploratory Data Analysis
- Checked shape, null values, data types
- Pair plots for feature relationships
- Correlation heatmap (key finding: Income ↔ Total Spending = **0.79**)

### 2. 🧹 Data Preprocessing
- Imputed missing `Income` values with **median**
- Removed outliers: Age > 90 and Income > 6,00,000

### 3. ⚙️ Feature Engineering
| New Feature | Formula |
|---|---|
| `Age` | `2026 - Year_Birth` |
| `Total_Spending` | Sum of all 6 product spend columns |
| `Total_Children` | `Kidhome + Teenhome` |
| `Customer_Tenure_Days` | Days since joining |
| `Education` | Grouped into 3 levels (Undergraduate / Graduate / Postgraduate) |
| `Living_With` | Simplified to Partner / Alone |

### 4. 🔢 Encoding & Scaling
- **OneHotEncoding** on `Education` and `Living_With`
- **StandardScaler** applied to all features before PCA

### 5. 📉 Dimensionality Reduction (PCA)
- Reduced to **3 principal components**
- 3D scatter plot for visual cluster separation

### 6. 🔍 Optimal K Selection
- **Elbow Method** (WCSS) + **KneeLocator** for automatic detection
- **Silhouette Score** validation
- Combined dual-axis plot → Optimal K = **4**

### 7. 🏷️ Clustering
- **KMeans** (n=4) — initial clustering
- **Agglomerative Clustering** with Ward linkage (n=4) — final model
- Cluster labels assigned back to original feature space

---

## 📊 Cluster Results

| Cluster | Color | Profile | Strategy |
|---|---|---|---|
| **0** | 🔴 Red | Low–Moderate Income, Low–Moderate Spending, More Children, Partner | Discounts & Coupons |
| **1** | 🔵 Blue | High Income, High Spending, Fewer Children, Partner | Loyalty Programs |
| **2** | 🟡 Yellow | Low Income, Low Spending, More Children, Alone | Sales & Heavy Discounts |
| **3** | 🟢 Green | Moderate–High Income, High Spending, Alone, **Best campaign response** | Premium Services |

> 💡 **Cluster 3 (Green)** = Best ROI segment. Fewest children, alone, highly responsive to campaigns → ideal target for premium offers.

---

## 📈 Key Findings

- **Income → Total Spending** correlation: `+0.79` (strongest)
- **Income → Web Visits** correlation: `−0.65` (high-income users prefer store/catalog over web)
- **Spending → Catalog Purchases**: `+0.78`
- High-income customers (Blue cluster) spend the most but respond averagely to campaigns
- Green cluster delivers the **best return on marketing investment**

---

## 📁 File Structure

```
smartcart-segmentation/
│
├── smartcart.ipynb          # Main Jupyter notebook (full pipeline)
├── smartcart_customers.csv  # Dataset
└── README.md
```

---

## ▶️ How to Run

```bash
# 1. Clone the repo
git clone https://github.com/paramramit305-a11y/smartcart-segmentation.git
cd smartcart-segmentation

# 2. Install dependencies
pip install pandas matplotlib seaborn scikit-learn kneed

# 3. Open the notebook
jupyter notebook smartcart.ipynb
```

---

## 🙋‍♀️ Author

**Paramramit** — [@paramramit305-a11y](https://github.com/paramramit305-a11y)

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).
