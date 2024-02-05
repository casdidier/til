# definition

A data warehouse is an enterprise system used for the analysis and reporting of structured and semi-structured data from multiple sources.
They support ad hoc analysis and custom reporting, such as data pipelines, queries, and business applications. They can consolidate and integrate massive amounts of current and historical data in one place and are designed to give a long-range view of data over time. These data warehouse capabilities have made data warehousing a primary staple of enterprise analytics that help support informed business decisions.

key capabilities that cloud data warehouses include:

- Massively parallel processing (MPP)
- Columnar data stores
- Self-service ETL and ELT data integration
- Disaster recovery features and automatic backups
- Compliance and data governance tools
- Built-in integrations for BI, AI, and machine learning

eg: BigQuery, Snowflake,

## database (db) vs data warehouse (dh) vs data lake (dl)

database is OLTP(online transactional process) based process and is good for capturing record detailed live real time data on a flexible schema
data warehouse is good for OLAP (analytical process), has data refreshed from data sources (historical) on a rigid schema
data lake captures everything (any type of structure) made for lage amount for AI and ML , can inject into DB and DW
