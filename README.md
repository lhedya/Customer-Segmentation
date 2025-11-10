# 🛒 Customer Segmentation Analysis — Global E-Commerce Sales  
**By: Lhedya Monica Ismon**

---

## 📘 Project Overview
This project aims to perform **customer segmentation** using the **RFM (Recency, Frequency, Monetary)** approach on the **Global E-Commerce Sales** dataset from Kaggle.  
The goal is to help companies understand customer shopping behavior, identify high-value customers, and provide actionable marketing strategy recommendations.

---

## 🎯 Business Objectives

### **Primary Objective**
Segment customers based on their purchasing behavior to improve the effectiveness of marketing strategies.

### **Specific Objectives**
- Identify customers with the highest contribution to total sales.  
- Determine product categories with the highest revenue.  
- Analyze customer and revenue distribution by region.  
- Perform customer segmentation using the **RFM method**.  
- Evaluate revenue distribution within each customer segment.  
- Provide **data-driven insights and recommendations** for targeted marketing.

---

## 🧾 Dataset Information
**Source:** [Global E-Commerce Sales (Kaggle)](https://www.kaggle.com/datasets/tyagi586/global-e-commerce-sales)  
**Records:** ~500,000 transactions (2022–2024)

| Column | Description |
|---------|-------------|
| `Transaction Date` | Date of purchase (YYYY-MM-DD) |
| `Customer ID` | Unique identifier for each customer |
| `Region` | Geographic region (Asia, Europe, America, etc.) |
| `Product Category` | Type of product purchased |
| `Price` & `Quantity` | Product price and units sold |
| `Discount (%)` | Discount applied to the purchase |
| `Total Revenue` | Final amount after discount |
| `Payment Method` | Payment type (Credit Card, PayPal, Bank Transfer, Crypto, etc.) |

---

## ⚙️ Data Preprocessing (Python)
The preprocessing and feature engineering steps were conducted in **Python (Jupyter Notebook)**.

### **Steps:**
1. **Load Dataset**
   ```python
   df = pd.read_csv('global_ecommerce_sales.csv')
   ```
2. **Data Cleaning**
   - No missing values found  
   - No duplicate data  
   - Converted date columns to datetime format  
   - Adjusted data types for numeric columns  

3. **Feature Engineering**
   - Added `Total_Spend = Quantity * Price`  
   - Created the **RFM table**:
     ```python
     rfm = df.groupby('Customer ID').agg({
         'Transaction Date': lambda x: (df['Transaction Date'].max() - x.max()).days,
         'Customer ID': 'count',
         'Total_Spend': 'sum'
     })
     rfm.columns = ['Recency', 'Frequency', 'Monetary']
     ```

4. **RFM Scoring**
   - Determined cutoffs for each metric based on quartiles.  
   - Assigned scores from 1–4 for Recency, Frequency, and Monetary.  
   - Categorized customers into six RFM segments:
     - **Champions**
     - **Loyal**
     - **Potential Royalists**
     - **At Risk**
     - **Hibernating**
     - **Lost**

---

## 📊 Data Visualization & Segmentation Dashboard (Power BI)
After data preprocessing and RFM analysis, the results were exported to **Power BI** for interactive visualization.

### **Dashboards Created:**
1. **EDA Dashboard**
   - Sales distribution by product category.  
   - Regional sales comparison.  
   - Most common payment methods.

2. **Customer Segmentation Dashboard**
   - Customer distribution by RFM segments.  
   - Revenue contribution by segment.  
   - Segment performance trends over time.

---

## 💡 Key Findings

### **Exploratory Data Analysis**
- **Top-selling category:** *Toys & Games* (≈ Rp 8.6 billion)  
- **Region with the most customers:** *Asia* (56,527 customers, Rp 11.5 billion total sales)  
- **Most used payment method:** *Bank Transfer*

### **RFM Segmentation**
- **Largest segment:** Hibernating (2,700 customers)  
- **Highest revenue segment:** At Risk (Rp 20.2 billion)  
- **Most valuable (but smallest) segment:** Champions

---

## 🧠 Actionable Insights & Recommendations

| Issue | Insight | Recommendation |
|--------|----------|----------------|
| Ineffective marketing campaigns | High discounts across all categories do not drive the highest revenue | Use discounts to retain at-risk or inactive customers, not high-value ones |
| Lack of marketing differentiation | Sales and payment distribution are almost equal across regions | Design region- and segment-specific campaigns (e.g., Champions in Asia, Potential in Africa) |
| Difficulty identifying high-value customers | Small “Champions” group contributes significantly to total revenue | Create a **VIP customer list**, and apply **upselling/cross-selling** for Loyal and Potential segments |

---

## 🧰 Tech Stack
- **Python** → pandas, numpy, matplotlib, seaborn  
- **Jupyter Notebook** → data preprocessing & analysis  
- **Power BI** → visualization and interactive dashboards  
- **Excel/CSV** → intermediate storage and export format  

---

## 📈 Output Files
| File | Description |
|------|--------------|
| `Final_Project_Global_E_Commerce_Sales_Lhedya_Monica_Ismon.ipynb` | Python Notebook for preprocessing and RFM analysis |
| `RFM_Results.csv` | Final customer segmentation results |
| `PowerBI_CustomerSegmentation.pbix` | Power BI dashboard |
| `Final_Project_Lhedya_Monica_Ismon.pdf` | Final report |

---

## 👩‍💻 Author
**Lhedya Monica Ismon**  
📧 Email: [lhedyamonica21@gmail.com](mailto:lhedyamonica21@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/lhedya/)

---

✨ *This project was developed as part of a Data Analyst Final Project — Customer Segmentation using RFM Analysis.*
