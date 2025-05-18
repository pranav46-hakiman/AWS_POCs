Task1: Set Up Security Groups:
-----------------------------
1.Go to VPC > Security Groups > Create security group.

2.Name:

3.Description: Security group for Aurora.

4.VPC: RetailPoC-VPC.

5.Inbound rules: Add rule:

-Type: PostgreSQL (5432).

S-ource: Custom, select RetailPoC-LambdaSG (create later).

7.Outbound rules: Default (all traffic allowed).

8.Click Create.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task2: Set Up Aurora PostgreSQL:
-------------------------------
Step 1:Create DB Subnet Group:
-----------------------------
1.Go to RDS console > Subnet groups > Create DB subnet group.

2.Name

3.Description: Subnet group for Aurora.

4.VPC: RetailPoC-VPC.

-Add subnets: PrivateSubnetA, PrivateSubnetB.

5.Click Create.

Step 2:Create Aurora Cluster:
-----------------------------
1.Go to RDS > Databases > Create database.

2.Choose:

-Engine: Amazon Aurora.

-Edition: Aurora PostgreSQL.

-Capacity type: Serverless.

3.Settings:

-DB cluster identifier: retailpoc-cluster.

-Master username: admin.

-Master password: RetailPoC123! (min 8 characters, note this down).


-DB instance size: Serverless.

-VPC settings:

-VPC: RetailPoC-VPC.

-Subnet group: retailpoc-dbsg.

-Security group: RetailPoC-AuroraSG.

-Database options:

-Initial database name: retaildb.

-Serverless settings:

-Min capacity: 2 ACUs.

-Max capacity: 16 ACUs.

-Auto-pause: Enable, pause after 5 minutes.

-Additional configuration:

-Enable encryption (default).

-Disable public access.

3.Click Create database (takes ~10-15 minutes).

Note the cluster endpoint (e.g., retailpoc-cluster.cluster-xxx.us-east-1.rds.amazonaws.com).

Task3: Set Up Bastion Host for Database Access:
----------------------------------------------
1.Go to EC2 console > Instances > Launch instances.

2.Name: RetailPoC-Bastion.

3.AMI: Amazon Linux 2 (Free Tier eligible).

4.Instance type: t2.micro.

5.Key pair: Create or select an existing key pair (save .pem file).

6.Network:

-VPC: RetailPoC-VPC.

-Subnet: PublicSubnetA.

-Auto-assign public IP: Enable.

7.Security group: Create new:

-Name: RetailPoC-BastionSG.

-Rule: SSH (port 22) from your IP (e.g., 203.0.113.0/32).

8.Launch instance.

9.Connect via SSH

10.Install PostgreSQL client

11.Connect to Aurora DB

12.Create tables

13.Remove bastion access

