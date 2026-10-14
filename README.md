# Indian Banking Transactions Analysis (Excel Dashboard)

An end-to-end Excel project that turns raw Indian banking transaction data into an interactive dashboard for tracking transaction trends, channel performance, transaction status and fraud risk.

![Dashboard](images/dashboard.png)

## Business Objective

- Analyse transaction trends across regions, branches and months
- Identify fraud-prone branches, accounts and payment modes
- Compare digital, card and cash-based channels
- Track the share of Completed, Pending, Failed and Reversed transactions
- Give leadership a single, filterable view of the key banking KPIs

## Dataset

- **Rows:** 500 transactions (Jul 2023 to Jul 2025), total value about ₹9.39 Cr
- **Coverage:** 5 regions, 25 branches, 4 account types, 5 payment modes
- **Key fields:** Transaction ID, Customer ID and Name, Account Number, Region, City, Branch, Account Type, Transaction Type, Amount, Payment Mode, Date, Status, Balance After Txn, Is Fraud

## Workflow

1. **Data understanding:** classified each field as transactional, customer-level or derived
2. **Data cleaning:** checked duplicates, blanks, invalid values and naming consistency; rebuilt the empty `year_month` field; stored Account Number as text
3. **Feature engineering:** added derived columns (below)
4. **Analysis:** summary tables built with `COUNTIFS` and `SUMIFS`
5. **Dashboard:** KPI cards and charts driven by Region and Year drop-downs

## Derived Columns

| Column | Logic |
|---|---|
| `year_month` | Year and month from Transaction Date |
| `Year`, `Month Start` | Helpers for filters and the monthly trend |
| `Fraud_Flag` | 1 if Is Fraud = Yes, else 0 |
| `Transaction Category` | Digital (UPI, Net Banking), Card-Based (Debit, Credit), Cash-Based (Cash) |
| `Customer Type` | Frequent if the Customer ID has more than one transaction, else One-Time |

## Workbook Structure

| Sheet | Purpose |
|---|---|
| Dashboard | Filters, 12 KPI cards and 9 charts |
| Insights | Written findings for the full dataset |
| Analysis | Formula-based summary tables that feed the charts |
| Data | Cleaned 500 rows plus derived columns |
| Fraud Cases | The 13 fraud-flagged transactions |
| Cleaning Log | Live validation checks (all pass) |
| Data Understanding | Field dictionary and notes on the dataset |

## Dashboard Features

- Region and Year drop-down filters
- KPIs: total transactions, total value, average value, fraud rate, status percentages, category shares
- Charts: regional volume, monthly trend, channel donut, transaction type, status, transaction category, fraud rate by account type and by category, fraud by branch (stacked bar)

## Key Insights

- North has the highest volume (110 transactions); South the lowest (97)
- 86.8% of transactions completed, 5.2% failed, 4.2% reversed, 3.8% pending
- Fraud rate is 2.6% (13 cases); 11 of 13 were completed, so funds moved
- Bhopal Branch: 3 of 20 transactions flagged (15%)
- Savings accounts hold 7 of 13 fraud cases (6.0% rate), versus under 1% for FD and RD
- Cash-based payments have the highest fraud rate (5.1%), versus Digital (2.3%) and Card-Based (1.8%)
- Cheque and Online Transfer make up about 68% of total value

## Limitations

- Only 13 fraud cases, so segment and branch rates are volatile and should be treated as leads, not conclusions
- Every Customer ID appears once, so all customers are "One-Time" and loyalty analysis is not possible
- No separate Channel field (ATM, Branch, Mobile App); Payment Mode is used as the channel
- July 2025 is a partial month (data ends 6 July)

## How to Use

1. Download `Indian_Banking_Dashboard_Final.xlsx`
2. Open the **Dashboard** sheet
3. Use the yellow Region and Year drop-downs to filter all KPIs and charts
4. Do not delete rows or columns on the **Data** sheet, as the formulas depend on it

## Skills Demonstrated

Excel (formulas, charts, data validation) | Data Cleaning | Data Analysis | Dashboarding | Business Insights

## Repository Structure

```
├── Indian_Banking_Dashboard_Final.xlsx
├── README.md
└── images/
    └── dashboard.png
```

## Author

**Kiranbabu Kummari**
LinkedIn(www.linkedin.com/in/kiran-babu-kummari-163b69317) | Project completed as part of Innomatics Research Labs
