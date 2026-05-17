# 🔄 Enterprise Cross-Platform Database Migration & Inventory Analytics Pipeline


## 📌 Project Overview
This project engineering showcase simulates a real-world enterprise lifecycle: transitioning data operations from a **Testing Environment (Test Env)** to a **Production Environment (Prod Env)**, followed by a full **Cross-Database Migration (MS SQL Server to Oracle MySQL)**. 

Instead of deploying standard static models, this architecture handles complex database staging pipelines, structural inconsistencies across platforms, data anomalies, and dynamic backend switching inside **Power BI via Advanced Power Query M-Code manipulation**, preserving upstream semantic data models and DAX configurations perfectly.

---

## 🏗️ Technical Architecture & Pipeline Flow
The project workflow guarantees a decoupling of data storage layers from analytical visualizations, ensuring zero downtime or structural breakages during database migration workflows.

```text
[Phase 1: Test CSVs] ──> MS SQL Server (test_env) ──> Left Join Transformation ──> Power BI Report V1
                                                                                              │
[Phase 2: Prod CSVs] ──> MS SQL Server (PROD) ───> Data Cleansing & Mapping ──────> Power BI Report V2
                                                                                              │
[Phase 3: Migration] ──> MySQL Workbench (prod) ─> M-Code Schema Redirect ────────> Final Published BI Solution
```

---

## 🛠️ Step-by-Step Engineering Execution Workflow

### 🔹 Step 1: Testing Environment Simulation & Schema Assessment (SQL Server)
The process initiated by establishing a controlled database sandbox environment inside **Microsoft SQL Server Management Studio (SSMS)** to analyze data integrity, column behaviors, and foundational entity relationships.

1. Formulated the infrastructure sandbox by initializing the testing layer:
```sql
CREATE DATABASE test_env;
USE test_env;
```

2. Ingested `Test+Environment+Inventory+Dataset.csv` and `Products.csv` tables. Analyzed historical metric data and distribution variables to establish boundaries.

3. Structured an unified relational layer by engineering a comprehensive `LEFT JOIN` pipeline query to model product variables alongside supply-chain inventory availability metrics:
```sql
SELECT a.order_date_dd_mm_yyyy, a.product_id, a.availability, a.demand, b.product_name, b.unit_price
FROM [dbo].[Test+Environment+Inventory+Dataset] as a
LEFT JOIN products as b ON a.product_id = b.product_id;
```

4. Materialized this unified transformation sequence securely directly into an optimized schema structure called `New_table` to enable early-stage testing in Power BI.

---

## 📊 Analytical Data Modeling & DAX Blueprint
Directly after setting up Step 1, the analytical engine was constructed by consolidating all business logic into a single dedicated **Measures Table** to drive cross-page execution parameters.

### 📈 Page 1 & Page 2 Analytics (Operational & Financial KPI Dashboard)
Focuses on tracking core commercial values, asset velocity distributions, total portfolio capital, and risk management variables.

#### 🖼️ Dashboard Preview
<!-- PLACE YOUR DASHBOARD SCREENSHOT HERE -->

<img width="1298" height="745" alt="Screenshot 2026-05-17 155833" src="https://github.com/user-attachments/assets/30e03675-75c3-4235-8d2f-f377db64fc74" />

<img width="1298" height="755" alt="Screenshot 2026-05-17 155900" src="https://github.com/user-attachments/assets/8b2fb1e5-8a15-48e5-8eda-3b10348abab8" />


* **Isolated Metric Architecture:** All explicit system formulas are isolated into a single unified workspace table for high-performance processing.
* **Dynamic Slicing Capabilities:** Integrated page-level interactive matrix structures leveraging built-in backend engine layers:
  * **Product Name Filtering:** Evaluates localized distribution velocity patterns across isolated stock categories (`product_name`).
  * **Timeline Axis Filtering:** Slices multi-period variables dynamically using sequential operational logging configurations (`order_date_dd_mm_yyyy`).

---

