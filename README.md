# Metadata-Driven End-to-End Azure Lakehouse Platform

**Core Ecosystem:** ☁️ Microsoft Azure | 🧱 Azure Databricks | 🔥 Apache Spark | 🤖 GitHub Actions CI/CD

##  Executive Summary & Business Impact
This repository showcases a production-grade, fully automated **Metadata-Driven End-to-End Azure Data Engineering Platform**. Built on a modern **Lakehouse Architecture**, the framework decouples compute and storage while maintaining strict enterprise data governance, unified cataloging, and automated infrastructure delivery.

###  Why this matters to Engineering Managers:
* **Dynamic Metadata-Driven Ingestion:** Eliminates hardcoded ETL code. Uses an orchestration framework controlled entirely via a central metadata repository to scale ingestions horizontally.
* **Unified Governance & Audit Trail:** Implements data lineage, schema enforcement, and role-based access controls across storage layers.
* **Enterprise Security Framework:** Utilizes zero-trust token fetching boundaries to guarantee zero credential leakage within public or private source code.
* **GenAI-Ready Data Delivery:** Models transactional data down to analytical formats optimized for traditional dashboards as well as modern **LLM-driven Data Agents**.

---

##  Technical Architecture & Data Flow

As detailed in the architecture blueprint, the system isolates operational concerns into five specialized pillars:

### 1. Data Sources
The platform ingests transactional data simultaneously from both structured and unstructured storage fabrics:
* **PostgreSQL Database:** Relational transaction storage containing master datasets.
* **Azure Blob Storage:** Object store holding raw file drops and landing structures.

### 2. Orchestration & Data Ingestion
* **Azure Data Factory (ADF):** Governs control flow, executing programmatic, parameterized ingestion loops from source layers.
* **Azure SQL Database (Metadata + Auditing):** Functions as the state engine for the orchestration system. It stores execution logs, dynamic source parameters, watermarks, and pipeline auditing footprints.

### 3. Data Transformation (Medallion Engine)
Processing is handled by **Azure Databricks** backed by the open-source **Apache Spark** computing core over optimized **Delta Lake** formats:
* **Bronze (Raw Layer):** Appends raw data drops directly from source systems to maintain transactional history.
* **Silver (Cleaned Layer):** Performs schema enforcement, complex column normalization, data deduplication, and automated formatting checks.
* **Gold (Curated Layer):** Builds highly optimized, aggregated business-ready dimensions and facts ready for business logic application.

### 4. Governance, Security & CICD
* **Unity Catalog:** Centralized data governance tool managing asset cataloging, lineage tracking, and granular table-level security policies.
* **Azure Key Vault:** Central cryptographic boundary holding pipeline credentials, service principal secrets, and managed token pairs.
* **Azure Logic Apps:** Event-driven notifier dispatching immediate status telemetry and diagnostic alerts via email/Slack when SLA execution milestones are missed.
* **GitHub Actions:** Provides the automated continuous integration and continuous deployment engine promoting code artifacts seamlessly from development environments to staging and production.

### 5. Consumption Tier
Data objects curated inside the Gold layer are delivered to three strategic data consumption vectors:
* **Databricks Dashboards:** High-performance, native real-time analytical visuals.
* **Databricks Genie:** Conversational Business Intelligence engine allowing business users to interrogate data fabrics safely using standard natural language queries.
* **Databricks Genie Agents:** Purpose-built, autonomous LLM agents pulling data inputs programmatically for down-stream predictive analytical pipelines.

---

##  Technology Ecosystem
* **Core Compute:** Apache Spark / PySpark / Spark SQL
* **Storage Framework:** Delta Lake Format on ADLS Gen2
* **Ingestion/Orchestration:** Azure Data Factory (ADF) & Azure SQL DB
* **Identity & Access Management:** Azure Key Vault (AKV) & Databricks Secret Scopes
* **Data Governance Platform:** Databricks Unity Catalog
* **Workflow Alerts Engine:** Azure Logic Apps
* **Source Code & DevOps:** GitHub (Git Flow Integration)

---

##  Key Technical Deliverables Highlighted
* **Zero Credential Exposure:** 100% compliance using service accounts integrated via Key Vault Secret Scopes.
* **Metadata-Driven Scalability:** The ADF pipeline reads source configurations dynamically from Azure SQL DB tables, enabling the ingestion of new data tables without modifying a single pipeline component.
* **Advanced ACID Capabilities:** Full integration of Delta Lake optimization techniques including Z-Ordering, data time-travel log extraction, and schema evolution.
* **LLM Semantic Layer Setup:** Configured specialized Gold schema contexts enabling Databricks Genie interfaces to accurately translate natural language text into high-performance analytical Spark SQL.

---

##  Repository Layout
```text
├── .github/workflows/      # Automated deployment automation files
├── adf/                    # Azure Data Factory templates (JSON configurations)
│   ├── pipeline/           # Parameterized ingestion loops
│   ├── linkedservice/      # Key Vault bounded connection templates
│   └── dataset/            # Dynamic dataset schemas
├── sql-metadata/           # DDL scripts for Ingestion Metadata & Audit Tables
├── databricks/             # Scalable transformation code
│   ├── 01_bronze_to_silver.py   # Cleansing, schema typing, and validation filters
│   └── 02_silver_to_gold.py     # Aggregation, modeling, and Genie semantic setups
├── logic-apps/             # SLA alerting workflow definitions
└── README.md               # Architecture documentation
```
