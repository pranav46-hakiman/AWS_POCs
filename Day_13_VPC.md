Task1: Create a VPC: Virtual Private Cloud:
------------------------------------------
1. Go to VPC in AWS Console and click on create VPC,

2. Configure the VPC:

   - Name:
  
   - IPv4 CIDR
  
   - No. of AZs:
  
   - Public subnets
  
   - Private subnets
  
   - NAT GW:
  
3. Click on create.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task2: Create a Security Group:
------------------------------
1. Go to SG and click on create.

2. Configure SG:

    - Name:
  
    - Description:
  
    - VPC:

3. Inbound rules

4. Click on create.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task3: Launchan EC2 with VPC Public IP:
---------------------------------------
1. Create a EC2 instance

2. Select the previously created VPC and a public or a private subnet based on your need.

3. Also the already created SG,

   
      - 
