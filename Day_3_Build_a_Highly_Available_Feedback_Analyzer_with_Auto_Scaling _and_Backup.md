Build a Highly Available Feedback Analyzer with Auto Scaling and Backup:
-----------------------------------------------------------------------

Task1. Launch an EC2 Instance and Transfer Feedback App:
---------------------------------------------------------------
Refer Day2

Task2: Configure a Security Group and Attach and Configure EBS Volume:
----------------------------------------------------------------------

1.EC2 > Security Groups > Create Security Group.

2.Name it, allow Inbound(HTTP,SSH,Custom) and Outbound all traffic.

3.Attach this security group to your EC2 instance

4.Test access to the app (http://<public-ip>) and SSH.

Task3: Attach and Config EBS Volume:
---------------------------------
1.EC2 > Volumes, create a new EBS volume (e.g., 10 GB, gp3 type) in the same Availability Zone as your EC2 instance.

2.Attach the volume to your EC2 instance.

3.SSH into the instance and format/mount the volume.

cmds: 

lsblk 

sudo mkfs.ext4 /dev/xvdf

sudo mkdir /data

sudo mount /dev/xvdf /data

5.Update /etc/fstab to auto-mount on reboot: echo '/dev/xvdf /data ext4 defaults,nofail 0 2' | sudo tee -a /etc/fstab

6.Move your feedback app’s data (e.g., database files or user uploads) to /data

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task4: Create an EBS Snapshot:
-----------------------------
1.In EC2 > Volumes, select your EBS volume.

2.Choose Actions > Create Snapshot.

3.Add a description (e.g., FeedbackAppDataBackup).

4.Verify the snapshot in EC2 > Snapshots.

5.If needed(Optional) Test recovery by creating a new volume from the snapshot and attaching it to another EC2 instance.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task5: Create an AMI:
--------------------
1.In EC2 > Instances, select your instance.

2.Choose Actions > Image and Templates > Create Image.

3.Name the AMI (e.g., FeedbackAppAMI) and include the EBS volume.

4.Wait for the AMI to be available in EC2 > AMIs.

5.Testing: Launch a new EC2 instance from the AMI to verify it works.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task6: Set up an Application Load balancer [ALB]:
------------------------------------------------
1. Go to EC2 > Load Balancers > Create Load Balancer > Application Load Balancer.

2. Name it FeedbackAppALB and configure:

   Scheme: Internet-facing.

   Listeners: HTTP (port 80).

   VPC: Default VPC, select at least two Availability Zones.

4. Create a new Target Group (e.g., FeedbackAppTG) with:

-Protocol: HTTP.

-Health check: Path / (or your app’s health endpoint).

4.Register your EC2 instance in the target group.

5.Create a new security group for the ALB (ALBSG):

-Allow HTTP (port 80) from 0.0.0.0/0.

-Attach to the ALB.

6.Update the EC2 instance’s security group (FeedbackAppSG) to allow HTTP (port 80) only from the ALB’s security group.

***Testing: ALB by accessing its DNS name (e.g., http://<alb-dns-name>).

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task7: Configure an Auto Scaling Group (ASG):
---------------------------------------------
1.Go to EC2 > Auto Scaling Groups > Create Auto Scaling Group.

2.Name it FeedbackAppASG and use a Launch Template

-Create a launch template using your custom AMI (FeedbackAppAMI).

-Specify the instance type (t2.micro), key pair, and security group (FeedbackAppSG).

3.Configure the ASG:

-VPC: Default VPC, select the same subnets as the ALB.

-Attach the ASG to the ALB’s target group (FeedbackAppTG).

-Set desired capacity: 2, minimum: 1, maximum: 4.

4.Add a scaling policy:

-Choose Target Tracking Scaling Policy.

-Metric: Average CPU utilization, target: 50%.

5.Verify that two EC2 instances are launched and registered with the ALB.

***Test the ALB DNS name to ensure traffic is distributed across instances.

****Deliverable: ASG configured to scale your app based on demand.
