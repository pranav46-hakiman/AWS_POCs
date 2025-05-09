Simple Storage Service [S3]:
----------------------------

Task1: Creating a bucket:
------------------------
1. Log in to the AWS Console and navigate to S3.

2. Click on create bucket.

3. Create the Source Bucket:

-Bucket name: 

-Region: 

-Object Ownership: default

-Block Public Access settings: disabled for now

-Bucket Versioning: disabled for now

-Encryption: Leave default

4. Click Create bucket.

5. Upload a Sample Video

-Click Upload, then Add files, and select sample-video from your local machine.

-Click Upload to complete the upload.
   

Task2: Configure S3 bucket policy:
---------------------------------
1. Create the StreamVibeUploader IAM Role:

2. Navigate to IAM using the search bar.

3. Click Roles in the left sidebar, then Create role.

4. Select type of trusted entity: Choose AWS service > S3.

5. Click Next: Permissions, skip attaching permissions, and click Next: Tags.

6. Role name: Enter StreamVibeUploader.

7. Click Create role.

8. Click on StreamVideoUploader in the Roles list.

***Note the Role ARN (e.g., arn:aws:iam::116981810703:role/StreamVibeUploader).

9. Go to the Permissions tab, click Add inline policy, and select the JSON tab.

paste this:

{

  "Version": "2012-10-17",

  "Statement": [
  
    {
    
      "Effect": "Allow",
      
      "Action": ["s3:PutObject", "s3:PutObjectAcl"],
      
      "Resource": "arn:aws:s3:::source-bucket-116981810703/videos/*"
    
    }
  
  ]

}

10. Click Review policy, name it S3UploadPolicy, and click Create policy.

11. Apply a Bucket Policy:

-Go back to S3, click on source-bucket-116981810703.

-Go to the Permissions tab.

-Under Block public access (bucket settings), click Edit.

-Uncheck Block all public access and all sub-options.

-Click Save changes, type confirm, and click Confirm.

-Scroll to Bucket policy, click Edit.

12. Test the policy

Task3: Enabling S3 versioning:
-----------------------------
1. In S3, click on source-bucket.

2. Go to the Properties tab.

3. Scroll to Bucket Versioning, click Edit.

4. Select Enable, then click Save changes.

Task4: Setting up S3 replication:
--------------------------------
1. Create a Destination bucket- follow Task1 steps.

2. Create an IAM role for replication - Follow Task2 steps but you need to choose following/edit it:
Destination:[  "s3:PutObject",

   "s3:PutObjectAcl",

   "s3:ReplicateObject",

   "s3:ReplicateTags" ]

Source:[ "s3:GetObject",
        
        "s3:GetObjectVersion",
        
        "s3:ReplicateObject",
        
        "s3:ReplicateTags"]

3. Configure Replication:

-Go to S3, click on source-bucket-116981810703.

-Go to the Management tab.

-Under Replication rules, click Create replication rule.

-Rule name: Enter VideoReplicationToEU.

-Status: Select Enabled.

-Source bucket: Leave as source-bucket-116981810703.

-Choose a source: Select Apply to all objects in the bucket.

-Destination bucket: Select destination-bucket-116981810703.

-IAM role: Select S3ReplicationRole.

-Click Save.

4. Test Replication:

-Go to the videos folder in source.

-Upload a new file (e.g., new-video.mp4).

-Switch to eu-west-1 in the console, go to destination, and confirm the file is replicated in the videos folder
