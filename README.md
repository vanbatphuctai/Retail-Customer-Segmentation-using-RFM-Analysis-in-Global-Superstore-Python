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
### 🌍 Global SuperStore - Business Context

**SuperStore** is a multinational retail company operating across multiple global markets with a **large and diverse customer base**.

As transaction volume continues to scale, traditional **manual segmentation methods** (previously handled in Excel) are no longer feasible. Meanwhile, customers increasingly expect **personalized engagement** instead of mass marketing campaigns.

During the **Christmas and New Year season**, the Marketing Department aimed to:

- **Reward loyal customers**
- **Re-engage inactive customers**
- **Identify potential high-value customers**
- **Optimize campaign targeting efficiency**

However, due to the size of the dataset, segmentation needed to be **automated and scalable**.

The Data Analytics team was tasked with building a **Python-based RFM segmentation pipeline** to support a **data-driven marketing strategy**.

---

### 🎯 Project Objective

The goal of this project was to design and implement a **scalable RFM (Recency – Frequency – Monetary) segmentation framework** that:

- **Identifies high-value and loyal customers**
- **Detects early churn-risk segments**
- **Supports targeted campaign execution**
- **Establishes the foundation for Customer Lifetime Value (CLV) strategy**

---

### 📌 RFM Framework Definition

The **RFM model** evaluates customer behavior using transactional data:

- **Recency (R):** How recently a customer made a purchase  
- **Frequency (F):** How often a customer makes purchases  
- **Monetary (M):** How much revenue the customer generates  

Rather than treating RFM as a simple scoring table, this project positions it as a **behavior-based analytical foundation** for **long-term customer strategy**.

---

### ❗ Why RFM Over Traditional Segmentation

Traditional segmentation methods such as demographic grouping or total revenue ranking are often **static and assumption-driven**.

RFM provides stronger business value because it:

- Uses **actual transactional behavior**
- Enables **scalable segmentation for large datasets**
- Provides **clear retention and prioritization logic**
- Supports advanced modeling such as:
  - **Customer Lifetime Value (CLV)**
  - **Churn prediction**
  - **Survival analysis**

It bridges the gap between **descriptive reporting** and **predictive customer analytics**.

---

### 🛠 Technical Implementation

The segmentation workflow was implemented in **Python**, including:

- **Data cleaning and preprocessing**
- **Aggregation of transaction-level data into customer-level metrics**
- **Calculation of R, F, and M values**
- **Scoring and quantile-based segmentation**
- **Segment labeling and business interpretation**

The final output was a **structured customer segmentation dataset** ready for:

- **CRM integration**
- **Marketing automation**
- **Dashboard visualization**
- **Campaign targeting**

---

### 👥 Stakeholders

- **Senior Management**
- **Marketing & CRM Team**
- **Strategy & Growth Team**
- **Business & Data Analysts**

---

### ❓ Key Business Questions Answered

- Which customer segments generate the **highest revenue**?
- Which customers show **declining engagement patterns**?
- How should **marketing budget** be prioritized across segments?
- How can transactional data support **long-term CLV optimization**?

---

### 📊 Project Outcomes

The RFM framework successfully:

- **Identified high-value loyal customers**
- **Detected at-risk and inactive customers**
- **Improved targeting precision for seasonal campaigns**
- **Enabled scalable, automated segmentation using Python**
- **Established analytical groundwork for advanced customer modeling**

This project demonstrates the practical application of **behavioral analytics** to support **personalized marketing at scale** in a global retail environment.

---

## 📂 Dataset Description & Data Structure

### 📌 Data Source

- **Source:** E-commerce Retail Dataset  
- **Size:** 541,910 rows × 8 columns  
- **Format:** `.xlsx` (2 sheets)  

---

### 📂 Data Structure & Relationships

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

## 🧹 Data Cleaning & Preprocessing

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

### Summary

⚡ Initial exploration revealed several data quality issues, including **negative values in Quantity and UnitPrice, missing CustomerID (~135K records), duplicate transactions, and inconsistencies between StockCode and Description**.  
These issues require validation and cleaning before reliable analysis.

