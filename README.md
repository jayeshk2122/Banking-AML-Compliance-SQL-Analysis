# Banking & Anti-Money Laundering (AML) Compliance Monitoring (SQL)

## 📌 Project Overview
This project simulates a core banking compliance and transaction monitoring workflow using **Microsoft SQL Server (SSMS)**. Drawing on domain knowledge in banking operations and financial governance, I designed a normalized 3-table relational database (`Customers`, `Accounts`, `Transactions`) and wrote analytical SQL queries to detect suspicious wire transfers, non-compliant KYC activity, high-risk customer exposure, and dormant accounts.

## 🛠️ Tools & SQL Concepts Used
* **Database Engine:** Microsoft SQL Server (T-SQL) / SSMS
* **Database Design (DDL & DML):** `CREATE DATABASE`, `CREATE TABLE`, `PRIMARY KEY`, `FOREIGN KEY`, `INSERT INTO`
* **Data Filtering & Compliance Rules:** `SELECT`, `WHERE`, `IN`, comparison operators (`>`, `!=`), `IS NULL`
* **Multi-Table Relationships:** `INNER JOIN`, `LEFT JOIN` (Anti-Join pattern), table aliasing

## 🗂️ Database Schema
The database (`banking_aml_project`) consists of three interconnected tables:
1. **`Customers`**: Stores customer ID, full name, KYC verification status (`Verified`, `Pending`, `Expired`), risk rating (`Low`, `Medium`, `High`), and city.
2. **`Accounts`**: Tracks account ID, customer ID (FK), account type (`Savings`, `Current`), current balance (INR), and account opening date.
3. **`Transactions`**: Logs transaction ID, account ID (FK), transaction date, transaction type (`Deposit`, `Withdrawal`, `Wire Transfer`), amount (INR), and counterparty country.

## 🚨 Compliance & AML Scenarios Solved
1. **High-Value Transaction Threshold Alert (`INNER JOIN` + `WHERE`):** Flagged single transactions exceeding ₹5,00,000 (*Neha Kapoor* and *Siddharth Verma*) for Enhanced Due Diligence (EDD).
2. **Cross-Border Wire Transfer Audit (`JOIN` + `!=`):** Isolated offshore fund transfers sent outside India (*Cayman Islands* and *Panama*) alongside customer risk ratings.
3. **Non-Compliant KYC Activity Detection (`JOIN` + `IN`):** Identified active transactions executed by customers with `'Pending'` or `'Expired'` KYC status (*Neha Kapoor* and *Rajeshwari Nair*).
4. **Dormant / Zero-Activity Account Detection (`LEFT JOIN` + `IS NULL`):** Used an anti-join pattern to locate opened accounts with zero transaction history (*Meera Joshi*) for branch follow-up.
5. **High-Risk Customer Exposure Report (`JOIN` + `WHERE`):** Generated an exposure summary displaying total balances held by `'High'` risk customers across branches.

## 🚀 How to Run This Project
1. Open **SQL Server Management Studio (SSMS)** and connect to your local SQL Server instance.
2. Open `banking_aml_monitoring.sql` from this repository.
3. Highlight and execute (`F5`) the DDL and DML sections to create the database and sample records.
4. Highlight and execute each commented compliance query individually to inspect the audit outputs.
