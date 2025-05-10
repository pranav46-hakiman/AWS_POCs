RDS and Dynamo DB:
-----------------
Task1: RDS:
----------
1. AWS MGMT Console > RDS > Databases.

2. Click on create database.

3. Enter the followings:

-Method: Standard create”

-Engine type: “MySQL”.

-Choose “Free Tier” (db.t2.micro).

-DB identifier: my-rds-db.

-Master username

-Give a passwd and confirm it

-Enable “Publicly accessible”

-use default VPC/security group.

4. Click “Create database”

5. Connect:

-Open cmd prompt in windows as administrator.

-Use a MySQL Client or CLI: 

-mysql -h my-rds-db.xxxx.rds.amazonaws.com -u admin -p

-Enter the password

6. Create a table and insert some values to it.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task2: DynamoDB:
---------------
1. AWS MGMT Console > Dynamo DB

2. Create a table

3. Add items to it.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

