Identity and Access Management [IAM]:
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

Task 1: Users and Groups:

Step 1: Go to the AWS mgmt console in your browser and navigate to IAM> Dashboard > Acsess Management > User/Groups

Step 2: Click on create user.

Step 3: Enter the required details:

      a. Username

      b. Select: provide user access to AWS mgmt console*

      c. choose I want to create an IAM user.

Step 3: Click on next and choose add user group.

Step 4: Click on to create a new Group.

Step 5: Enter the Group's name.

Step 6: Choose the permissions based on your need, it can be any.

Step 7: Clcik on review+create and clcik on create user.

Step 8: Now your "USER and GROUP" will be created.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task 2: Assigning a Policy:

Step 1: Go to the AWS mgmt console in your browser and navigate to IAM > Dashboard > Acsess Management > Policy.

Step 2: Remove the user that you created earlier from the group.

Step 3: Now go to the users add the needed permissions.

Step 4: Add the user to the group, attach the permissions directly.

Step 5: Click on add permissions and choose the needed one.

Testing?

Step 6: Try to createa new user group, for that you need to log in as user not root account.

Step 7: Creating your own policy.

Step 7.1: Choose either Visual Editor or JSON.

Step 7.2: If it is Visual Editor, enter the folloing:

       a. Service: actions allowed and resource 

       b. Policy name

Step 7.3: Click on create policy.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task 3: Enabling MFA

Step 1: Go to the AWS mgmt console in your browser and navigate to security creditionals which is located on top righter in your account.

Step 2: Click on Assign MFA.

Step 3: Enter the necessary details:

     a. Device name

     b. Select MFA method:

        -Authenticator app

        -Hardware token key

        -Passkey

Step 4: Set up the device and fill it up the MFA1 and MFA2 code in Authapp -> Aunthenticator app.

Step 5: You create your own passkey on your device -> Passkey

------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task 4: Assigning Roles:

Step 1: Go to the AWS mgmt console in your browser and navigate to IAM > Dashboard > Acsess Management > Roles

Step 2: Choose the service.

Step 3: Use case: for which service? eg: lamda, EC2,etc.

Step 4: Click on next.

Step 5: Select the policy.

Step 6: Select the Role name, descrption and click on trusted policy.

Step 7: Click on create.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task 5: IAM Security tools:

--> Credential Report:

Step 1: Go to the AWS mgmt console in your browser and navigate to IAM > Dashboard > Acsess Reports> Credentials Report.

Step 2: Download it as a CSV file and view it.

--> Last Accesed [Old name Access Advisior]

Step 1: Go to the AWS mgmt console in your browser and navigate to IAM > Dashboard > Acsess Management > Users > Last Accesed.
