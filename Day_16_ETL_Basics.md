Glue ETL Basics - Run a Glue job to convert CSV data to Parquet and store it in another S3 bucket:
--------------------------------------------------------------------------------------------------

Task1: Set up S3 buckets:
------------------------
1. Source

2. Destination


Task2: Create an IAM role for Glue:
----------------------------------
1.Go to IAM in the AWS Console.

2.Click on create new role.

Task3: Create a Glue Crawler to catalog CSV data:
-------------------------------------------------
1.Navigate to AWS Glue in the AWS Console.

2.Go to Crawlers > Create Crawler.

3.Crawler Info:

- Name: csv-crawler

- Data Source

- IAM role

- Output DB

- Schedule

4. Run the crawler.

Task4: Glue ETL Jobs:
--------------------
1.In AWS Glue, go to Jobs > Add job

2.Job Details:

-Name: csv-to-parquet-job

-IAM Role: AWSGlueETLRole

-Type: Spark

-Glue version: Glue 4.0 (or latest stable version).

-Language: Python

3. Write the script in script editor.

4. Run the Glue Job.

