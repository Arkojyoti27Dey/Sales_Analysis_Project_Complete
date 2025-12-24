

# 📊 XYZ Sales Intelligence: End-to-End Data Analysis

> **Unlocking Revenue Drivers & Optimizing Market Expansion for XYZ Company (2014-2018)**

This project performs a deep-dive Exploratory Data Analysis (EDA) on a complex, multi-source retail dataset. The goal is to transform raw relational data into actionable business insights regarding revenue, seasonal trends, and concentration risk.

---

## 🎯 Problem Statement

XYZ Company possesses extensive sales data spanning 2014-2018 but lacks a unified view of performance. This analysis aims to:

* **Identify Key Drivers:** Pinpoint high-performing products, channels, and regions.
* **Uncover Trends:** Detect seasonality and sales outliers.
* **Optimize Strategy:** Align performance against budgets to refine pricing and promotion strategies.

---

## 🏗️ Data Architecture & Wrangling

The raw data existed in a disjointed relational format (Excel sheets). A significant portion of this project involved **Data Engineering** to construct a unified "Master Analytical Table."

### 1. Data Sources

The dataset (`Regional Sales Dataset.xlsx`) was deconstructed into the following logical entities:

* **Sales Orders:** The core transactional table (`OrderNumber`, `OrderDate`, `Quantity`, `Unit Cost`).
* **Customers:** Client mapping (`Customer Names`).
* **Products:** Item details (`Product Name`).
* **Regions:** Granular location data (`City`, `County`, `Population`, `Median Income`).
* **State Regions:** High-level aggregation (`State`, `Region` e.g., 'Midwest').

### 2. The ETL Pipeline(extract transform load)

We implemented a robust join strategy to denormalize the database:

* **Merge 1:** `Sales Orders`  `Customers` (Left Join on Customer Index)
* **Merge 2:** `Sales Orders`  `Products` (Left Join on Product Description Index)
* **Merge 3:** `Sales Orders`  `Regions` (Left Join on Delivery Region Index)
* **Merge 4:** `Sales Orders`  `State Regions` (Left Join on State Code)

### 3. Data Cleaning Checklist

* [x] **Redundancy Removal:** Dropped surrogate keys (`Customer Index`, `Warehouse Code`, `id`) post-merge to reduce dimensionality.
* [x] **Sanity Checks:** Verified Null values across all columns (Dataset was remarkably clean with 0 nulls in key fields).
* [x] **Schema Validation:** Renamed confusing columns and corrected data types.
* [x] **Feature Selection:** Filtered for high-value features: `Order Quantity`, `Unit Price`, `Total Unit Cost`, `Region`, `Time Zone`.

---

## 📈 Key Analysis & Insights

### 1. Pricing Strategy Analysis

* **Unit Price Distribution:** Used Boxplots to visualize the spread of `Unit Price` across different `Product Names`.
* **Observation:** Identified products with high price variance vs. those with fixed pricing models, aiding in discount strategy formulation.

### 2. Regional Performance

* **Location Intelligence:** Enriched sales data with census metrics (`Population`, `Median Income`).
* **Time Zone Analysis:** Segmented sales by `Time Zone` (America/New York vs. America/Los Angeles) to optimize support hours and marketing timing.

### 3. Profitability calculation

* Derived potential profit margins by analyzing the delta between `Unit Price` and `Total Unit Cost`.

---

## 🛠️ Tech Stack

* **Core:** `Python 3.x`
* **Data Manipulation:** `Pandas` (Merging, Cleaning, Aggregation)
* **Visualization:** `Matplotlib`, `Seaborn` (Boxplots, Distribution curves)

---

