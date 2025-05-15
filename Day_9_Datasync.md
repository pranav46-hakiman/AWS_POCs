Move files from one S3 bucket to another S3 bucket:
---------------------------------------------------

Task1: Create a source S3 bucket and uplaod some files to it:
------------------------------------------------------------
1.Log in to the AWS Console and navigate to S3.

2.Click on create bucket.

3.Create the Source Bucket:

-Bucket name:

-Region:

-Object Ownership: default

-Block Public Access settings: disabled for now

-Bucket Versioning: disabled for now

-Encryption: Leave default

4.Click Create bucket.

5.Upload a Sample files

-Click Upload, then Add files, and select sample-files from your local machine.

-Click Upload to complete the upload.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task2: Create a destination bucket:
----------------------------------
1.Log in to the AWS Console and navigate to S3.

2.Click on create bucket.

3.Create the Source Bucket:

-Bucket name:

-Region:

-Object Ownership: default

-Block Public Access settings: disabled for now

-Bucket Versioning: disabled for now

-Encryption: Leave default

4.Click Create bucket.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task3:Set Up AWS DataSync:
---------------------------
AWS > Datasync

1.Click Create location → choose Amazon S3 as source.

2.Select your source S3 bucket.

3.Choose IAM role (create one if not already existing).

4.Click Create location again → choose Amazon S3 as destination.

5.Select your destination S3 bucket.

6.Use a similar or different IAM role as needed.

7.Click on create.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task4: Create a DataSync Task:
-----------------------------
1.Click Create Task.

2.Choose the source and destination locations you just set up.

3.Name the task (e.g., MoveS3FilesTask).

4.Leave other options default unless you have specific needs (e.g., delete after transfer).
