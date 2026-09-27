# Digital Payments Analytics & Fraud Risk Monitoring

An end-to-end **Digital Payments Analytics and Fraud Risk Monitoring** solution built using **Python, SQL/MySQL, and Power BI** to analyze 250,000 UPI transactions, identify payment-performance patterns, analyze observed fraud, and monitor behavioral risk indicators.

The project follows a complete analytics workflow:

**Raw Data → Data Quality → Python/EDA → Feature Engineering → MySQL/SQL Analytics → Power BI → Business Insights**

---

## Project Overview

Digital payment platforms generate large volumes of transactional data that require continuous monitoring across payment performance, transaction behavior, observed fraud, and operational risk.

This project was developed to answer four core analytical questions:

1. **How is the payment ecosystem performing?**
2. **Where are transaction failures and observed fraud concentrated?**
3. **Which transaction behaviors represent higher-risk signals?**
4. **How can the analysis be converted into actionable business monitoring?**

The final solution combines Python-based data preparation, SQL analytics, explainable risk scoring, and an interactive Power BI dashboard.

---

## Key Metrics

| Metric                      |        Value |
| --------------------------- | -----------: |
| Transactions                |      250,000 |
| Transaction Value           |    ₹32.79 Cr |
| Average Transaction Value   |    ₹1,311.76 |
| Successful Transactions     |      237,624 |
| Failed Transactions         |       12,376 |
| Success Rate                |       95.05% |
| Failure Rate                |        4.95% |
| Observed Fraud Transactions |          480 |
| Observed Fraud Rate         |        0.19% |
| Analysis Period             | Jan–Oct 2024 |

> **Note:** The fraud rate represents the fraud flag available in the dataset. It should not be interpreted as an independently validated fraud-detection model output.

---

# Objectives

The project focuses on:

* Payment performance monitoring
* Transaction trend analysis
* Transaction-type analysis
* Observed fraud analysis
* Merchant-category fraud analysis
* Bank and state-level analysis
* Behavioral risk monitoring
* High-value transaction identification
* Transaction velocity analysis
* Executive-level reporting
* Interactive Power BI decision support

---

# Technology Stack

### Data Analysis

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn

### Database & Analytics

* MySQL
* SQL
* SQLAlchemy

### Business Intelligence

* Microsoft Power BI
* DAX
* Power Query

### Development & Documentation

* Jupyter Notebook
* Git
* GitHub

---

# Data Pipeline

```text
                    ┌─────────────────────┐
                    │   Raw UPI Dataset   │
                    │    250K Records     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Data Profiling &    │
                    │ Quality Validation  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Python / Pandas     │
                    │ Cleaning & EDA      │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Feature Engineering │
                    │ Risk Indicators     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ MySQL + SQLAlchemy  │
                    │ SQL Analytics Layer │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Power BI            │
                    │ Dashboard           │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Business Insights   │
                    │ & Risk Monitoring   │
                    └─────────────────────┘
```

---

# Analytical Workflow

## 1. Data Profiling

The raw transaction dataset was first profiled to understand:

* Dataset dimensions
* Data types
* Missing values
* Duplicate transaction IDs
* Categorical distributions
* Transaction amount distribution
* Timestamp coverage
* Fraud-flag distribution
* Transaction-status distribution

The dataset contains **250,000 transactions across 17 fields**.

---

## 2. Data Cleaning & Standardization

The cleaning workflow included:

* Standardizing column names
* Converting timestamps to datetime format
* Validating transaction amounts
* Checking duplicate transaction IDs
* Standardizing categorical values
* Validating transaction status
* Validating fraud flags
* Creating time-based analytical fields

Derived fields include:

* Hour of day
* Day of week
* Weekend indicator
* Transaction velocity indicators
* Transaction amount bands

---

# Exploratory Data Analysis

The EDA stage analyzed:

### Transaction Performance

* Transaction volume
* Transaction value
* Average transaction value
* Success rate
* Failure rate
* Monthly transaction trends

### Fraud Analysis

* Fraud volume
* Fraud rate
* Fraud value
* Fraud by transaction type
* Fraud by merchant category
* Fraud by state
* Fraud by bank
* Fraud by transaction amount