#### ⚡ Data Quality Insights
A mismatch was observed between **StockCode (4070)** and **Description (4223)** counts, indicating potential inconsistencies such as:

- Multiple descriptions for the same product  
- Missing or duplicated product identifiers  
- Manually entered or inconsistent product names  

Further validation is required to ensure data consistency.

#### ⚠ Manual Review Required
Some orders contain **incorrect or inconsistent descriptions** → These records should be manually reviewed and flagged as errors.

#### 🔎 Data Validation & Error Identification
- Checked **description mismatches** between StockCode and Description  
- Verified **negative Quantity values** against cancellations (`InvoiceNo` starting with **"C"**)  
→ Flagged suspicious transactions for further validation.

### ✨ Conclusion

**Data Types:** Convert the following columns to string:

- InvoiceNo  
- StockCode  
- Description  
- CustomerID  
- Country  

**Data Values:**

- **Quantity < 0 & InvoiceNo starts with "C"** → Canceled orders → remove  
- **Quantity < 0 but InvoiceNo does not start with "C"** → Invalid records → remove  
- **UnitPrice < 0 or incorrect descriptions** → Invalid transactions → remove

---

## 🔍 Exploratory Data Analysis (EDA)

After completing the initial data inspection, the dataset `ecommerce_retail` was cleaned and prepared for analytical tasks.

#### 🛠 Step 1: Convert to Correct Data Types

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


#### 🛠 Step 2: Remove Invalid Transactions

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


#### 🛠 Step 3: Handle Missing CustomerID

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

[Out 7]:

<img width="900" alt="image" src="https://github.com/user-attachments/assets/91806737-394f-46b2-bb3b-b024ac57aad7" />


#### Investigation Findings

Missing `CustomerID` values were not concentrated in specific countries or time periods, suggesting general recording issues rather than systematic bias.

#### Final Decision

Since `CustomerID` is critical for customer segmentation and RFM analysis:

[In 8]

```python
# Remove transactions with missing CustomerID to ensure valid customer-level analysis
ecommerce_retail = ecommerce_retail.dropna(subset=["CustomerID"])
```

All transactions without valid customer identifiers were removed.


#### 🛠 Step 4: Handle Duplicate Records

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

#### Case 1:  Identical Duplicates

- Same invoice, product, customer, date, and quantity  
- Likely caused by system duplication  
➝ Removed

#### Case 2:  Same Transaction but Different Quantities

- Same invoice & product but recorded in separate rows  
- Likely order split issue  
➝ Quantities aggregated to maintain revenue accuracy  

---
## 🧮 Apply RFM Model

#### 🛠 Step 1: RFM Feature Engineering

[In 10]:

```python
# Set the reference date for calculating Recency as December 31, 2011
last_date = pd.to_datetime('12/31/2011')


# Calculate the Revenue column
ecommerce_retail['Revenue'] = ecommerce_retail['Quantity'] * ecommerce_retail['UnitPrice']


# Create RFM df
rfm = ecommerce_retail.groupby('CustomerID').agg(
    Recency=("InvoiceDate", lambda x: (last_date - x.max()).days), # Calculate the number of days since the last purchase
    Frequency=("InvoiceNo", "nunique"), # Count the number of transactions per customer
    Monetary=("Revenue", "sum") # Sum the total revenue per customer
).reset_index()


#Check
rfm.head()
```

[Out 10]:

<img width="900" alt="image" src="https://github.com/user-attachments/assets/f9f50de5-d2fa-4f7d-b588-21d9171286a4" />


#### 🛠 Step 2: Check outlier

[In 11]:

```python
# Create 1 row, 3 columns
fig, axes = plt.subplots(1, 3, figsize=(15, 5))


# Check outliers for the 'Recency' column
sns.boxplot(data=rfm, x='Recency', ax=axes[0])
axes[0].set_title('Recency Outliers')


# Check outliers for the 'Frequency' column
sns.boxplot(data=rfm, x='Frequency', ax=axes[1])
axes[1].set_title('Frequency Outliers')


# Check outliers for the 'Monetary' column
sns.boxplot(data=rfm, x='Monetary', ax=axes[2])
axes[2].set_title('Monetary Outliers')


plt.tight_layout()
plt.show()
```

