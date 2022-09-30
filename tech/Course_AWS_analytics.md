# Note: Data Analytics Fundamentals
https://explore.skillbuilder.aws/learn/course/44/play/483/data-analytics-fundamentals

### The challenges identified in many data analysis solutions can be summarized by five key challenges: 
- **volume, velocity, variety, veracity (trustworthiness), and value**
- Note: veracity is the degree to which data is accurate, prcise, and trusted. It is contingent on the integrity and trustworthiness of the data. (data cleansing: fix the data flows before storing)

### A data analysis solution includes the following components
- Ingest/collect: ingest a wide variety of data - structured, semistructured, and unstructured - at any speed, from batch to streaming.
- Store: secure, scalable, and durable storage
- Process/analyze:make data more consumable - applying business logic to produce meaningful analytical dataset, which will be loaded into a new storage location (data lake, database, or data warehouse).
- Consume/visualize: querying by analyst or Business Intelligence (BI) tools

### Data lake (Amazon S3 bucket)
- store structured, semistructured, and unstructured data
- once stored, an object key will be assigned.
- An object key is the unique identifier for an object in a bucket. 
- Below is an example of a URL for a single object in a bucket named doc, with an object key composed of the prefix 2006-03-01 and the file named AmazonS3.html.
- ![s3 bucket schematic](https://github.com/er1czz/tech_notes/blob/main/S3_bucket_schematic.png)
- REST APIs: Representational State Transfer (REST) APIs are programming interfaces commonly used to interact with files in Amazon S3. 
### Data warehouses (Redshift)
- A central repository of structured data from many data sources. 
- Data here is transformed, aggregated, and prepared for business reporting and analysis.
- Data is stored within the data warehouse using a schema. A schema defines how data is stored within tables, columns, and rows.

### Amazon EMR 
- the AWS service that implements Hadoop frameworks.
- two file systems: Hadoop Distributed File System (HDFS) and Elastic MapReduce File System (EMRFS)

## Processing
- Batch processing: scheduled (hourly, daily, weekly, etc.) and periodic (irregular, certain amount of data collected)
  - Batch: Velocity is very predictable with batch processing. It amounts to large bursts of data transfer at scheduled intervals.
  - Periodic: Velocity is less predictable with periodic processing. The loss of scheduled events can put a strain on systems and must be considered.
- Stream processing: near real-time (within minute) and real-time (within miliseconds)
  - Near real-time: Velocity is a huge concern with near real-time processing. These systems require data to be processed within minutes of the initial collection of the data. This can put tremendous strain on the processing and analytics systems involved.
  - Real-time: Velocity is the paramount concern for real-time processing systems. Information cannot take minutes to process. It must be processed in seconds to be valid and maintain its usefulness.
- Data acceleration (bursts, rate at which large collections of data can be ingested, processed, and analyzed)

|  | Batch data processing | Stream data processing |
| :---: | :---: | :---: |
| Data scope | Queries or processing over all or most of the data in the dataset | Queries or processing over data within a rolling time window, or on just the most recent data record |
| Data size | Large batches of data | Individual records or micro batches consisting of a few records |
| Latency | Minutes to hours | Seconds or milliseconds |
| Analysis | Complex analytics | Simple response functions, aggregates, and rolling metrics |

#### Common framework for data collection
- Hadoop, running in Amazon EMR, configures a cluster of EC2 instances to serve as a single distributed storage and processing solution
- Apache Spark, uses in-memory caching and optimized execution for faster performance, avoids writing data to storage, preferring to keep the data in memory at all times.

### Batch processing architecture
- Amazon S3: Amazon Simple Storage Service is an object storage service that offers industry-leading scalability, data availability, security, and performance. 
- AWS Lambda: run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running. 
- Amazon EMR: provides a managed Hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances. 
- AWS Glue: a fully managed extract, transform, and load (ETL) service that makes it easy for you to prepare and load your data for analytics. 
- Amazon Redshift: a fast, scalable data warehouse that makes it simple and cost-effective to analyze all your data across your data warehouse and data lake. 
- ![Batch processing architecture 1](https://github.com/er1czz/tech_notes/blob/main/batch_processing_architecture1.png)
- <p align="center"><b>Batch processing architecture 1</b></p>
- ![Batch processing architecture 2](https://github.com/er1czz/tech_notes/blob/main/batch_processing_architecture2.png)
- <p align="center"><b>Batch processing architecture 2</b></p>

### Stream processing
- ![Benefits of stream processing](https://github.com/er1czz/tech_notes/blob/main/benefits_of_stream_processing.png)
- <p align="center"><b>Benefits of stream processing</b></p>
##### Amazon Kinesis key functions:
 - to ingest the constant stream of data
 - to process and analyze the stream
 - to load the data into an analytical data store
##### Amazon Kinesis key components:
 - Amazon Kinesis Data Firehose: to capture, transform, and load data streams into AWS data stores for near real-time analytics with existing business intelligence tools
 - Amazon Kinesis Data Stream: to build custom, real-time applications that process data streams using popular stream processing frameworks. 
 - Amazon Kinesis Video Stream: to securely stream video from connected devices to AWS for analytics, machine learning (ML), and other processing.
 - Amazon Kinesis Data Analytics: to process data streams in real time with SQL or Java without having to learn new programming languages or processing frameworks.
#### Combined processing architecture
- ![Combined processing architecture](https://github.com/er1czz/tech_notes/blob/main/combined_processing_architecture.png)
- <p align="center"><b>Combined processing architecture</b></p>

## Data variety
- Key concepts
  - schema: a relational data model that defines and standardizes data elements and their relation to one another.
  - structured data: in a tabular format, often within a database management system (DBMS). (e.g. Amazon RDS, Amazon Aurora, MySQL, MariaDB, PostgreSQL, Microsoft SQL Server, and Oracle)
  - semi-structured data: stored in the form of elements within a file. This data is organized based on elements and the attributes that define them. It doesn't conform to data models or schemas. (e.g. CSV, XML, JSON, Amazon DynamoDB, Amazon Neptune, and Amazon ElastiCache)
  - unstructured data: stored in the form of files. This data doesn't conform to a predefined data model and isn't organized in a predefined manner. Unstructured data can be text-heavy, photographs, audio recordings, or even videos. (e.g. emails, photos, videos, clickstream data, Amazon S3, and Amazon Redshift Spectrum)
### Types of information systems
- Online transaction processing (OLTP): often called operational databases, logically organize data into tables with the primary focus being on the speed of data entry. 
- Online analytical processing (OLAP): often called data warehouses, logically organize data into tables with the primary focus being the speed of data retrieval through queries. 
- "*In practice, data is written to the OLTP database with a very high frequency. Records from that system are copied over to an OLAP system on a scheduled basis.*" 
- **Comparing OLTP and OLAP**

| Characteristic | OLTP | OLAP |
| :---: | :---: | :---: |
| Nature | Constant transactions (queries/updates) | Periodic large updates, complex queries |
| Type | Operational data | Consolidated data |
| Examples| Accounting database, online retail transactions | Reporting, decision support |
| Data retention | Short-term (2-6 months) | Long-term (2-5 years) |
| Storage| Gigabytes (GB) | Terabytes (TB)/petabytes (PB)  |
| User | Many | Few |
| Protection | Robust, constant data protection and fault tolerance | Periodic protection |

### Row-based indexing & columnar data indexing
- Both OLTP and OLAP systems can use either indexing method
- Row-based index: row by row storage, best at random reads and writes, returning full rows of data based on a key
- Columnar data index: column by column storage, best at sequential reads and writes, returning aggregations of column values

### Non-relational database: semistructured & unstructured data
- NoSQL: a common semi-structured database, quick data retrieval and data purge
  - Key-value table vs relational table
  - Amazon DyanamoDB
  - Graph database: store any types of data
    - Amazon Neptune
#### Schema changes in a relational database: 
The needs of the business have changed. You need to add a new column to track each product's rating. Not all products have a rating yet, so you need to allow the column to accept NULL values.
- To add a new column to the table, you must:
  - 1 Execute a SQL command to add the column.
  - 2 The table now contains an empty column.
  - 3 Populate the new column with a value for each existing record.
#### Schema changes in non-relational database:
- When the same requirement is placed on data in a non-relational database, the remedy is quite different. You simply add the data for that record.
- With a non-relational database, each record can have its own set of attributes. This flexibility is one of the greatest benefits of non-relational databases.
#### Graph databases
Graph databases are purpose-built to store any type of data: structured, semistructured, or unstructured. The purpose for organization in a graph database is to navigate relationships.
#### relational vs non-relational databases
- ![relational vs non-relational databases]([relational_vs_non-relational_db.png](https://github.com/er1czz/tech_notes/blob/main/relational_vs_non-relational_db.png)

## Data veracity: the degree to which data is accurate, precise, and trusted.
- Curation: the action or process of selecting, organizing, and looking after the items in a collection.
- Data veracity is contingent on the integrity of the data.
- Data integrity is the maintenance and assurance of the accuracy and consistency of data over its entire lifecycle.
  - Data cleansing: the process of detecting and correcting corruptions within data.
  - Referential integrity: the process of ensuring that the constraints of table relationships are enforced.
  - Domain integrity: the process of ensuring that the data being entered into a field matches the data type defined for that field..
  - Entity integrity: the process of ensuring that the values stored within a field match the constraints defined for that field.

### Data schema: the set of metadata used by the database to organize data objects and enforce integrity constraints. 
- logical schema: focus on the constraints to be applied to the data within the database.
  - This includes the organization of tables, views, and integrity checks.
- physical schema: focus on the actual storage of data on disk or in a cloud repository. 
  - These schemas include details on the files, indices, partitioned tables, clusters, and more.
- Information schema: a database of metadata that houses information on the data objects within a database.
  - Microsoft SQL Server calls its information schema the master database. 
  - Oracle uses data dictionary tables and a metadata registry. 
  - Apache Hadoop uses a metastore. 
  - Each DBMS may have different names for the data structure that houses the metadata, but the purpose is the same: **to define what all of the objects within the database are and record vital information about them.**
 
### ACID
- ACID: Atomicity, Consistency, Isolation, and Durability. It is a method for maintaining consistency and integrity in a structured database.
  - e.g. Amazon RDS (return the most recent consistent version of all data)
  - ACID is the long-standing bastion of relational data integrity. ACID-compliant database
    - Atomicity: ensures your transactions either completely succeed or completely fail
    - Consistency: ensures all transactions provide valid data to the database.
    - Isolation: ensures one transaction cannot interfere with another concurrent transaction.
    - Durability: ensures the result of the transaction is permanent even in the event of a system failure. (making sure your changes actually stick)
### BASE consistency: commonly in NoSQL
- **B**asically **A**vailable **S**oft state **E**ventually consistent
- consistency and integrity in a structured or semistructured database.
  - Basically Available: allows for one instance to receive a change request and make that change available immediately.
  - Soft state: changeable state,  partial consistency across distributed instances.
    - ACID: hard state, because users cannot access data that is not fully consistent.
  - Eventual consistency: a change will eventually be made to every copy
#### ACID vs BASE compliance
| ACID compliance | BASE compliance |
| :---: | :---: |
| Strong consistency | Weak consistency – stale data is OK |
| Isolation is key | Availability is key|
| Focus on committed results | Best effort results |
| Conservative (pessimistic) availability | Aggressive (optimistic) availability |

### ETL: Extract, Transform, Load
- process of collecting data from raw data sources and transforming that data into a common type
- Transforming one data source type into a different storage format:  relational, non-relational, and file-based destination formats.
  - Amazon EMR: hands-on approach to creating your data pipeline. 
  - AWS Glue: a serverless, managed ETL tool that provides a much more streamlined experience than Amazon EMR.
  - Use Amazon EMR for the more intensive operations and workloads, and use AWS Glue for the workloads that require more flexibility and mobility within your pipeline.

## Data analytics
- Two classification: informaiton analytics & operational analytics
  - Information analytics: the process of analyzing information to find the value contained within, 
    - It is often synonymous with data analytics.
  - Operational analytics: similar, focuses on the digital operations of an organization.
- Five types of analysis: descriptive, diagnostic, predictive, prescriptive, and cognitive.
  - Descriptive analysis, often called data mining.
  - Predictive analytics, 3 key layers: Application services, Platform services, Frameworks and interfaces (ML practice)
  - Cognitive analytics, highly specialized recommendations to businesses without any human involvement
  - ![5 types of data analytics](https://github.com/er1czz/tech_notes/blob/main/5types_data_analytics.png)
  - <b>Different type of data analytics based on the input of human judgement</b>
- Analytic services by velocity: batch, interactive, and stream
  - batch analytics: querying large amounts of “cold” data. (e.g. Amazon EMR)
  - interactive analytics: running complex queries across complex data sets at high speeds (e.g. Amazon Elasticsearch Service <ES>, Amazon Athena, Amazon Redshift), scheduled report deliveries.
  - stream analytics: requires ingesting a sequence of data and incrementally updating metrics, reports, and summary statistics in response to each arriving data record. This method is best suited for real-time monitoring and response functions. (e.g. Amazon Kinessi and AWS Lambda)
### Data analytics solutions by AWS
- Ingest/collect: in large batches or in a stream process (Amazon EMR, AWS Glue, Amazon Kinesis)
- Store: storing objects or storing records in a database or data warehouse. (Amazon S3, Amazon RDS, Amazon DynamoDB, Amazon Redshift)
- Process/analyze: an iterative process. (Amazon ML, Amazon EMR, AWS Glue, Amazon Kinesis Data Analytics, Amazon Athena)
- Consume/visualize (Amazon Redshift, Amazon Quicksight, Amazon Athena)

### "Data analysis isn't really about data and charts. It's about finding and telling a story." - Glen Rabbie, CEO Yellowfin
 
### Data Visualization
#### Data preparation
  - Inspecting data, Cleansing data, Transforming data, Visualizing data
#### Data reporting
  - static report, interactive report, dashboard
#### Best practice of writing reports
  - Gather the data, facts, action items, and conclusions.
  - Identify the audience, expectations they have, and the proper method of delivery.
  - Identify the visualization styles and report style that will best fit the needs of the audience.
    - Best practice number 1: The top-left corner of each page of your report is the primary focal point for report consumers. This is where dominant visuals should go.
    - Best practice number 2: Locate navigational elements, filters, and similar items at the edges of report page. This will ensure report consumers can find the elements they need without learning a new navigational style.
  - Create the reports and dashboards.
    - Remember that these reports and dashboards will be somewhat fluid. They change as the data evolves.
