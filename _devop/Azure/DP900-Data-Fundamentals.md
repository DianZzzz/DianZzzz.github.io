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

## OLAP vs OLTP
- OLAP: Online Analytical Processing 
  - Multiple data sources
  - Long and complex queries, with an emphasis on read (SELECT)
  - Few transactions
  - Throughput sensitive 
- OLTP: Online Transaction Processing
  - Single data source
  - Short query, with an empahsis on write (INSERT, UPDATE, DELETE)

![](/assets/2022-10-23-16-53-41.png)

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
  - XML: a markup lanaguage that looks similar to HTML
  - JSON: a text file that is composed of dictionaries and arrays
  - RCFiles: a storage format designed for MapReduce framework
  - ORC: a columnar data structure that's 75% more efficient than RCFiles; works well with HIVE
  - AVRO: a row wise data structure for Hadoop system
  - PARQUET: a columnar data-structure for Hadoop system
- MS products: Azure Tables, Azure CosmoDB, MongoDB, Apache Cassandra

### Structured data
- Most common structure is tabular
- MS products: MySQL, Postgres, Azure SQL, Azure Synapse Analytics

## ELT vs ETL

- Extract, Transform and Load
  - Loads data first into a staging server and then to the target system
  - Used for on-premise, relational and structured data
  - Commonly used for small amount of data
  - Doesn't provide data lake suport
  - Easy to implement

- Extract, Load and Transform
  - Loads data directly into the target system
  - Used for scalable structured and unstructured data
  - Used for large amount of data
  - Provide data lake support
  - Require specialized skills to implement 

## Data Analytics

![](/assets/2022-10-23-01-05-39.png)

- Description analytics - what happened?
- Diagnostic analytics - why did it happen?
- Predictive analytics - what will happen?
- Prescriptive analytics - how can we make it happen?
- Cognitive analytics - what if this happens?

## Azure Synapse Analytics

- A data warehouse and unified analytics platform
- Synapse SQL is a distributed version of T-SQL with built-in streaming capabilities to load data from cloud data sources
- Offer both serverless and didicated resource models
  - Serverless: for unpredicable workloads
  - Dedicated: for predictable workloads
- Can seamlessly integrate with Apache Spark

## Azure Blob

- Blob is a object-store that is optimized for storing massive amount of unstructured data
- Azure Storage supports 3 types of blobs:
  - Block blobs
    - Store text and binary data
    - Can be managed invidividually
    - Store up to 4.75 TB of data
  - Append blobs
    - Optimized for append operations
    - Ideal for scenarios such as logging data
  - Page blobs
    - Store random access files up to 8TB
    - Store virtual hard drive files and serve as disks for Azure virtual machine

## Read Replica
- A copy of the database that is kept sync with the original database
- Used to  offload read requests or analytics traffic from the primary instance

## Connectivity Architecture
- Proxy
  - Connections are proxies through a gateway
  - Increased latency and reduced throughput
  - Intended for workloads from outside the Azure network
- Redirect
  - Direct connection
  - Reduced lantecy and improved throughput
  - Intending for workloads from inside the Azure network 

## Public vs Private Endpoint
- Public: reachable outside the Azure Network over the Internet
- Private: only reachable within the Azure Network
## Role-Based-Access-Controls (RBAC)
- SQL DB Contributor
  - Manage SQL databases
  - Cannot give access to others
- SQL Managed Instance Contribute
  - Manage SQL Managed Instances and require network configuration
  - Cannot give access to others
- SQL Server Contributor
  - Manage SQL servers and databases
  - Cannot give access to others
- SQL Security Manager
  - Manage the security-related policies of SQL servers and databses
  - Cannot give access to others

## Transparent Data Encryption
- Encrpyts data-at-rest
- Uses a database entryption key (DEK) which is a symmetric key (same key used for both encryption and decryption)
- Can be applied to 
  - SQL Server
  - Azure SQL Database
  - Azure Synapse Analytics

## Dynamic Data Masking
- A central data masking policy acts directly on sensitive fields in the database.
- Designate privileged users or roles that do have access to the sensitive data.

## Private Links
- Allows secure connections between Azure resources so traffic remains within the Azure network

## Mongo DB
- An open-source database that stores JSON-like documents
- The primary data structure is called Binary JSON (BSON)
  - Has more data-types than JSON
  - Designed to be efficient both in storage space and scan speed