[Out 11]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/12d996e0-1f1a-4a2d-bb33-43f94a45ded8" />

📌 **Solution**

The boxplots show the presence of **extreme values** and **right-skewed distributions**, especially in **Frequency** and **Monetary**.

To ensure more **reliable analysis**, a **95th percentile threshold** will be applied to **remove extreme outliers**.  
This allows the analysis to focus on the **majority of customers** and prevents **distortion caused by unusually large values**.

#### 🛠 Step 2.1: Outlier Treatment using 95th Percentile

[In 12]:

```python
# Apply 95th percentile cap
rfm['Frequency'] = rfm['Frequency'].clip(upper=rfm['Frequency'].quantile(0.95))
rfm['Monetary'] = rfm['Monetary'].clip(upper=rfm['Monetary'].quantile(0.95))
```

#### 🛠 Step 3: Assign RFM scores using Qcut

[In 13]:

```python
# Recency score: Lower values indicate more recent purchases, so assign higher scores to lower recency values
rfm['R_Score'] = pd.qcut(rfm['Recency'], 5, labels = [5,4,3,2,1])


# Frequency score: Higher values indicate more frequent purchases, so assign higher scores to higher frequency values
rfm['F_Score'] = pd.qcut(rfm['Frequency'].rank(method='first'), 5, labels = [1,2,3,4,5])


# Monetary score: Higher values indicate higher spending, so assign higher scores to higher monetary values
rfm['M_Score'] = pd.qcut(rfm['Monetary'], 5, labels = [1,2,3,4,5])


# Combine RFM scores into a single string to create the RFM segment
rfm['RFM_Score'] = rfm['R_Score'].astype(str) + rfm['F_Score'].astype(str) + rfm['M_Score'].astype(str)
rfm.head()
```

[Out 13]:

<img width="1050" alt="image"  src="https://github.com/user-attachments/assets/276f4aed-f305-4a3e-9d3c-9d0d4ad429c5" />


#### 🛠 Step 4: Calculate RFM Score

[In 14]:

```python
#Split the RFM Score column into a list
segmentation['RFM Score'] = segmentation['RFM Score'].astype(str).str.split(',')

#Explode (each score into a separate row)
segmentation = segmentation.explode('RFM Score')

#Remove whitespace from RFM_Score values
segmentation['RFM Score'] = segmentation['RFM Score'].str.strip()

#Merge segmentation into rfm
rfm = rfm.merge(segmentation, left_on="RFM_Score", right_on="RFM Score", how="left")


# After merging, remove the RFM column to prevent confusion
rfm = rfm.drop(columns=['RFM Score'])


#Generates the combined RFM_Score by concatenating the individual Recency, Frequency, and Monetary scores into a single string.
rfm['RFM_Score'] = rfm['R_Score'].astype(str) + rfm['F_Score'].astype(str) + rfm['M_Score'].astype(str)
rfm


```
[Out 14]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/4c8db269-ce57-4370-96a2-7d56e206799c" />

---

## 📊 Visualization & Analysis

#### Visualization Configuration

[In 15]:

```python
# Set Visualization Style
sns.set(style="whitegrid")
plt.rcParams["figure.figsize"] = (10, 6)


# Define Custom Color Palette
# Set palette
Brand_color = "#4A90E2"


def brand_palette(n, reverse=False):
    return sns.light_palette(Brand_color, n_colors=n, reverse=reverse)

```

### Group A. Customer Segmentation Overview

Understanding the distribution and behavioral characteristics of each RFM customer segment.

#### 1. Customer Count by Segment

Visualize the number of customers in each RFM segment

[In 16]:

