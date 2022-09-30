# Data Engineering Foundations 
- Essential tools for data engineering by Harshit Tyagi
```The data engineer moves data from transactional databases to analytical databases to make life easier for the data scientist.```

## Processing Framekworks
- Data cleaning
- Data aggregation
- Data clustering
- Batch and stream processing

## Tools for Processing Frameworks
- Spark
- Hive
- Flink and Kafka

## Automation: scheduling
- Set up and manage workflows
- Plan jobs with specific intervals
- Resolve dependency requirements of jobs
- tools: Airflow, Oozie, Luigi, etc.

## Complete pipeline
- Step 1: user transactions / historical data / online analytics
- Step 2: Apache Spark
- Step 3: Processed data

## Database (definition)
- **A large collection of data organized in efficient structures and formats to support rapid search and retrival**

## Storage: database vs file system
- Structured data: relational database
- Semi-structured data: e.g. ``` {"key":"value"} ``` JSON
- Unstructured data: e.g. video, images, text files

## SQL vs NoSQL
- Relational database vs No
- Database schema vs structured or unstructured
- Tables vs key-value e.g. JSON

## Database Schema
- A **schema** describe the strucutre and relations of a database
  - SQL: Star Schema: consists of one or more fact tables referencing any number of dimension tables
    - Facts: events that happened (e.g. order)
    - Dimensions: information in the world (e.g. customer details)

## Major tasks for Distributed computing (parallel computing)
```one task split into multiple subtask```
- collect data from different sources, join, clean, and aggregate
- Benefit
  - more processing power
  - more scalable
  - cost effective
  - fault tolerant
- Risk
  - Overhead due to communication between nodes (bottleneck)
  - Suitable for large task 
  - parallel slow down (non-linear)

## Tools:
- Hadoop: a collection of open-source projects, maintained by the Apache Software Foundation
  - Framework for distributed processing of large data
  - Use the MapReduce algorithm
  - - MapReduce: a processing technique and a program model for distributed computing based on Java (hard to write jobs)
  - HDFS (Hadoop Distributed File Sytem)
- Hive: a layer of on top of the Hadoop
  - enable SQL-like interface to query data e.g. Hive SQL
- Spark: 
  - distributed data proceesing tasks between clusters
  - processing done in memory instead of in disk
  - rely on resilient distributed datasets (RDDs)
    - RDD: data across multiple nodes, immutable (ready-only), partitioned
    - Transformations - transformed RDD: e.g. filter(), map(), groupByKey(), union()
    - Actions - single result: e.g. count(), first(), collect(), reduce()
  - PySpark, similar to pandas
- **Workflow** orchestrate different ETL tasks
  - Directed Acyclic Graph (DAG): a collection of all the tasks that need to be run, organized in a way reflects their relationship and dependencies (Set of nodes, directed edges, no cycle)
- Apache Airflow: tool for describing, executing, and monitoring workflows and pipelines. (DAG, Python)

- Extraction from files
  - Unstructred: plain text e.g. number of documents
  - Flat: e.g. ```.csv or .tsv``` (comma / tab separated files)
  - semi-structured: e.g. JSON (JavaScript Object Notation: atomic, composite elements)

- Data through API (typically JSON)
- Data from Databases
  - 1. Online Transaction Processing (**OLTP**): application, row oriented, stored per record
  - 2. Online Analytical Processing (**OLAP**): analytical, column oriented, aggregated, parallelization
