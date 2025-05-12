
Task: Push the Docker Image to AWS ECR:
--------------------------------------

1.1 Create an ECR Repository:
---------------------------
1.Go to the AWS Management Console > Elastic Container Registry (ECR).

2.Click Create repository.

3.Name it my-react-app, set it to Private, and create it.

1.2 Authenticate Docker to ECR:
------------------------------
1.In your terminal, authenticate Docker to your ECR registry by following cmd: aws ecr get-login-password --region <your-region> | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.<region>.amazonaws.com

2.If successful, you’ll see: Login Succeeded.

1.3 Tag and Push the Image:
--------------------------
1.Tag your local image for ECR: docker tag my-react-app:latest <aws_account_id>.dkr.ecr.<region>.amazonaws.com/my-react-app:latest

2.Push the image to ECR: docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/my-react-app:latest