```python
# Customer Count by Segment


order = rfm['Segment'].value_counts().index
palette = brand_palette(len(order), reverse=True)


ax = sns.countplot(
    data=rfm,
    x='Segment',
    order=order,
    palette=palette
)


# Add value labels
for p in ax.patches:
    ax.annotate(
        f'{int(p.get_height())}',
        (p.get_x() + p.get_width()/2., p.get_height()),
        ha='center',
        va='bottom',
        fontsize=9
    )


plt.title("Customer Count by Segment", fontsize=14, weight='bold')
plt.xlabel("Segment")
plt.ylabel("Customer Count")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
[Out 16]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/11411cd8-ce3a-4f3f-816b-2fb8ba1dc852" />

#### 📌 Insight

- **Champions account for 835 customers (~20% of the total base)**, making it the largest segment and a strong foundation for retention-driven growth.

- **Hibernating customers represent 696 customers (~16%)**, while  
  **Lost customers account for about 480 (~11–12%)**.

- Inactive segments (**Hibernating + Lost**) together make up roughly **27% of the customer base**, indicating meaningful churn risk and a clear opportunity for reactivation strategies.

#### 2. Revenue Contribution by Segment


Calculate total revenue generated by each customer segment


[In 17]:

```python
# Revenue Contribution by Segment


plt.figure(figsize=(12,6))


segment_rev = (
    rfm.groupby('Segment')['Monetary']
    .sum()
    .sort_values(ascending=False)
    .reset_index()
)


palette = brand_palette(len(segment_rev), reverse=True)


ax = sns.barplot(
    data=segment_rev,
    x='Segment',
    y='Monetary',
    palette=palette
)


for p in ax.patches:
    ax.annotate(
        f'{p.get_height():,.0f}',
        (p.get_x() + p.get_width()/2., p.get_height()),
        ha='center',
        va='bottom',
        fontsize=9
    )


plt.title("Total Revenue by Segment", fontsize=14, weight='bold')
plt.xlabel("Segment")
plt.ylabel("Total Revenue")
plt.xticks(rotation=45)
plt.tight_layout()
ax.ticklabel_format(style='plain', axis='y')
plt.show()
```
[Out 17]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/977d0c2a-f828-4b6d-9d86-9e40a0c75acf" />

#### 📌 Insight  

- **Champions generate 2.86M in revenue**, contributing the largest share and serving as the primary revenue engine of the business.  

- **Loyal and At Risk segments together contribute over 1.5M**, forming a strong but retention-sensitive revenue base.  

- Revenue is heavily concentrated in top-tier customers, indicating high dependency on core high-value segments.


#### 3. Revenue Share by Segment (%)

Show the percentage contribution of each segment to total revenue

[In 18]:

```python
# Revenue Share by Segment (%)


plt.figure(figsize=(12,6))


segment_rev['Revenue_%'] = (
    segment_rev['Monetary'] /
    segment_rev['Monetary'].sum()
) * 100


palette = brand_palette(len(segment_rev), reverse=True)


ax = sns.barplot(
    data=segment_rev,
    x='Segment',
    y='Revenue_%',
    palette=palette
)


for p in ax.patches:
    ax.annotate(
        f'{p.get_height():.1f}%',
        (p.get_x() + p.get_width()/2., p.get_height()),
        ha='center',
        va='bottom',
        fontsize=9
    )


plt.title("Revenue Share by Segment (%)", fontsize=14, weight='bold')
plt.xlabel("Segment")
plt.ylabel("Revenue Percentage")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

[Out 18]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/558abe0e-b93d-48f7-9b37-d3df8af8b865" />

#### 📌 Insight  

- **Champions contribute 50.3% of total revenue**, indicating a strong dependence on top-tier customers as the primary revenue driver.  

- **Loyal (15.3%) and At Risk (11.6%)** together account for nearly **27%**, representing a substantial but retention-sensitive revenue base.  

- All remaining segments individually contribute below 6%, highlighting a highly concentrated revenue structure.

#### 4. Average RFM Heatmap by Segment
Compare average Recency, Frequency, and Monetary values across segments

[In 19]:

```python
# Average RFM Metrics by Segment


plt.figure(figsize=(10,6))


segment_avg = (
    rfm.groupby('Segment')[['Recency','Frequency','Monetary']]
    .mean()
)


# Rename columns to RFM
segment_avg.columns = ['R', 'F', 'M']


sns.heatmap(
    segment_avg,
    annot=True,
    fmt=".1f",
    cmap=sns.light_palette(Brand_color, as_cmap=True)
)


plt.title("Average RFM Metrics by Segment", fontsize=14, weight='bold')
plt.tight_layout()
plt.show()
```

