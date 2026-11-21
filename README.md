# 📊E-Commerce Data Transformation & Modeling | Power BI

To improve the quality and consistency of e-commerce sales data through data cleaning, transformation, aggregation, and relationship modeling using Power BI.

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Data Sources & Architecture](#-data-sources--architecture)
- [Data Transformation ETL](#-data-transformation-etl)
- [Data Model DAX](#-data-model-dax)
- [Dashboard Features](#-dashboard-features)
- [Key Insights](#-key-insights)
- [How To Use](#-how-to-use)

---

## 🎯 Project Overview

\- **Business Problem:** E-commerce data is maintained across multiple tables with different levels of information, making it difficult to perform consistent sales and profitability analysis without proper data preparation and modeling.

\- **Objective:** To clean and standardize the sales datasets, create meaningful calculated columns and summary tables, and establish relationships between tables to prepare a reliable data model for future business reporting.

\- **Target Audience:** Aspiring Data Analysts, Sales Analysts, Business Intelligence Professionals, and Sales Operations Teams.

## 🗃️ Data Sources & Architecture

- **Source Systems:** Three CSV files imported into Power BI.
- **Datasets Used:**
  1. **List of Orders:** Contains customer details, order dates, city, and state.
  2. **Order Details:** Contains order-level transaction details such as amount, profit, quantity, category, and sub-category.
  3. **Sales Target:** Contains monthly sales targets for different product categories.
- **Data Volume:** List of Orders was restricted to the first 500 rows. Sales Target contains 36 records.
- **Storage Mode:** Import Mode.
- **Data Preparation Environment:** Power BI Desktop and Power Query Editor.

## ⚙️ Data Transformation ETL

**Tool Used:** Power Query Editor.

The following transformations were performed to improve data quality and prepare the datasets for modeling.

**1. Data Cleaning & Formatting**
- Imported all three CSV datasets.
- Restricted List of Orders to the first 500 rows.
- Assigned appropriate data types to columns.
- Converted CustomerName into Proper Case.
- Checked missing values, errors, and duplicate records.

**2. Custom Column Creation**
- Created a Location column by combining City and State.
- Created a Profit Margin column using Profit and Amount.
- Created a conditional Profit Status column to classify records as Profit, Loss, or No Profit.

**3. Data Merging**
- Merged List of Orders with Order Details using Order ID.
- Used Left Outer Join to retain all records from List of Orders.
- Expanded the required transaction columns.
- Renamed the merged query as Orders Data.

**4. Sorting & Filtering**
- Sorted Order Date in descending order.
- Applied a State filter using Tamil Nadu.

**5. Data Aggregation**
Created three summary tables using the Group By feature:

- **Order Details Summary:** Order Count and Average Profit by Category.
- **Sub Category Summary:** Total Amount by Sub-Category.
- **Sales Target Summary:** Total Target by Month of Order Date.

**Custom Power Query M Expression – Profit Margin**

```powerquery
if [Amount] = 0 then null else [Profit] / [Amount]
```

The resulting Profit Margin column was formatted as a Percentage.

## 🧠 Data Modeling

**Model Type:** Relational Data Model.

**Tables Included:**

- List of Orders
- Order Details
- Sales Target
- Orders Data
- Order Details Summary
- Sub Category Summary
- Sales Target Summary

**Relationships Established:**

| Tables | Relationship Column | Cardinality |
|---|---|---|
| List of Orders ↔ Order Details | Order ID | One-to-Many |
| Order Details ↔ Sales Target | Category | Many-to-Many |

**Modeling Approach:**
- Used Order ID to connect List of Orders with Order Details.
- Used Category to connect Order Details with Sales Target.
- Configured and verified active relationships through Manage Relationships.
- Reviewed the overall table connections in Model View.

**DAX Usage:** No DAX measures or calculated columns were created in this project. All data transformations and aggregations were performed using Power Query Editor.

## 🖥️ Dashboard Features

**Project Scope:** Data Transformation and Data Modeling.

An interactive dashboard was not part of this assignment. However, the prepared datasets and summary tables provide a foundation for developing future reports, such as:

- Category-wise Order Count and Average Profit.
- Sub-Category-wise Total Amount.
- Month-wise Sales Target.
- Transaction-level Profit Margin and Profit Status analysis.
- State-wise order analysis.

## 💡 Key Insights

- **Data Integration:** Order and transaction information was combined into a consolidated Orders Data table using Order ID.
- **Category-Level Analysis:** Order Count and Average Profit were summarized by Category.
- **Sub-Category Analysis:** Total Amount was aggregated across different Sub-Categories.
- **Monthly Target Analysis:** Sales targets were grouped by Month of Order Date.
- **Data Model:** Relationships were established between the main datasets to organize the data for further analysis.

## 🚀 How To Use

1. **Prerequisites:** Install Microsoft Power BI Desktop.
2. **Repository Access:** Clone or download this GitHub repository.
3. **Open Project:** Open the `.pbix` file using Power BI Desktop.
4. **Data Source Configuration:** If the CSV files are moved to another location, update their paths through Data Source Settings.
5. **Explore Transformations:** Open Transform Data to review the applied Power Query steps.
6. **Explore Data Model:** Navigate to Model View to review the relationships between tables.

---

**Project Status:** Data Transformation & Data Modeling Completed  
**Tools Used:** Power BI Desktop | Power Query Editor | Power Query M | CSV Files  
**Project Level:** Beginner – Hands-on Learning Project
