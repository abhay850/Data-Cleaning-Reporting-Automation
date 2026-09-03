# 📊 Employee Data Cleaning & Reporting Automation

A data cleaning and reporting project that takes a messy employee dataset (1,020 rows), cleans and standardizes it, and presents the results as an interactive Power BI dashboard. ✨

## 📁 Project overview

| | |
|---|---|
| **Dataset size** | 1,020 employee records |
| **Tools used** | Microsoft Excel / WPS Office, Power Query, Power BI Desktop |
| **Columns** | Employee_ID, First_Name, Last_Name, Age, Department, Region, Status, Join_Date, Salary, Email, Phone, Performance_Score, Remote_Work |

## 🗂️ Files in this repository

| File | Description |
|---|---|
| `Messy_Employee_dataset.xlsx` | The original, uncleaned raw dataset |
| `Employee_dataset_CLEANED.xlsx` | The final cleaned and standardized dataset |
| `Employee_Data_Cleaning_Report.pbix` | Power BI report file (open in Power BI Desktop for the interactive dashboard) |
| `Employee_Data_Cleaning_Report.pdf` | Static PDF export of the dashboard, for quick viewing without Power BI |
| `README.md` | This file |

## 🧹 Data cleaning steps

The raw dataset had several data quality issues. Each was identified and fixed as follows:

| Column | Issue found | Rows affected | Action taken |
|---|---|---|---|
| Age | Missing values | Filled | Filled using an appropriate method |
| Salary | Missing values | Filled | Filled using an appropriate method |
| Phone | Negative numbers, and leading zeros lost when values were stored as numbers | 93 fixed, 1 unrecoverable | Converted to positive, zero-padded back to 10 digits. One row (EMP2019) had no recoverable number and was left as missing |
| Department_Region | Combined into a single field | 1,020 rows | Split into two separate columns: Department and Region |
| Status | Corrupted or missing values | Recovered | Values restored to valid categories (Active / Inactive / Pending) |
| Join_Date | Mixed date formats (e.g. `04-02-2021` and `7/17/2022`) | 1,020 rows | Standardized to a single `DD Month YYYY` format (e.g. `04 February 2021`) and locked as a true date type |

After cleaning, the dataset was verified column by column: no missing values remain except the one unrecoverable phone number, no duplicate Employee_IDs, all emails are valid, and all categorical fields (Department, Region, Status, Performance_Score, Remote_Work) contain only clean, expected values.

## ⚠️ Key data quality notes

- **Phone numbers**: stored as text (not numbers) in the final file to preserve leading zeros. If re-exporting to CSV, this formatting will be lost — always save as `.xlsx`, not `.csv`.
- **Join_Date**: stored as a true date value with a fixed display format, so it won't drift when reopened in Excel or Power BI.

## 📈 Power BI report

The `.pbix` file contains a single-page dashboard with:

- **Total employees** summary card
- **Cleaning summary table** — a record of every issue found and fixed
- **Status distribution** (Active / Inactive / Pending) — pie chart
- **Employees by department** — bar chart
- **Average salary by region** — column chart
- **Performance score distribution** — donut chart
- **Remote work split** (remote vs. office) — pie chart
- **Hiring trend by year** (2020–2024) — line chart



## 💡 Key insights

- Headcount is fairly evenly spread across departments, with DevOps the largest (189) and Cloud Tech the smallest (146)
- Average salary is consistent across all six regions (roughly $83.6K–$86.6K), showing no major regional pay disparity
- Performance scores are well distributed across Excellent, Good, Average, and Poor categories
- The workforce is close to an even split between remote (513) and in-office (507) employees
- Hiring dipped in 2022 before rising sharply in 2023

## 🙋 Author

**Abhay Tiwari**
