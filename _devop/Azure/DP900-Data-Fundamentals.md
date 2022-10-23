---
layout: blog
topic: Azure
title: DP-900 Data Fundamentals
tags:  datascience daa
comments: true
date: 2022-10-22
---

# DP-900: Data Fundamentals

## Azure SQL Family of Services

![](/assets/2022-10-22-00-24-31.png)

[https://azure.microsoft.com/en-us/blog/the-azure-sql-family-innovation-and-value-in-the-cloud/](https://azure.microsoft.com/en-us/blog/the-azure-sql-family-innovation-and-value-in-the-cloud/)


## Database Administrator Tools

- Azure Data Studio
  - Graphic interphase for managing on-premises and cloud-based data services
  - Runs on Windows, Mac and Linux
- SQL Server Management Studio
  - Runs on Windows
  - More mature than Azure Data Studio
- Azure Portal and CLI
  - Manage SQL database configurations

## Data Engineering Tools

- Azure Synapse Studio
  - A central portal to manage Azure Synapse, Azure data factory (data ingestion) and Synapse assets (SQL/Spark pools)
- Knowledge SQL
  - Create databases, tables, views, etc
- Azure CLI
  - Support SQL command to connect to Microsoft Server
- HDInsights
  - Streaming data or applying ELT jobs via HIVE, PIG, Apache Spark
- Azure dATABRICKS
  - Streaming data or applying ELT jobs via Apache Spark

## Data Analyst Tools
- Power BI

## Batch Vs Stream Processing

- Batch Processing
  - Not real time
  - Ideal for large processing workloads
  - Cost effective

- Stream Processing
  - Offer real-time analytics
  - More expensive


## Normalized vs Denormalized data

- Normalized data
  - Easier to maintain data integrity
  - Little to no redundant data
  - Optimized for data storage
  - Querying is slower

- Denormalized data
  - Harder to maintain data integrity
  - Redundant data is common
  - Storage is less optimal
  - Querying is fast

## Strongly vs Eventual Consistency

- Strongly consistent
  - Each query returns the most update to date (consistent) data
  - At the cost of high latency

- Eventually consistent
  - Query may return stale data at first 
  - Time taken to get consistent may or may not be defined.
  - Low latency


## Synchronous vs Asychronous Data Trasmission

- Synchronous
  - Sender and receiver are permanently synchronized using a common timing signal
  - Guarantee consistency of data at time of access
  - Can only access data once transfer is complete
  - e.g. chat app, streaming services
  
- Asychronous
  - Sender and receiver are synchronized only during transmission, by a starting bit and a stop bit
  - No guarantee of consistency
  - Can access data anytime
  - e.g. email


## Data Storage

### Data Warehouse
- A central repository of relational data designed for analytical purpose
- Can return queries very fast

### Data Mart
- A subset of data warehouse, allowing teams or department to have control over their own datasets
- Generally read only

### Data Lake
- A centralized repository that holds vast amount of raw data in structured, semi-structured, or unstructured form
- Mainly designed for machine learning and big data analysis

### Data Lakehouse
- Compoared to a data warehouse:
  - Support video, audio and text files
  - Support data science and ML workloads
  - Support both ELT and streaming
- Compared to a data lake:
  - Perform BI tasks well
  - Easier to set up and maintain
  - More management features

## Data Structure

### Unstructured data
- A bunch of loose data
- MS products: Sharepoint, Azure Blob Storage, Azure files, Azure Data Lake

### Semi-structured data
- Has some form of relationship
- e.g. XML, JSON, AVRO, PARQUET, Optimized Row Columnar format (ORC)
- MS products: Azure Tables, Azure CosmoDB, MongoDB, Apache Cassandra

### Structured data
- Most common structure is tabular
- MS products: MySQL, Postgres, Azure SQL, Azure Synapse Analytics