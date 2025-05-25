Build and Deploy a Node.js Web Application with AWS Code Tools:
--------------------------------------------------------------

Task1: Setup the environment:
---------------------------
1. Go to VS code.

2. Configure AWS.

3. Verify node and npm installation.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task2: Create a node.js application in vscode:
----------------------------------------------
1. Create a app.js.

2. Test it by running node app.js.

3. Push all the files: app.js,package.json, package-lock.json and .gitignore to github repo.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task3: Configure AWS CodeBuild:
-------------------------------
1. Create a buildspec.yl file and push it to repo.

2. Set up CodeBuild project:

-Go to the AWS CodeBuild console.

-Create a new project:

-Project name: NodeJSChallengeBuild.

-Source provider: AWS CodeCommit (select nodejs-challenge-repo) or GitHub (connect your repository).

-Environment:

-Operating system: Amazon Linux 2.

-Runtime: Node.js 14.

-Image: aws/codebuild/amazonlinux2-x86_64-standard:4.0.

-Buildspec: Use buildspec.yml from the repository.

-Artifacts: Store in an S3 bucket (create one if needed, e.g., nodejs-challenge-artifacts).

-Start a build to verify it completes successfully.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Task5: Set up AWS Codepipeline:
------------------------------
1.Create an Elastic Beanstalk Environment:

-Go to the AWS Elastic Beanstalk console.

-Create a new application:

-Application name: NodeJSChallengeApp.

-Environment name: NodeJSChallengeEnv.

-Platform: Node.js (latest version).

-Environment type: Web server environment.

-Instance type: t2.micro.

2.Create a CodePipeline:

-Go to the AWS CodePipeline console.

-Create a new pipeline:

-Pipeline name: NodeJSChallengePipeline.

-Source stage:

-Source provider: AWS CodeCommit (nodejs-challenge-repo) or GitHub.

-Branch: master (or main for GitHub).

-Build stage:

-Build provider: AWS CodeBuild.

-Select the NodeJSChallengeBuild project.

-Deploy stage:

-Deploy provider: AWS Elastic Beanstalk.

-Select the NodeJSChallengeApp application and NodeJSChallengeEnv environment.

-Start the pipeline.

3.Monitor the Pipeline
