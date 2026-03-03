# 🛒 Retail Marketing Strategy & RFM Customer Segmentation | Python

**Author:** Van Bat Phuc Tai  
**Tools Used:** Python (Pandas, NumPy, Matplotlib, Seaborn)

---

## 📑 Table of Contents

- 📌 [Background & Overview](#-background--overview)  
- 📂 [Dataset Description & Data Structure](#-dataset-description--data-structure)  
- 🧹 [Data Cleaning & Preprocessing](#-data-cleaning--preprocessing)  
- 🔍 [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)  
- 🧮 [Apply RFM Model](#-apply-rfm-model)  
- 📊 [Visualization & Analysis](#-visualization--analysis)  
- 💡 [Insight & Recommendation](#-insight--recommendation)  
---

## 📌 Background & Overview

### 🎯 Objective

#### 📖 What is this project about?

The **Marketing team** aims to launch **personalized campaigns** for **customer retention and acquisition** during peak sales periods. However, with a dataset exceeding **540,000+ transactions**, manual segmentation is no longer feasible.

To address this challenge, the **RFM model (Recency, Frequency, Monetary)** is applied using **Python (Google Colab)** to systematically classify customers based on purchasing behavior.

This project covers:

- Data preparation & preprocessing  
- RFM score calculation  
- Customer segmentation  
- Data visualization  
- Actionable business recommendations  

---

#### 👤 Who is this project for?

✔️ **Marketing Department**  
✔️ **Sales Team**  
✔️ **Business Decision-Makers & Stakeholders**

---

### ❓ Business Questions

- How can we **segment customers effectively** using the RFM model?  
- Which customer groups should be **prioritized for retention and promotional campaigns**?  
- What actionable insights can improve **marketing performance and engagement**?  
- What strategies should be applied to **different customer segments** to maximize value?

---

### 🔎 RFM Analysis Overview

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

## 📂 Dataset Description & Data Structure

### 📌 Data Source

- **Source:** E-commerce Retail Dataset  
- **Size:** 541,910 rows × 8 columns  
- **Format:** `.xlsx` (2 sheets)  

---

## 📂 Data Structure & Relationships

#### 1. Tables Used

The dataset consists of two sheets:

- **Sheet 1 – E-commerce Retail**  – Contains transaction-level data, including order details, customer IDs, and purchase information.

- **Sheet 2 – Segmentation**  – Stores customer segments along with their RFM scores.

---

#### 2. Table Schema & Data Snapshot

#### 📌 Sheet 1: E-commerce Retail

#### 📋 Table Schema: E-commerce Retail

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

#### 📊 Customer Segmentation & RFM Scores

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

# 🧹 Data Cleaning & Preprocessing

[In 1]:

```python
# Print the first five rows of the dataset
ecommerce_retail.head()
```

[Out 1]:

<img width="900" alt="image" src="https://github.com/user-attachments/assets/85cf956e-5536-4c99-b8fe-0970bd4aa482" />

---

[In 2]:

```python
# Check the general information of df
ecommerce_retail.info()
```

[Out 2]:

<img width="900" alt="image" src="https://github.com/user-attachments/assets/b724fbd1-8851-489a-8c62-d13f17f80f66" />

[In 3]:

```python
# Check Data Summary
ecommerce_retail.describe()
```

[Out 3]:

<img width="900" alt="image" src="https://github.com/user-attachments/assets/ee6eeb17-0f5e-4b88-9aad-de35e1475461" />

[In 4]:

```python
# Check unique values of key categorical columns
ecommerce_retail[['StockCode', 'Description', 'CustomerID', 'Country']].nunique()
```

[Out 4]:

<img width="900" alt="image" src="https://github.com/user-attachments/assets/4ca5e41a-156c-4c8e-9186-797b3d06b2b4" />

---

## 📌 Summary

The dataset contains **541,909 transaction records** including invoice details, product information, customer identifiers, and transaction values.

Initial inspection revealed structural inconsistencies and logical anomalies that could affect revenue calculation and customer segmentation accuracy.

Key concerns include:

- Negative values in `Quantity` and `UnitPrice`
- Missing `CustomerID` (~135K records)
- Extreme outliers in transaction values
- Duplicate records
- Inconsistencies between product identifiers and descriptions

---

## ⚡ Data Quality Insights

### 1️⃣ Product Code–Description Mismatch

A mismatch was identified between:

- **Stock Code count: 4,070**
- **Description count: 4,223**

This discrepancy suggests potential data integrity issues, such as:

- Multiple descriptions assigned to the same StockCode  
- Descriptions not properly linked to valid StockCodes  
- Inconsistent or manually entered product names  
- Missing or duplicated stock identifiers  

This inconsistency required further validation before performing product-level or revenue analysis.

---

### 2️⃣ Missing Customer Identifiers

Approximately **135,000 transactions** contain missing `CustomerID`.

Since RFM modeling relies on customer-level aggregation, these records cannot contribute to segmentation analysis.

Distribution checks show missing IDs are spread across months and countries, suggesting system or input errors rather than region-specific issues.

---

### 3️⃣ Logical Inconsistencies in Transaction Values

Descriptive statistics revealed:

- `Quantity` minimum: -80,995  
- `UnitPrice` minimum: -11,062  

Negative quantities may represent cancellations (credit notes), while others may indicate incorrect descriptions or recording errors.

Negative unit prices are financially invalid and must be excluded.

---

### 4️⃣ Duplicate Records

A total of **10,038 duplicate entries** were detected based on:

`InvoiceNo`, `StockCode`, `InvoiceDate`, and `CustomerID`.

These duplicates may arise from:

- System duplication  
- Split-order recording  
- Data synchronization inconsistencies  

---

## ⚠ Manual Review Required

To address product description inconsistencies and abnormal transactions:

- Suspicious description mismatches were flagged
- Negative quantities were validated against cancellation patterns (`InvoiceNo` starting with "C")
- Erroneous records were marked using an `Error` indicator

This ensured incorrect data was identified before removal.

---

## 🔎 Data Validation & Cleaning Strategy

The cleaning workflow included:

1. Standardizing categorical data types (`InvoiceNo`, `StockCode`, `Description`, `CustomerID`, `Country`)
2. Converting `InvoiceDate` to datetime format
3. Removing canceled invoices (`InvoiceNo` starting with "C")
4. Excluding transactions with:
   - `Quantity < 0`
   - `UnitPrice < 0`
   - Flagged description errors
5. Dropping missing `CustomerID`
6. Resolving duplicates:
   - Removing identical duplicates
   - Aggregating split-order quantities

---

## ✨ Conclusion

Before conducting Exploratory Data Analysis, several structural and logical inconsistencies needed to be resolved:

- Product code–description mismatches  
- Missing customer identifiers  
- Negative and financially invalid transactions  
- Duplicate invoice records  

After systematic validation and correction, the dataset became internally consistent and suitable for reliable revenue analysis and RFM customer segmentation.

---

# 4. 🔍 Exploratory Data Analysis (EDA)

After completing the initial data inspection, the dataset `ecommerce_retail` was cleaned and prepared for analytical tasks.

---

## 🛠 Step 1. Convert to Correct Data Types

To ensure proper grouping and time-based analysis, identifier columns were converted to string format and the date column was standardized.

[In 5]:

```python
# Convert identifier columns to string type
column_list = ["InvoiceNo", "StockCode", "Description", "CustomerID", "Country"]

for col in column_list:
    ecommerce_retail[col] = ecommerce_retail[col].astype(str)

# Convert InvoiceDate to datetime format
ecommerce_retail["InvoiceDate"] = pd.to_datetime(ecommerce_retail["InvoiceDate"])
```

---

## 🛠 Step 2. Remove Invalid Transactions

To ensure revenue accuracy, invalid records were removed using business logic rules.

[In 6]:

```python
# 1. Remove canceled invoices (InvoiceNo starting with "C")
ecommerce_retail = ecommerce_retail[
    ~ecommerce_retail["InvoiceNo"].str.startswith("C")
]

# 2. Remove negative quantity transactions
ecommerce_retail = ecommerce_retail[
    ecommerce_retail["Quantity"] > 0
]

# 3. Remove negative unit prices
ecommerce_retail = ecommerce_retail[
    ecommerce_retail["UnitPrice"] > 0
]
```

### Business Logic

- Invoices starting with **"C"** represent cancellations (credit notes)
- Negative quantities indicate returns or incorrect entries
- Negative unit prices are financially invalid

Only valid sales transactions were retained.

---

## 🛠 Step 3. Handle Missing CustomerID

Customer-level analysis requires valid customer identifiers.

[In 7]:

```python
import missingno as msno
import numpy as np

# Visualize missing data
msno.matrix(ecommerce_retail)

# Standardize missing formats
ecommerce_retail["CustomerID"] = (
    ecommerce_retail["CustomerID"]
    .replace(["nan", "", " "], np.nan)
)

# Missing value summary
missing_summary = pd.DataFrame({
    "volume": ecommerce_retail.isnull().sum(),
    "%": (ecommerce_retail.isnull().sum() / ecommerce_retail.shape[0]) * 100
})

print(missing_summary)
```

### Investigation Findings

Missing `CustomerID` values were not concentrated in specific countries or time periods, suggesting general recording issues rather than systematic bias.

### Final Decision

Since `CustomerID` is critical for customer segmentation and RFM analysis:

[In 8]

```python
ecommerce_retail = ecommerce_retail.dropna(subset=["CustomerID"])
```

All transactions without valid customer identifiers were removed.

---

## 🛠 Step 4. Handle Duplicate Records

Duplicate rows were identified based on:

- `InvoiceNo`
- `StockCode`
- `InvoiceDate`
- `CustomerID`

[In 9]:

```python
# Identify duplicate rows based on 'InvoiceNo', 'StockCode', 'InvoiceDate', and 'CustomerID'



ecommerce_duplicate = ecommerce_retail[
    ecommerce_retail.duplicated(
        subset=["InvoiceNo", "StockCode", "InvoiceDate", "CustomerID"]
    )
]
```

If duplicates exist, they are handled in two cases:

### Case 1 — Identical Duplicates

- Same invoice, product, customer, date, and quantity  
- Likely caused by system duplication  
- ➝ Removed

### Case 2 — Same Transaction but Different Quantities

- Same invoice & product but recorded in separate rows  
- Likely order split issue  
- ➝ Quantities aggregated to maintain revenue accuracy  

---

## ✅ Dataset Status After EDA Preparation

After:

- Data type conversion  
- Removal of canceled and invalid transactions  
- Handling missing CustomerID  
- Resolving duplicates  

The dataset `ecommerce_retail` is now:

- Financially valid  
- Structurally consistent  
- Customer-ready  
- Suitable for revenue analysis and RFM modeling  
