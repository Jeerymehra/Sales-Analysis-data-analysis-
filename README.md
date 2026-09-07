# 📊 Sales Data Analysis & Business Insights

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-yellow.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Data%20Visualization-orange.svg)

## 📖 Project Overview
This project is an end-to-end Exploratory Data Analysis (EDA) of a retail company's yearly sales data. The script automates the process of merging 12 months of raw CSV data, cleaning the dataset, engineering new features, and generating visual reports. The goal of this analysis is to extract actionable business insights regarding seasonal trends, regional performance, and product bundling opportunities.

---

## 📑 Table of Contents
1. [Key Business Questions](#-key-business-questions)
2. [Dataset Description](#-dataset-description)
3. [Technologies Used](#%EF%B8%8F-technologies-used)
4. [Methodology & Workflow](#-methodology--workflow)
5. [Installation & Setup](#-installation--setup)
6. [Key Insights & Visualizations](#-key-insights--visualizations)
7. [Future Enhancements](#-future-enhancements)

---

## 🎯 Key Business Questions
This script calculates and visualizes the answers to the following strategic questions:
1. **Revenue Seasonality:** What was the best month for sales, and what was the total revenue? 
2. **Geographic Performance:** Which city (and state) generated the highest volume of sales?
3. **Market Basket Analysis:** What pairs of products are most frequently purchased together?
4. **Price Elasticity & Demand:** What is the most sold product, and how does its unit price correlate with the total quantity ordered?

---

## 📁 Dataset Description
The analysis relies on 12 separate CSV files (one for each month of the year). 

**Raw Data Columns:**
* `Order ID`: Unique identifier for each transaction.
* `Product`: The name of the item sold.
* `Quantity Ordered`: The number of items purchased in a single transaction.
* `Price Each`: The cost of a single unit of the product.
* `Order Date`: The timestamp of the purchase.
* `Purchase Address`: The physical address where the order was shipped.

---

## 🛠️ Technologies Used
* **Language:** Python 3.x
* **Data Manipulation:** `pandas`
* **Data Visualization:** `matplotlib.pyplot`
* **Built-in Libraries:** `os`, `collections.Counter`, `itertools.combinations`

---

## 🔬 Methodology & Workflow

### 1. Data Ingestion & Merging
* Scans the local `./Sales_Data` directory.
* Iterates through all monthly CSV files and concatenates them into a single master DataFrame (`all_data.csv`).

### 2. Data Cleaning
* **Missing Values:** Identifies and drops completely blank rows (`NaN`).
* **Header Duplication:** Removes rows where the header was accidentally duplicated inside the data (e.g., dropping rows where `Order Date` equals `'Or'`).
* **Type Conversion:** Casts `Quantity Ordered` to integers and `Price Each` to floats for mathematical operations. Converts `Order Date` to standard datetime format.

### 3. Feature Engineering
* **Month Column:** Extracted from the `Order Date` for time-series grouping.
* **Sales Column:** Calculated dynamically (`Quantity Ordered` * `Price Each`).
* **City Column:** Parsed from the `Purchase Address` string, formatted as `City (State)` to resolve duplicate city names across different states.

### 4. Advanced Aggregation
* Utilizes `pandas.groupby()` functions for categorical summation.
* Implements a Market Basket Analysis using `itertools.combinations` to find items bought together based on duplicate `Order ID`s.

---

## 💻 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/sales-data-analysis.git](https://github.com/yourusername/sales-data-analysis.git)
   cd sales-data-analysis