[Out 19]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/207ec3f6-a6a5-4204-95f4-94c3f027e867" />

#### 📌 Insight  

- **Champions show the strongest engagement**, with the lowest Recency (31.8), highest Frequency (8.8), and highest Monetary value (3430.1), confirming them as the most valuable and active segment.  

- **At Risk customers still generate high Monetary value (1559.8)** despite high Recency (164.4), indicating significant revenue at potential churn risk.  

- **Lost customers exhibit the weakest performance** (Recency 296.6, Frequency 1.1, Monetary 200.4), reflecting minimal engagement and low recovery value.

---

### Group B. Customer Value Analysis

Evaluating customer spending behavior and lifetime value across segments.

#### 5. Average Revenue per Customer by Segment

Measure the average spending value of customers in each segment

[In 20]:

```python
# Average Revenue per Customer


plt.figure(figsize=(12,6))


rev_per_customer = (
    rfm.groupby('Segment')['Monetary']
    .mean()
    .sort_values(ascending=False)
    .reset_index()
)


palette = brand_palette(len(rev_per_customer), reverse=True)


ax = sns.barplot(
    data=rev_per_customer,
    x='Segment',
    y='Monetary',
    palette=palette
)


for p in ax.patches:
    ax.annotate(
        f'{p.get_height():,.0f}',
        (p.get_x() + p.get_width()/2., p.get_height()),
        ha='center',
        va='bottom',
        fontsize=9
    )


plt.title("Average Revenue per Customer", fontsize=14, weight='bold')
plt.xlabel("Segment")
plt.ylabel("Revenue per Customer")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

[Out 20]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/fdbc6348-969c-42e7-be73-d5875d53eb75" />

#### 📌 Insight  

- **Champions generate the highest revenue per customer (3,430)**, significantly outperforming Loyal (2,035) and At Risk (1,560), confirming their premium value.  

- High-value but vulnerable segments such as **Cannot Lose Them (1,432)** and **At Risk (1,560)** represent substantial revenue at potential churn risk.  

- Lower-tier segments like **Lost (200) and New Customers (224)** contribute minimal value per customer, highlighting the need for upselling rather than reactivation focus.


#### 6. CLV Proxy Calculation & Distribution

Purpose: Estimate long-term customer value using RFM

CLV Proxy = Frequency*Monetary

[In 21]:

```python
# Create CLV proxy metric
rfm['CLV_Proxy'] = rfm['Frequency'] * rfm['Monetary']
```

#### 6.1 Customer Lifetime Value (CLV) Distribution
Analyze the distribution of estimated customer lifetime value

[In 22]:

```python
# CLV Distribution


plt.figure(figsize=(10,6))


sns.histplot(rfm['CLV_Proxy'], bins=50, color=Brand_color)


plt.title("Customer Lifetime Value (CLV) Distribution", fontsize=14, weight='bold')
plt.xlabel("CLV Proxy")
plt.ylabel("Customer Count")
plt.tight_layout()
plt.show()
```

[Out 22]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/1dc1f0cd-6df2-4a5e-ad64-df2201e2c887" />

#### 📌 Insight

- The **CLV distribution is highly right-skewed**, with most customers at **low CLV** and a small group generating **exceptionally high value**.

- A limited number of **high-CLV customers** contribute disproportionately to total revenue, confirming strong **value concentration**.

- This pattern underscores the need to **prioritize retention of top-value customers** while applying targeted **upsell strategies** to mid-tier segments.

#### 6.2 CLV Comparison Across Segments

Compare CLV distribution across different customer segments

[In 23]:

```python
# CLV by Segment (Boxplot Comparison)


plt.figure(figsize=(12,6))


sns.boxplot(
    x='Segment',
    y='CLV_Proxy',
    data=rfm,
    color=Brand_color
)