### 🔹 Step 2: Production Environment Ingestion & Data Cleansing
Moving from sandbox validation to active implementation, data models were scaled up inside a newly engineered Production Database.

1. Provisioned the isolated live operational database:
```sql
CREATE DATABASE PROD;
USE PROD;
```

2. **Data Anomaly Rectification:** Discovered underlying mapping issues where product reference keys contained architectural mismatches (IDs 21 and 22 were corrupt and did not map cleanly into the core operational master files). Engineered relational structural fixes via transaction updates:
```sql
UPDATE dbo.[Prod+Env+Inventory+Dataset] SET Product_ID = 7 WHERE Product_ID = 21;
UPDATE dbo.[Prod+Env+Inventory+Dataset] SET Product_ID = 11 WHERE Product_ID = 22;
```

3. Re-applied enterprise modeling transformations to generate an optimized unified reporting script block within the finalized environment schema layer.
4. **Environment Hot-Swapping Integration:** Fully tested environmental resilience by executing schema migrations back and forth utilizing the local `Data Source Settings` parameters (`test_env` 🔄 `PROD`) to guarantee structural field durability.

### 🔹 Step 3: Cross-Platform Migration Implementation (SQL Server ➡️ MySQL)
To align data infrastructure with modern application microservices, the enterprise backend storage layer was completely migrated into **MySQL Database Engine**.

1. Formulated a parallel structure inside **MySQL Workbench** to accept live system assets securely.

2. Rewrote underlying legacy queries into optimized MySQL-compliant dialects, dynamically adjusting naming mechanics to seamlessly run transformations across varying database engines:
```sql
USE prod;

CREATE TABLE New_Table AS 
SELECT 
    a.`Order Date (DD/MM/YYYY)` AS order_date_dd_mm_yyyy, 
    a.`product ID` AS product_id, 
    a.availability, 
    a.demand, 
    b.`product Name` AS product_name, 
    b.`Unit Price ($)` AS unit_price
FROM `prod`.`prod+env+inventory+dataset` a
LEFT JOIN `prod`.`products` b ON a.`product ID` = b.`product ID`;
```

### 🔹 Step 4: Advanced Power Query M-Code Source Transitioning
Instead of rebuilding the analytical dashboards from scratch—which would discard critical DAX models, user hierarchies, and custom formatting layers—the underlying analytical platform infrastructure was updated utilizing structural **M-Code engineering overrides**.

1. Initiated the multi-tier reporting application framework within the initial SQL Server system dependencies.
2. Entered the **Advanced Editor** parameters within the system Power Query console interface.
3. Manipulated the structural data connectivity layer functions, dynamically migrating system properties from `Sql.Database` variables directly over to live active `MySQL.Database` nodes while preserving internal downstream field conversions intact:
```powerquery
// Structural Transformation Logic Inside Advanced Editor
Source = MySQL.Database("localhost", "prod", [ReturnSingleDatabase=true]),
Navigation = Source{[Schema="prod", Item="New_Table"]}[Data]
```
4. Validated calculation contexts across all downstream analytical visual nodes to verify complete data parity.

---

## 🛠️ Technology Ecosystem Stack
* **Relational Database Management Systems:** Microsoft SQL Server Management Studio (SSMS), Oracle MySQL Workbench
* **Business Intelligence & Reporting Suite:** Power BI Desktop, Power Query Engine, Power BI Service Cloud Architecture
* **Development Query Languages:** Transact-SQL (T-SQL), MySQL Dialect Scripting, Power Query M-Code, Data Analysis Expressions (DAX)

---

### 🤝 Professional Affiliations & Portfolio Channels
I specialize in transforming disjointed data structures into robust analytics solutions.

* **LinkedIn Profile:** [Charan Kumar Donthula](https://linkedin.com)
* **GitHub Code Space:** [charankumar08](https://github.com)

*Thank you for evaluating this enterprise data migration architecture framework. For queries regarding M-Code adjustments, feel free to drop a message.*