### Behavioral Analysis

* High-value transactions
* Night transactions
* Weekend transactions
* Transaction velocity
* Device and network behavior

---

# Risk Monitoring Methodology

The project uses an **interpretable, rule-based risk scoring framework**.

It does **not** claim to be a machine-learning fraud prediction model.

### Risk Indicators

Four behavioral indicators were created:

| Indicator         | Description                                                       | Weight |
| ----------------- | ----------------------------------------------------------------- | -----: |
| High Value        | Transaction above the 95th percentile                             |      2 |
| Night Transaction | Transaction during defined night hours                            |      1 |
| Weekend Activity  | Transaction occurring on a weekend                                |      1 |
| High Velocity     | Transaction activity above the 95th-percentile velocity threshold |      1 |

### Risk Score

```text
Risk Score =
    (High Value × 2)
    + Night Transaction
    + Weekend Transaction
    + High Velocity
```

Maximum score: **5**

### Risk Classification

```text
0–1  → Low Risk
2–3  → Medium Risk
4–5  → High Risk
```

These thresholds are **analyst-defined rules for this portfolio project** and are intended for monitoring and prioritization rather than automated fraud decisions.

---

# SQL Analytics Layer

The SQL layer was developed using **MySQL and SQLAlchemy**.

Key analytical queries include:

* Overall payment KPIs
* Transaction success/failure analysis
* Monthly transaction trends
* Month-over-month growth
* Fraud contribution by category
* Fraud rate by state
* Bank-level performance
* Risk-category analysis
* High-risk transaction analysis
* Daily fraud monitoring
* Rolling 7-day analysis

### Window Functions

`LAG()` was used to compare the current month's transaction value with the previous month and calculate month-over-month growth.

Conceptually:

```text
MoM Growth %
=
(Current Month Value - Previous Month Value)
/
Previous Month Value × 100
```

---

# Power BI Dashboard

The Power BI report contains seven analytical sections.

## 01 — Executive Payments Overview

Provides an executive-level view of:

* Transaction volume
* Transaction value
* Average transaction value
* Success rate
* Failure rate
* Fraud rate
* Payment trends
* Transaction-type performance

**Business question:**

> How healthy is the overall payment ecosystem?

---

## 02 — Transaction & Payment Performance

Analyzes:

* Transaction trends
* Payment success/failure
* Transaction value
* Transaction types
* Operational payment performance

**Business question:**

> How efficiently are transactions being processed?

---

## 03 — Participant Intelligence

Analyzes available participant and transaction attributes including:

* Age groups
* Transaction behavior
* Merchant categories
* Device types
* Network types

**Business question:**

> How does transaction behavior differ across participant and transaction segments?

---

## 04 — Fraud Intelligence

Analyzes observed fraud using:

* Fraud transactions
* Fraud rate
* Fraud value
* Transaction types
* Merchant categories
* Banks
* States
* Amount bands
* Fraud trends

**Business question:**

> Where is observed fraud concentrated?

---

## 05 — Risk Monitoring

Focuses on behavioral risk indicators:

* Risk categories
* High-value activity
* Night activity
* Weekend activity
* Transaction velocity
* Risk vs observed fraud
* Risk vs transaction value

**Business question:**

> Where are potentially risky transaction patterns appearing?

---

## 06 — Bank & State Performance

Compares:

* Bank transaction performance
* State transaction performance
* Success rates
* Failure rates
* Observed fraud rates
* Transaction volume and value

**Business question:**

> How does payment performance and observed fraud vary across banks and states?

---

## 07 — Executive Recommendations

Summarizes analytical findings and translates them into areas for:

* Monitoring
* Investigation
* Operational improvement
* Risk review

**Business question:**

> What should stakeholders investigate next?

---

# Key Analytical Distinction

The project separates **observed fraud** from **behavioral risk**.

### Observed Fraud

Based on the fraud flag available in the dataset.

```text
Observed Fraud
       ↓
Historical / recorded outcome
```

### Risk

Based on behavioral indicators engineered from transaction data.

```text
Behavioral Signals
       ↓
Risk Score
       ↓
Low / Medium / High
```

Therefore:

> **A high-risk transaction is not automatically a fraudulent transaction.**

The risk framework is intended to prioritize transactions or segments for further investigation.

---

# Business Insights

The analysis enables stakeholders to:

* Monitor overall payment health
* Track transaction growth and performance
* Identify failure patterns
* Compare payment types
* Identify segments with higher observed fraud rates
* Monitor high-value transaction activity
* Identify unusual transaction velocity
* Compare bank and state performance
* Prioritize potentially higher-risk transactions for investigation

---

# Project Structure

Digital Payments Fraud Intelligence/
│
├── README.md
│
├── Dashboard/
│   └── digital & fraud Dashboard.pbix
│
├── Database/
│   ├── Raw/
│   │   └── upi_transactions_2024.csv
│   ├── clean/
│   │   └── clean.csv
│   └── analytics/
│       ├── fraud_by_category.csv
│       ├── fraud_by_state.csv
│       ├── monthly_growth.csv
│       └── risk_analysis.csv
│
├── Notebook/
│   ├── 01_data_loading_and_profiling.ipynb
│   ├── 02_Data Cleaning & Standardization.ipynb
│   └── 03_Exploratory Data Analysis (EDA).ipynb
│
├── src/
│   └── Python/
│       ├── 01_load_to_mysql.ipynb
│       └── SQL Analytics Master Layer with SQLAlchemy.ipynb
│
├── image/
│   ├── HR_days_trend.png
│   ├── montly tranction value trend.png
│   └── montly UPI trend.png
│
└── screenshot/
    ├── page_01_executive_payments_overview.png
    ├── page_02_transaction_payment_performance.png
    ├── page_03_customer_participant_intelligence.png
    ├── page_04_fraud_intelligence.png
    ├── page_05_risk_monitoring.png
    ├── page_06_bank_state_performance.png
    ├── page_07_operational_failure_analysis.png
    └── page_08_executive_recommendations.png
```

---

# Data Quality

Before analysis, the dataset was checked for:

* Missing values
* Duplicate transaction IDs
* Invalid transaction amounts
* Invalid status values
* Invalid fraud flags
* Timestamp consistency
* Categorical consistency

The cleaned dataset contains **250,000 transaction records with no duplicate transaction IDs and no missing values across the analyzed fields**.

---

# Limitations

This project is designed as an **analytics and portfolio project**, not a production fraud-detection system.

Key limitations include:

* Risk weights are analyst-defined.
* Risk thresholds have not been production-validated.
* The fraud flag is treated as the available historical outcome.
* No machine-learning fraud classifier is currently deployed.
* The dataset covers January–October 2024 rather than the complete calendar year.
* Production deployment, real-time streaming and automated alerting are outside the current scope.

---

# Future Enhancements

Potential extensions include:

* Machine-learning fraud classification
* Anomaly detection
* Model performance monitoring
* Precision/recall-based risk validation
* Real-time transaction monitoring
* Automated risk alerts
* Drill-through transaction investigation
* Data-quality monitoring
* Cloud data warehouse integration
* Scheduled Power BI refresh
* Role-based dashboard access

---

# Skills Demonstrated

This project demonstrates practical experience with:

**Python**

* Pandas
* NumPy
* Data Cleaning
* EDA
* Feature Engineering

**SQL**

* Aggregations
* CASE statements
* CTEs
* Window Functions
* `LAG()`
* Analytical KPI calculations

**Power BI**

* Data Modeling
* Power Query
* DAX
* KPI Design
* Interactive Visualizations
* Dashboard UX
* Business Storytelling

**Analytics**

* Fraud analysis
* Risk segmentation
* Trend analysis
* Comparative analysis
* Business insight generation

---

# Project Outcome

The final solution transforms raw UPI transaction data into a structured analytics workflow covering:

**Data Quality → Transaction Analytics → Fraud Intelligence → Risk Monitoring → Executive Decision Support**

The project demonstrates how a Data Analyst can combine **Python, SQL and Power BI** to move from raw transactional data to actionable business insights.

---

## Disclaimer

This is a portfolio analytics project. The risk scoring framework is designed for analytical monitoring and demonstration purposes and should not be interpreted as a production financial fraud-detection or automated decision-making system.