plt.xticks(rotation=45)
plt.title("CLV Comparison Across Segments", fontsize=14, weight='bold')
plt.tight_layout()
plt.show()
```

[Out 23]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/195e8320-34ae-471a-ad29-a411bfbd3592" />


#### 📌 Insight

- **Champions** exhibit the highest median **CLV** with a wide value spread, confirming their role as the primary long-term revenue drivers.

- **Loyal** and **At Risk** segments also show elevated CLV levels, indicating strong monetization potential but varying retention stability.

- In contrast, segments such as **New Customers**, **Hibernating**, and **About To Sleep** display consistently low CLV, reflecting limited current value.

- Overall, **customer lifetime value is highly concentrated** in a few key segments, reinforcing the need for differentiated retention and upsell strategies.

#### 7. Top 10% High CLV Customers

Identify the top 10% customers with the highest lifetime value

[In 24]:

```python

# Top 10% High CLV Customers Highlight


# Define top 10% threshold
threshold = rfm['CLV_Proxy'].quantile(0.90)
top_customers = rfm[rfm['CLV_Proxy'] >= threshold]


plt.figure(figsize=(12,7))


# Background customers (smaller + lighter)
plt.scatter(
    rfm['Recency'],
    rfm['Frequency'],
    s=20,
    alpha=0.1,
    color='grey'
)


# Scale bubble size properly for top customers
scaled_size = (top_customers['CLV_Proxy'] /
               top_customers['CLV_Proxy'].max()) * 1500


# Highlight Top 10%
plt.scatter(
    top_customers['Recency'],
    top_customers['Frequency'],
    s=scaled_size,
    alpha=0.8,
    color=Brand_color,
    edgecolor='white',
    linewidth=1
)


# Add median reference lines
plt.axvline(rfm['Recency'].median(), linestyle='--', alpha=0.4)
plt.axhline(rfm['Frequency'].median(), linestyle='--', alpha=0.4)


plt.xlabel("Recency")
plt.ylabel("Frequency")
plt.title("Top 10% High CLV Customers", fontsize=16, weight='bold')


plt.grid(alpha=0.2)
plt.tight_layout()
plt.show()
```

[Out 24]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/e56511ac-3489-435a-a16b-8cc7fc017d6b" />

#### 📌 Insight

- The **top 10% high-CLV customers** are primarily concentrated in the **low Recency – high Frequency** zone, indicating strong engagement and repeat purchasing behavior.

- These customers represent the core **revenue-driving segment** and should be prioritized for retention and loyalty programs.

- Protecting this small but valuable group is critical to sustaining long-term revenue performance.

---

### Part C. Risk & Retention Analysis

Analyzing churn risk to identify customers who may require retention strategies.

#### 8. Churn Risk Scoring

Purpose: Identify customers with high probability of churn

Simple approach: Higher Recency → Higher churn risk

[In 25]:

```python
# Normalize Recency (scale between 0 and 1)
rfm['R_scaled'] = rfm['Recency'] / rfm['Recency'].max()


# Define churn score (higher Recency = higher risk)
rfm['Churn_Score'] = rfm['R_scaled']
```

#### 8.1 Customer Churn Risk Distribution

Visualize the distribution of churn risk among customers

[In 26]:

```python
# Churn Risk Distribution


plt.figure(figsize=(10,6))


sns.histplot(rfm['Churn_Score'], bins=40, color=Brand_color)


plt.title("Churn Risk Distribution", fontsize=14, weight='bold')
plt.xlabel("Churn Score")
plt.ylabel("Customer Count")
plt.tight_layout()
plt.show()
```

[Out 26]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/38d1fc3e-3139-4495-ad9c-c3cbf0d64873" />

#### 📌 Insight

- The churn risk distribution is right-skewed, with the majority of customers concentrated at **low churn scores (below 0.3)**, indicating a relatively stable customer base.

- However, a noticeable tail of customers exhibits **high churn risk (above 0.7)**, representing a vulnerable segment that may require immediate retention actions.

- Although smaller in size, this high-risk group could pose significant revenue impact if it overlaps with high-value segments.
  
- Overall, churn risk is not evenly distributed, highlighting the importance of targeted, segment-based retention strategies.

#### 8.2 Churn Risk by Customer Segment**


Evaluate which segments have the highest risk of churn

[In 27]:

```python
# Churn Risk by Segment


plt.figure(figsize=(12,6))


