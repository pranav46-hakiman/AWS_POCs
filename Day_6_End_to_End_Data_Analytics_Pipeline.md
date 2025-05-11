End-to-End Data Analytics Pipeline on AWS:
-----------------------------------------

Task1: Set Up the Data Source (Streaming Data):
-----------------------------------------------
1.1 Create a Kinesis Data Stream:
---------------------------------
1.Log in to the AWS Management Console.

2.Navigate to Amazon Kinesis (search for "Kinesis" in the AWS console).

3.Click Create data stream.

4.Set the following:

-Data stream name: EcommerceStream

-Number of open shards: 1 (for simplicity; each shard supports 1 MB/s ingress and 2 MB/s egress).

-Capacity mode: Select On-demand (for simplicity; auto-scales based on traffic).

5.Click Create data stream.

1.2 Generate Mock Data:
----------------------
1.Prepare a Python script

2.Install Boto3 (AWS SDK for Python) locally

3.Configure AWS CLI credentials

4.Save the script as send_kinesis_data.py and run it

5.Verify data ingestion

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Task2: Process Streaming Data:
------------------------------
2.1 Create an IAM Role for Lambda:
-----------------------------------

1.Navigate to IAM in the AWS console.

2.Click Roles > Create role.

3.Select:

-Trusted entity type: AWS service

-Use case: Lambda

4.lick Next.

5.Attach the following policies:

-AWSLambdaBasicExecutionRole (for CloudWatch logging)

-AmazonKinesisReadOnlyAccess (to read from Kinesis)

-AmazonS3FullAccess (to write to S3; we’ll refine permissions later)

-Click Next.

-Set:

-Role name: LambdaEcommerceProcessorRole

6.Click Create role.

2.2 Create a Lambda Function:
-----------------------------

1.Navigate to AWS Lambda in the AWS console.

2.Click Create function.

3.Set:

-Function name: ProcessEcommerceEvents

-Runtime: Python 3.9 (or latest available)

-Execution role: Select Use an existing role and choose LambdaEcommerceProcessorRole.

4.Click Create function.

5.Write lambda code

2.3 Add Kinesis Trigger:
-------------------------
1.In the Lambda function console, click Add trigger.

2.Select Kinesis.

3.Set:

-Kinesis stream: EcommerceStream

-Batch size: 100

-Starting position: Latest

4.Click Add.

5.test the lambda function

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Task3: Store Data in a Data Lake:
--------------------------------
3.1 Create an S3 Bucket

3.2 Update Lambda IAM Permissions

3.3 Verify Data in S3 - run the pyhton script from step 1.2

3.4 Set Up AWS Glue Crawler:
----------------------------
1.Navigate to AWS Glue in the AWS console.

2.Click Crawlers > Create crawler.

3.Set:

-Crawler name: EcommerceProcessedCrawler

4.Click Next.

5.Data source:

-Add data source:

-Select S3.

-Include path: s3://ecommerce-data-lake-<yourname>/processed/

5.Click Next.

6.Database:

7.Click Create database.

-Name: ecommerce_analytics_db

-Click Create.

-Select ecommerce_analytics_db for the crawler.

-Click Next.

8.IAM Role:

-Create a new IAM role:

-Click Create an IAM role.

-Name: GlueEcommerceCrawlerRole

-Attach policies: AWSGlueServiceRole, AmazonS3ReadOnlyAccess.

10.Select GlueEcommerceCrawlerRole.

-Click Next.

11.Output and scheduling:

-Output database: ecommerce_analytics_db

-Table prefix: Leave blank. 

12.Click Next.

13.Review the crawler settings and click Create crawler.

14.Run the crawler

3.5 Validate Data Catalog:

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Task4: Query the Data:
---------------------
4.1 Configure Athena:
---------------------
1.Navigate to Amazon Athena in the AWS console.

2.If prompted, set up a query result location:

3.Click Settings (gear icon).

-Set Query result location: s3://ecommerce-data-lake-<yourname>/athena-results/.

-Click Save.

4.Select the database:

-In the Data source dropdown, choose AwsDataCatalog.

-In the Database dropdown, select ecommerce_analytics_db.

-Verify the table (processed) appears in the Tables section.

4.2 Write and Run Queries:
