# AI-Powered Supply Chain Analytics Pipeline
(n8n | Supabase PostgreSQL | Quadratic)

## Project Overview
An automated supply chain ETL pipeline and performance analytics system built using n8n, Supabase, and Quadratic. The project automates order data ingestion via email triggers, resolves composite key constraints in PostgreSQL, and calculates core fulfillment metrics (OTIF %, IF %, OT %) across regional distribution hubs.

---

## Tech Stack and Architecture
* ETL and Automation: n8n (Gmail trigger -> File parsing -> PostgreSQL Upsert)
* Database and Storage: Supabase (PostgreSQL with composite primary key constraints)
* Data Analysis and Dashboards: Quadratic (SQL query execution and Python Pandas)

---

## Data Pipeline and Key Technical Fixes
1. Automated Ingestion: Daily order CSV files are parsed directly from Gmail attachments.
2. Database Conflict Resolution: Configured ON CONFLICT (order_id, order_placement_date) and ON CONFLICT (order_id, product_id) logic to execute seamless upserts without duplicate key constraint failures.
3. Fulfillment Analytics: Calculated key supply chain KPIs:
   * On-Time (OT %): Percentage of orders delivered on or before agreed dates.
   * In-Full (IF %): Percentage of orders delivered with complete item quantities.
   * On-Time In-Full (OTIF %): Percentage of orders meeting both criteria.

---

## Repository Structure
* /n8n: Exported workflow JSON pipeline and visual node diagrams.
* /supabase: DDL SQL schema scripts (schema.sql) including composite primary keys.
* /quadratic: SQL and Python analysis scripts for top customer KPI calculations.
* /data: Original sample datasets used for pipeline validation.

---

## How to Reproduce
1. Execute supabase/schema.sql inside your Supabase SQL Editor to build database tables.
2. Import n8n/workflow.json into n8n and configure your Postgres credentials.
3. Run SQL/Python code in quadratic/ to generate live fulfillment dashboards.