sns.boxplot(
    x='Segment',
    y='Churn_Score',
    data=rfm,
    color=Brand_color
)


plt.xticks(rotation=45)
plt.title("Churn Risk by Segment", fontsize=14, weight='bold')
plt.tight_layout()
plt.show()
```

[Out 27]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/363c2d21-83fb-4472-8bcf-db40ba3c59b9" />

#### 📌 Insight

- **Lost Customers** and **Cannot Lose Them** segments show the highest median churn scores (around 0.6–0.8), indicating severe disengagement and immediate revenue risk.

- **At Risk** customers also display elevated churn levels with wide variability, suggesting urgent retention opportunities with potentially high ROI.

- In contrast, **Champions** and **Loyal** segments maintain consistently low churn scores, confirming strong engagement and customer stability.
  
- Churn risk is clearly segment-driven rather than evenly distributed, reinforcing the value of RFM-based targeted retention strategies.

---

### Part D. Strategic Marketing Insights

Supporting marketing decision-making through strategic customer analysis.

#### 9. Pareto Analysis of Revenue Contribution (80/20 Rule)

Identify the proportion of customers contributing to total revenue

[In 28]:

```python
# Pareto Analysis


plt.figure(figsize=(12,6))


rfm_sorted = rfm.sort_values(by='Monetary', ascending=False)
rfm_sorted['Cum_Percent'] = (
    rfm_sorted['Monetary'].cumsum() /
    rfm_sorted['Monetary'].sum()
)


plt.plot(rfm_sorted['Cum_Percent'].values, color=Brand_color)
plt.axhline(y=0.8, linestyle='--')


plt.title("Pareto Analysis of Revenue Contribution - Cumulative Revenue", fontsize=14, weight='bold')
plt.xlabel("Customers Ranked by Revenue")
plt.ylabel("Cumulative Revenue Share")
plt.tight_layout()
plt.show()
```

[Out 28]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/37b991e5-c922-47c2-8329-0cc78dc4656a" />

#### 📌 Insight  

- Approximately **20–25% of customers generate nearly 80% of total revenue**, confirming a strong Pareto (80/20) effect.  

- Revenue is highly concentrated among top-spending customers, indicating significant dependence on a relatively small customer base.  

- Protecting and retaining high-value customers is critical, as losing a small portion of them could materially impact total revenue.


#### 10. RFM Customer Behavior Distribution

Visualize customer behavior based on Recency, Frequency, and Monetary values

[In 29]:

```python
# RFM Distribution Bubble Chart


plt.figure(figsize=(12,6))


plt.scatter(
    rfm['Recency'],
    rfm['Frequency'],
    s=rfm['Monetary']/10,
    alpha=0.4,
    color=Brand_color
)


plt.title("RFM Customer Behavior Distribution", fontsize=14, weight='bold')
plt.xlabel("Recency")
plt.ylabel("Frequency")
plt.tight_layout()
plt.show()
```

[Out 29]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/78a0d855-8f9f-4692-81ac-acb6250e61d1" />

#### 📌 Insight  


- High-value customers (larger bubbles) are concentrated in the **low Recency – high Frequency** zone, indicating that recent and frequent buyers drive the majority of revenue.  

- A large portion of customers cluster in the **high Recency – low Frequency** area, suggesting a substantial inactive or low-engagement base.  

- Revenue distribution is uneven, with a small group of active customers generating disproportionately higher monetary value.


#### 11. Segment Priority Matrix

This chart compares customer share vs revenue share of each segment. Bubble size represents total revenue.

Helps identify high-value segments that generate disproportionate revenue

[In 30]:

```python
from adjustText import adjust_text


sns.set(style="whitegrid")


# Segment Summary
segment_summary = (
    rfm.groupby('Segment')
    .agg(Customer_Count=('CustomerID','count'),
         Revenue=('Monetary','sum'))
    .reset_index()
)


segment_summary['Customer_Share'] = segment_summary['Customer_Count'] / segment_summary['Customer_Count'].sum()
segment_summary['Revenue_Share'] = segment_summary['Revenue'] / segment_summary['Revenue'].sum()


bubble_size = segment_summary['Revenue'] / segment_summary['Revenue'].max() * 2000




