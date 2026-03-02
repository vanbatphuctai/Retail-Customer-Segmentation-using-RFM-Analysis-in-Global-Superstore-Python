# 🛒 Retail Marketing Strategy & RFM Customer Segmentation | Python

**Author:** Van Bat Phuc Tai  
**Tools Used:** Python (Pandas, NumPy, Matplotlib, Seaborn)

---

# 📑 Table of Contents

- 📌 [1. Background & Overview](#-1-background--overview)  
- 📂 [2. Dataset Description & Data Structure](#-2-dataset-description--data-structure)  
- 🧹 [3. Data Cleaning & Preprocessing](#-3-data-cleaning--preprocessing)  
- 🔍 [4. Exploratory Data Analysis (EDA)](#-4-exploratory-data-analysis-eda)  
- 🧮 [5. Apply RFM Model](#-5-apply-rfm-model)  
- 📊 [6. Visualization & Analysis](#-6-visualization--analysis)  
- 💡 [7. Insight & Recommendation](#-7-insight--recommendation)  
---

# 1️⃣ 📌 Background & Overview

## 🎯 Objective

### 📖 What is this project about?

The **Marketing team** aims to launch **personalized campaigns** for **customer retention and acquisition** during peak sales periods. However, with a dataset exceeding **540,000+ transactions**, manual segmentation is no longer feasible.

To address this challenge, the **RFM model (Recency, Frequency, Monetary)** is applied using **Python (Google Colab)** to systematically classify customers based on purchasing behavior.

This project covers:

- Data preparation & preprocessing  
- RFM score calculation  
- Customer segmentation  
- Data visualization  
- Actionable business recommendations  

---

### 👤 Who is this project for?

✔️ **Marketing Department**  
✔️ **Sales Team**  
✔️ **Business Decision-Makers & Stakeholders**

---

## ❓ Business Questions

- How can we **segment customers effectively** using the RFM model?  
- Which customer groups should be **prioritized for retention and promotional campaigns**?  
- What actionable insights can improve **marketing performance and engagement**?  
- What strategies should be applied to **different customer segments** to maximize value?

---

## 🔎 RFM Analysis Overview

### Why use RFM?

**RFM (Recency – Frequency – Monetary)** is a proven customer analysis framework used to evaluate purchasing behavior and customer value.

Each customer is assigned a score based on:

- **Recency** → How recently did the customer make a purchase?  
- **Frequency** → How often does the customer purchase?  
- **Monetary** → How much does the customer spend?  

By applying RFM, businesses can:

- Identify **high-value customers**
- Detect **at-risk customers**
- Optimize **marketing targeting strategies**
- Improve **customer lifetime value (CLV)**

---

# 2️⃣ 📂 Dataset Description & Data Structure

## 📌 Data Source

- **Source:** E-commerce Retail Dataset  
- **Size:** 541,910 rows × 8 columns  
- **Format:** `.xlsx` (2 sheets)  

---

## 📂 Data Structure & Relationships

### 1️⃣ Tables Used

The dataset consists of two sheets:

- **Sheet 1 – E-commerce Retail**  
  Contains transaction-level data including:
  - Invoice number  
  - Product details  
  - Customer ID  
  - Quantity  
  - Price  
  - Invoice date  

- **Sheet 2 – Segmentation**  
  Contains:
  - RFM scores  
  - Customer segment labels  

---

### 2️⃣ Table Schema & Data Snapshot

#### 📌 Sheet 1: E-commerce Retail

### 📋 Table Schema: E-commerce Retail

<details>
<summary>📂 **Dataset Schema** (Click to expand)</summary>

<br>

| Column Name | Data Type | Description |
|-------------|------------|-------------|
| **InvoiceNo** | `object` | Unique invoice number for each transaction (6-digit). If it starts with **'C'**, it indicates a cancellation. |
| **StockCode** | `object` | Unique product (item) code (5-digit). |
| **Description** | `object` | Product (item) name. |
| **Quantity** | `int64` | The number of units purchased per transaction. |
| **InvoiceDate** | `datetime64[ns]` | Date and time when the transaction occurred. |
| **UnitPrice** | `float64` | Price per unit of the product in sterling. |
| **CustomerID** | `float64` | Unique 5-digit identifier for each customer. |
| **Country** | `object` | Name of the country where the customer resides. |

</details>

---

#### 📌 Sheet 2: Customer Segmentation

### 📊 Customer Segmentation & RFM Scores

<details>
<summary>📊 **RFM Segmentation Mapping** (Click to expand)</summary>

<br>

| Segment | RFM Score |
|----------|------------|
| **Champions** | 555, 554, 544, 545, 454, 455, 445 |
| **Loyal** | 543, 444, 435, 355, 354, 345, 344, 335 |
| **Potential Loyalist** | 553, 551, 552, 541, 542, 533, 532, 531, 452, 451, 442, 441, 431, 453, 433, 432, 423, 353, 352, 351, 342, 341, 333, 323 |
| **New Customers** | 512, 511, 422, 421, 412, 411, 311 |
| **Promising** | 525, 524, 523, 522, 521, 515, 514, 513, 425, 424, 413, 414, 415, 315, 314, 313 |
| **Need Attention** | 535, 534, 443, 434, 343, 334, 325, 324 |
| **About To Sleep** | 331, 321, 312, 221, 213, 231, 241, 251 |
| **At Risk** | 255, 254, 245, 244, 253, 252, 243, 242, 235, 234, 225, 224, 153, 152, 145, 143, 142, 135, 134, 133, 125, 124 |
| **Cannot Lose Them** | 155, 154, 144, 214, 215, 115, 114, 113 |
| **Hibernating Customers** | 332, 322, 233, 232, 223, 222, 132, 123, 122, 212, 211 |
| **Lost Customers** | 111, 112, 121, 131, 141, 151 |

</details>

---

# 3️⃣ 🧹 Data Cleaning & Preprocessing

Before applying RFM, the dataset underwent several cleaning steps:

### ✅ 1. Handle Missing Values
- Removed records with missing **CustomerID**
- Checked null values in key transaction fields

### ✅ 2. Remove Duplicates
- Dropped duplicated transaction records

### ✅ 3. Handle Invalid Transactions
- Removed negative quantities (returned/cancelled orders)
- Filtered out zero or negative unit prices

### ✅ 4. Convert Data Types
- Converted `InvoiceDate` to datetime format
- Ensured numeric columns are correctly typed

### ✅ 5. Create Derived Metrics
- Calculated **TotalRevenue = Quantity × UnitPrice**
- Determined **Snapshot Date** for Recency calculation

---

## 📌 Clean Dataset Outcome

- Valid transactions only
- Structured data ready for **RFM score calculation**
- Improved data reliability for analytical modeling

---
