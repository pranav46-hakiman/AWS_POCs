Elastic Compute CLoud: EC2:
---------------------------

Launching an EC2 instance using Amazon Linux:
---------------------------------------------

Step 1: AWS MGMT Console > EC2 > Instance

Step 2: Enter the following details:

    a. Nmae

    b. Tag - optional

    c. OS Img

    d. Instance Type: t2.micro coz free tier

    e. Key Pair: For creating key pair Step e.1: Name

                                            e.2: Type: RSA

                                            e.3: Primary Key format: .pem

    f. Allow SSH, HTTPS, HTTP.

Step 3: Click on Launch

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Hosting my project in EC2:
-----------------------------------------

Step 1: Zip your project folder before connecting via SSH.

Step 2: Enter the following commands in order:

    a. Connect to SSH [EC2]: ssh -i "C:\Users\getpr\Downloads\KeyPairFile Name.pem" ec2-user@ip

    b. Go to the backend directory using cd command and type "node server.js".

    c. Now using cd command go to frontend and type "npm start".

Step 3: You will get an success message after the frontend connection now copy the given url.

Step 4: Paste the url in yoyr browser.