# Segment Priority Matrix
plt.figure(figsize=(12,8))


x = segment_summary['Customer_Share'] * 100
y = segment_summary['Revenue_Share'] * 100


plt.scatter(x, y, s=bubble_size, alpha=0.7, color="#2E86C1")




# Labels
texts = [
    plt.text(x[i], y[i], segment_summary['Segment'][i], fontsize=10)
    for i in range(len(segment_summary))
]


adjust_text(texts)




# Quadrant reference lines
plt.axhline(y.mean(), linestyle='--', alpha=0.6)
plt.axvline(x.mean(), linestyle='--', alpha=0.6)




# Axis & Title
plt.xlabel("Customer Share (%)")
plt.ylabel("Revenue Share (%)")
plt.title("Segment Priority Matrix", fontsize=16, weight='bold')


plt.xlim(0,22)
plt.ylim(0,55)


plt.tight_layout()
plt.show()
```

[Out 30]:

<img width="1050" alt="image" src="https://github.com/user-attachments/assets/6ae7c3a2-9ce2-4112-bb34-553edf5e6fe9" />

#### 📌 Insight

- **Champions (~20% of customers)** generate approximately **50% of total revenue**, confirming strong revenue concentration and the need for priority retention strategies.

- **Loyal and At Risk segments (~10% each)** together contribute around **25–30% of revenue**, indicating significant churn sensitivity and high retention ROI.

- In contrast, **Hibernating customers (~16% of customers)** contribute only **~4–5% of revenue**, highlighting substantial reactivation potential.

- Overall, nearly **75–80% of revenue** is driven by a small group of high-value segments, reinforcing the importance of targeted, data-driven marketing actions.

---

## 💡 Insight & Recommendation
### Executive Insight & Strategic Direction

#### Overall Business Insight

SuperStore’s revenue structure is **highly concentrated and engagement-driven**.  

Approximately **20–25% of customers generate 75–80% of total revenue**, with **Champions (~20% of the base) contributing ~50% alone**. These high-value customers are characterized by **low Recency and high Frequency**, confirming that recent and repeat purchasing behavior is the primary driver of lifetime value.

Meanwhile, inactive segments such as **Hibernating and Lost (~27% of customers)** contribute minimal revenue but represent meaningful reactivation potential. In addition, **At Risk and Cannot Lose Them segments combine high monetary value with elevated churn scores**, exposing substantial revenue to potential loss.

This indicates that holiday marketing should not be mass-oriented, but **precision-driven and segment-specific**.

---

### Strategic Priorities for Holiday Campaign

#### 1️⃣ Revenue Protection (Top Priority)

**Target:** Champions & Loyal  

- Represent ~50–65% of total revenue.
  
- Low churn risk but extremely high financial impact if lost.

**Strategy:**
- VIP holiday rewards & exclusive access
  
- Loyalty tier upgrades
  
- Personalized appreciation campaigns

Goal → Protect the revenue core during peak season.

---

#### 2️⃣ Revenue Growth Acceleration

**Target:** Loyal, Potential Loyalists, At Risk  

- Contribute ~25–30% of revenue.
  
- Strong spending capacity but retention-sensitive.

**Strategy:**
- Holiday bundles & cross-sell promotions
  
- Time-limited festive incentives
  
- Early re-engagement triggers for rising Recency

Goal → Convert mid-tier customers into future Champions.

---

#### 3️⃣ Churn Mitigation & Revenue Recovery

**Target:** At Risk, Cannot Lose Them, Hibernating  

- High churn scores with meaningful revenue exposure.
  
- Represent both revenue risk and recovery opportunity.

**Strategy:**
- Win-back holiday vouchers
  
- Personalized reminder campaigns
  
- Behavioral-triggered discount offers

Goal → Reduce revenue leakage and reactivate dormant value pools.

---

## Strategic Conclusion

SuperStore should shift from broad holiday promotions to a **data-driven, RFM-based marketing execution model**.

By simultaneously protecting high-value customers, accelerating mid-tier growth, and mitigating churn risk, the company can maximize short-term holiday ROI while strengthening long-term customer lifetime value.




