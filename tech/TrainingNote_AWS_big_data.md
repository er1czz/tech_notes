# Big Data On AWS Training

Class slides and lab guide
- https://evantage.gilmoreglobal.com/
- Version 3.9.13 for student guide and lab guide

Lab (with time limit, 3 trials, )
- https://aws.qwiklabs.com/

recommended prerequisite
- https://www.aws.training/Details/eLearning?id=35364
- Data Analytics Fundamentals (free, 3.5 hrs)

ML Amazon SageMaker Training
- https://aws.amazon.com/training/classroom/the-machine-learning-pipeline-on-aws/

Training certificate
- https://www.aws.training/Transcript/CompletionCertificateHtml?transcriptid=iqpahq6gQku8a2W7BsFjJQ2

### Note: 
- The training content partially covered the content of "AWS Certified Data Analytics"
- AWS certificate reflects the working experience of examinees. The less experience, the harder/longer the exam prep.
- Lab: 
  - start lab in https://aws.qwiklabs.com/ then go to AWS
  - to end lab, **first** sign out AWS, **then** click **END lab**.

## Module 1:
AWS EB (Elastic Beanstalk) 
- (latest) https://www.youtube.com/watch?v=uiM1xzOX8Qg
- (old version) https://www.youtube.com/watch?v=SrwxAScdyT0

## Module 2:
Data ingestion:
- Transactional (Amazon Dynamo DB, Amazon RDS), expensive
- Stream (Amazon Kinesis), moderate
- File (Amazon S3), cheap
Hadoop uses S3DistCp in headnode
datasink
Apache Sqoop - transfer data from HDFS to relational (RDS) and back to HDFS (bi-directional, map-only job)
Data Transfer
- VPN connections are restricted to communicate VPC (Amazon RDS, Amazon Redshift, Amazon EMR)
Amazon Kinesis Agent (or Flume agent)

## Module 3: real time data ingestion
Incoming data
- **Stream processing**: continuous data, low latency (real-time: ms to s / near-real-time: 10 s to min)
- Batch processing: finite data

Windowsing data 
Amazon Kinesis Data Firehose (API, mins latency)

- Amazon Kinesis Stream (Real time latency)
- Amazon Kinesis Firehose (near real-time latency: min)
- Streaming Data Analytics (SQL on stream, real-time, high scalability) - KPU kinesis processing unit (1 vCPU + 4 GB memory)
- sub-second processing
- Snowplot analytics

## Module 4: Data storage solutions
Data Lake 
  - Schema on read (not predefined)
  -  Structured / semi-structured/ unstructured data
  -  tool flexibility
  -  data of low level of granularity

Data Wareouse 
  - Schema on write (predefined)
  - Structured data only
  - SQL compatible only
  - Summary / aggregated level of detail
S3 Glacier
  - Extremely low cost
  -  Glacier Standard
      -  standard (3-5 hrs, 250 GB)
      -  expediated (1-5 mins, 250 GB)
      -  bulk (up to 7 hrs)
  - Glacier DA (Deep Archive)
      -  standard (12-24 hrs)
      -  bulk (up to 48 hrs)
 
