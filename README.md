# 📊 AdventureWorks Executive Sales Intelligence Dashboard

An enterprise-grade, end-to-end business intelligence application transforming raw transactional databases into dynamic, decision-ready analytics.

## 🛠️ Data Architecture & Tech Stack
* **Data Source:** Microsoft SQL Server (AdventureWorks 2025 OLTP Relational DB)
* **Storage Mode:** Import Mode (Optimized Star Schema architecture)
* **Calculations Engine:** Advanced DAX (Context-aware ranking, rolling time intelligence arrays)
* **Version Control:** Power BI Project (`.pbip`) format tracked natively with Git

## 📈 Dashboard Architecture & Core Layout
1. **Executive Command Row:** Tracks key financial metrics globally using interactive territory slicers paired with reactive conditional warning rules.
2. **Dynamic Trend Window:** Utilizes programmatic `SWITCH` DAX architecture allowing users to dynamically switch axes between gross financial values and order totals.
3. **Product Performance Core:** Implements a recursive `RANKX` algorithmic lookup table to evaluate top-moving stock models instantly.

## 🧠 Advanced DAX Code Showcases

### 1. Context-Aware Dynamic Product Rank (Top N)
```dax
Product Revenue Rank = 
IF(
    ISINSCOPE(Dim_Products[Name]),
    RANKX(
        ALLSELECTED(Dim_Products),
        [Total Revenue],
        ,
        DESC
    ),
    BLANK()
)
```

### 2. Moving 12-Month Rolling Revenue
```dax
Rolling 12M Revenue = 
CALCULATE(
    [Total Revenue],
    DATESINPERIOD(
        Dim_Date[Date], 
        MAX(Dim_Date[Date]), 
        -12, 
        MONTH
    )
)
```

## 🗄️ Local Replication & Environment Setup
1. Restore the `AdventureWorks2025.bak` transaction file onto your local SQL Server instance.
2. Open `Sales-Intelligence-Dashboard.pbip` inside Power BI Desktop.
3. If prompted, change the SQL Server Connection string data source parameter settings to match your local `localhost` network footprint.