ACID transactions [(atomicity, consistency, isolation, durability)](https://en.wikipedia.org/wiki/ACID)
  - ACID transactions ensure the highest possible data reliability and integrity. They ensure that your data never falls into an inconsistent state because of an operation that only partially completes. 
Availability Zone (AZ): data center
Amazon Neptune (Graph database)

In-Memory Key-Value Store: Amazon ElastiCache (high performance)
  - Memcached
  - Redis 

Amazon Redshift
  - Based on postgres

Amazon RDS (relational database service)

HDFS: local disk, not on S3.
  
Choosing data storage solution (ElastiCache, DAX, DynamoDB, RDS (Aurora), ES, S3, S3 Glacier)
  - data structure
  - access pattern
  - data/access characteristics (request rate)
  - cost effetive https://calculator.aws/
 
## Module 5 Big Data Processing and Analytics
Type: batch, interactive analytics, message, stream queries, machine learning

Athena: interactive SQL query directly on S3
  - Athena ad hoc queries
  - Redshift for historical analysis (either Redshift spectrum or copy data, act as Athena)
  - EMR for ETL and analytics
  - QuickSight for visualization

DDL (data definition language) written in Hive

https://aws.amazon.com/blogs/big-data/analyzing-data-in-s3-using-amazon-athena/
1. S3 to infer the schema of raw data
2. rescan data as paquet (compressed, partition, columnar)
3. Athena query ready

## Lab 3 
UNIXTIME (epoch)
https://www.epochconverter.com/

## Module 7: Use EMR
#### Note: don't use AWS console for EMR production. 
  - Transient clusters
  - Long-running clusters
  - Master node = leader node

## Module 10: Apache Spark on Amazon EMR
  - Spark vs MapReduce
  - Yarn controls the Spark master (master node)
  - Benefit of Spark on EMR
      -   Ease of use
      -   Container service
      -   Cost
      -   Integration with AWS
      -   CouldWatch (metrics monitoring)

## AWS Glue to Automate ETL Workloads
- AWS Data Pipeline (just move data, orchestration only)
- Glue (ETL, data prep, operational, only Scala or Python jobs)
  - Serverless ETL: (No server management, flexible, no idle, availability)
    - Data Catalog: persistent metadata store (compatible with Hive Metastore)
    - Data Catalog Crawlers: automatic, ad hoc or on schedule, serverless
      -  Automatic Schema Inference (always schemea)
- [AWS step function, a visual workflow service](https://aws.amazon.com/step-functions/?step-functions.sort-by=item.additionalFields.postDateTime&step-functions.sort-order=desc)
- Development Endpoints (Sandbox)
- Job Bookmark Options: pick up where you left off 
- [dedup](https://aws.amazon.com/about-aws/whats-new/2019/08/aws-glue-provides-findmatches-ml-transform-to-deduplicate/)

Amazon Redshift: Relational Data Warehouse (different from db)
  - Exabyte scale
  - Redshift Spectrum
Athena: in memory platform (smaller query, only able to scan low PB, 5K/PB)
Redshift (RS) - > Redshift Spectrum (RSS): to exabyte

ETL pricing (situational)
- glue: moderate
- EMR: large dataset or longer task maybe
- Lambda: most cost effetive for small task (15 mins max running time)

Hadoop Distributed File System ( HDFS )

Amazon Redshift Architecture: leader node, compute notes
  - dc1, dc2, rd3
  - TLS 1.2 best practice

## Module 13: Securing Your Amazon Deployments
- Shared responsibility model
- AWS is essentially EC2 based
- IAM role for each EC2 instance
- MFA
- Server-side encryption (Master key)
- AWS KMS (encryption, $ service)
- Rest in HDFS
- Kinesis security (API only viable through ssl, sequence number, partition key, data blob)
  - use temporary security credentials (IAM roles) instead of long-term access keys
- DynamoDB is no longer compliant with HIPPA, etc.
- Redshift (AES-256), 5 GB / 4 hr, network isolated, VPC, Security Groups
- Security Hub (multi-account support)
- Monitoring and logging (SNS for notification and S3 for log storage)

## Model 14: Managing Big Data Costs
- On demand + Reserved + Spot
- EC2 foundation of AWS (80% used + 20% spare: 2 minutes termination window)
- Off-hour script
- Resevration 1) no upfront 2) partial upfront 3) full upfront
- Spot 
  - Spot fleet for large quantity of spot instances
  - Spot block (flat rate, up to six hours)
Blended approach
Storage and Transfer costs: S3 vary by region. Same region transfer is free.
Amazon Redshift: no upfront cost (on-demand node pricing, reserved node pricing)
- Dense storage (DS) nodes End of life
- Dense compute (DC) nodes (5 nodes)
- RA3 - NVME 

## Model 15: Visualizing and Ochestrating Big Data
Amazon QuickSight - SPICE
  - Dashboard (landscape)
  - Storyboard (portrait)
 
Tableau, Spotfire, Jaspersoft (AWS marketplace).
