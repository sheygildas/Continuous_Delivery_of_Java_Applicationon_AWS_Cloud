
# Project-09
## :ledger: Index

- [About The Project](#beginner-about-the-project)
- [Problem that this project solves ](#question-problem-that-this-project-solves)
- [Solution to the problem.](#key-solution-to-the-problem)
- [Tools](#hammer_and_wrench-Tools)
- [Architecture of this project](#house-architecture-of-this-project)
- [Steps to execute the project](#zap-steps-to-execute-the-project)
  - [Login to AWS Account ](#key-login-to-aws-account )
  - [Code Commit](#package-code-commit)
    - [Create CodeCommit repository](#package-create-codecommit-repository)
    - [Create IAM user with CodeCommit policy](#closed_lock_with_key-create-iam-user-with-codecommit-policy )
    - [Generate SSH keys locally](#key-generate-ssh-keys-locally)
    - [Exchange keys with IAM user](#key-exchange-keys-with-iam-user)
    - [Pull source code from github repository ](#package-pull-source-code-from-github-repository)
  - [Code Artifacte](#package-code-artifact)
    - [Create an IAM user with code artifact access](#closed_lock_with_key-create-an-iam-user-with-code-artifact-access)
    - [Install AWS CLI configure](#package-install-aws-cli-configure)
    - [Export authentication token](#key-export-authentication-token)
    - [Update settings.xml file in source code ](#package-update-settingsxml-file-in-source-code)
    - [Update pom.xml file with repository details](#package-update-pomxml-file-with-repository-details)
  - [Sonar cloud ](#cloud-sonar-cloud)
    - [Create sonar cloud account](#cloud-create-sonar-cloud-account)
    - [Generate token](#key-generate-token)
    - [Create SSM parameters with sonar details](#key-create-ssm-parameters-with-sonar-details)
    - [Create Build project](#rocket-create-build-project)
    - [Update CodeBuild role to access SSM parameter store](#key-update-codebuild-role-to-access-ssm-parameter-store)
  - [Create notifications for SNS or slack](#email-create-notifications-for-sns-or-slack)
  - [Build Project](#hammer_and_wrench-build-project)
    - [Update pom.xml with artifact version with timestamp](#package-update-pomxml-with-artifact-version-with-timestamp)
    - [Create variables in SSM parameter sore](#package-create-variables-in-ssm-parameter-sore)
    - [Create build project](#hammer_and_wrench-create-build-project)
    - [Update CodeBuild role to access SSM parameter store ](#key-update-codebuild-role-to-access-ssm-parameter-store)
  - [Create Pipeline](#package-create-pipeline)
    - [CodeCommit](#package-codecommit)
    - [Test code](#test_tube-test-code)
    - [Build](#hammer_and_wrench-build)
    - [Deploy to s3 bucket](#rocket-deploy-to-s3-bucket)
  - [Test Pipeline](#test_tube-test-pipeline)
  - [Create Beanstalk and RDS](#package-create-beanstalk-and-rds)
  - [Update RDS sec grp](#package-update-rds-sec-grp)
  - [Deploy DB in rds](#package-deploy-db-in-rds)
  - [Update settings.xml and pom.xml](#package-update-settingsxml-and-pom.xml)
  - [Create another build job to create artifact](#package-create-another-build-job-to-create-artifact)
  - [Create a build job for software testing](#package-create-a-build-job-for-software-testing)
  - [Create Pipeline](#package-create-pipeline)
  - [SNS Notification](#package-sns-notification)
- [Verify from browser](#earth_africa-verify-from-browser)
- [Resources](#page_facing_up-resources)
- [Credit/Acknowledgment](#star2-creditacknowledgment)


## :beginner:About The Project

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :question: Problem that this project solves 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :key: Solution to the problem.

<<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :hammer_and_wrench: Tools
- visual studio code
- AWS Account
- AWS CLI
- Maven
- JDK8 
- Sonar Cloud Account
- Git


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


## :beginner: Architecture of this project.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :zap: Steps to Execute the project. 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :key: Login to AWS Account

- Login into your AWS acount using the management console.
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>
### :package: Code Commit

- While signin in your AWS account, select `us-east-1` region aand search for CodeCommit service. 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Create CodeCommit repository

- Create CodeComit repository with the following name.




 ```sh
Name: vprofile-code-repo
   ```
   

- Follow the steps in the image below to configure you CodeComit reository so that you can connect to it through SSH.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create IAM user with CodeCommit policy

- Create an IAM user through console with CodeCommit access. We will create a policy for CodeCommit and allow full access only for `vprofile-code-repo`.
- Give the IAM user the following name.

```sh
Name: vprofile-code-admin-repo-fullaccess

   ```

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate SSH keys locally

-  Generate SSH keys locally using Git.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Exchange keys with IAM user
- Coppy the public SSH key that you generated Locally and upload it to your AM role Security credentials on AWS.

![Project Image](project-image-url)


- Next, create a config file locally using Git with the folowing details. SSH will use the config file to connect with CodeComit repo on AWS.

```sh
Host git-codecommit.us-east-1.amazonaws.com
    User <SSH_Key_ID_from IAM_user>
    IdentityFile ~/.ssh/vpro-codecommit_rsa

   ```
- Now, let's test our SSH connection to CodeCommit


```sh
ssh git-codecommit.us-east-1.amazonaws.com

   ```
   
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Pull source code from github repository 

- Clone the CodeComit repository to your local machine and take note of the location.
- Transition the `vprofile-project` repository from github to the CodeComit repository on AWS.
- Checkout the `vprofile-project` repository from github at this location [src/main/resources](https://github.com/sheygildas/Local_App_Setup/tree/local-setup/src/main/resources) directory.
- Run the following commands to do the transition.

```sh
git checkout master
git branch -a | grep -v HEAD | cur -d'/' -f3 | grep -v master > /tmp/branches
for i in `cat  /tmp/branches`; do git checkout $i; done
git fetch --tags
git remote rm origin
git remote add origin ssh://git-codecommit.us-east-1.amazonaws.com/v1/repos/vprofile-code-repo
cat .git/config
git push origin --all
git push --tags

   ```
   
- Now, the repo is ready on CodeCommit with all branches.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :package: Code Artifact

- While signin in your AWS account on the console, select `us-east-1` region aand search for Code Artifact service. 
- Create CodeArtifact repository with the following details, this CodeArtifact repository will be used by our Maven Build job.


 
```sh
Name: vprofile-maven-repo
Public upstraem Repo: maven-central-store
This AWS account
Domain name: visualpath

   ```
 
 - Follow the connection instructions given in CodeArtifact to create a connection with the `maven-central-repo`.

![Project Image](project-image-url)
 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create an IAM user with code artifact access

- Create an IAM user for CodeArtifact and configure aws CLI with its credentials of the IAM user. Also give the user programmatic access.

```sh
IAM name: vprofile-code-artifact-admin
IAM policy: AWSCodeArtifactAdminAccess

   ```
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Install AWS CLI configure

- Configure aws CLI with its IAM credentials.Install AWS CLI if you don't have it installed 

```sh
aws configure <provide your iam user credentials>
AWS Access key ID <>
AWS Secret key ID<>
Default region name <us-east-1>

   ```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Export authentication token

- Run command to get authentication token as in the Code Artifact instructions. 

```sh
export CODEARTIFACT_AUTH_TOKEN=`aws codeartifact get-authorization-token --domain visualpath --domain-owner 392530415763 --region us-east-1 --query authorizationToken --output text`

   ``` 
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update settings.xml file in source code 

- Update pom.xml and settings.xml with correct urls as suggested in instruction then push files to codeCommit.

- On your local machine, update the setting.xml file in our `vprofile-project` repository. change the following.

```sh
repository url: <replace it with your aws repo url found in the code artifact connection instruction>
domain name: <change it to your own domain name>
url below the domain name: <put a forward slash (/) at the end of the url>
   ```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml file with repository details

- Update pom.xml and pom.xml file with correct urls as suggested in instruction then push files to codeCommit.

- On your local machine, update the pom.xml file in our `vprofile-project` repository. change the following.

```sh
repository url: <replace it with your aws repo url found in the code artifact connection instruction>
   ```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


### :cloud: Sonar cloud 
- Set up a code analysis job using the sonar cloud. Folow the following steps to accomplish this task.


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :cloud: Create sonar cloud account

-  Go to https://www.sonarsource.com/products/sonarcloud/ and create an account if you have not done that yet.
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate token

-  Sign in and go to -> `My Account` -> `Security`. Generate token name as `vprofile-sonartoken`. save the token somewhere on your machine.


![Project Image](project-image-url)

- Create a project, got to ->` Analyze Project` -> `create project manually`. 

```sh
Organization: freedomthinker-projects
Project key: vprofile-repo
```
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>



#### :key: Create SSM parameters with sonar details
- Login to your AWS console and search for System Manager.
- Create parameters with the variables below which with obtain from sonar cloud.


```sh
ORGANIZATION          freedomthinker-projects	
HOST                  https://sonarcloud.io
PROJECT               vprofile-repo
SONARTOKEN            SecureString (put your sonarcloud token)
```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Create Build project

- On your AWS console bsearch for CodeBuild.
- Create Build Project with the following details.

```sh
ProjectName: Vprofile-Build
Source: CodeCommit
Branch: ci-aws
Environment: Ubuntu
runtime: standard:5.0
New service role: auto generated
Insert build commands: Go to the folder aws-files/sonar_buildspec.yml from the source code you clone and copy the content 
(Update sonar_buildspec.yml file parameter store sections with the exact names we have given in SSM Parameter store)
CloudWatch Logs-> GroupName: vprofile-nvir-buildlogs
StreamName: sonar-build-job
```

 
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Update CodeBuild role to access SSM parameter store
- Under `vprofile Build` job, got to `edit`->`Environment` copy the role name 
- Go to IAM service and find the role you copied and edit the role by attaching the system manager policy to it.


![Project Image](project-image-url)
 
 
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


#### :hammer_and_wrench: Build Project
- Under `vprofile Build` job, got to `start Build`

![Project Image](project-image-url)

- Go to SonarCloud and checkout the overview of the project.

![Project Image](project-image-url)
 


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml with artifact version with timestamp

- Update pom.xml and pom.xml file with correct urls as suggested in instruction then push files to codeCommit.
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Create variables in SSM parameter sore

- Login to your AWS console and search for System Manager.
- Add parameter with the variables below which with obtain from aws cli.


```sh
CODE ARTIFACT TOKEN: SecureString (put your token generated from aws cli)
```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Create build project

- Let create another job that will build our artifact.

- On your AWS Console, go to `CodeBuild` -> `Create Build Project`.

```sh
ProjectName: Vprofile-Build-Artifact
Source: CodeCommit
Branch: ci-aws
Environment: Ubuntu
runtime: standard:5.0
New service role: auto generated
Insert build commands: Go to the folder aws-files/sonar_buildspec.yml from the source code you clone and copy the content 
(Update sonar_buildspec.yml file parameter store sections with the exact names we have given in SSM Parameter store)
CloudWatch Logs-> GroupName: vprofile-nvir-buildlogs
StreamName: buildjob
```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Update CodeBuild role to access SSM parameter store 


- Under `vprofile Build` job, got to `edit`->`Environment` copy the role name 
- Go to IAM service and find the role you copied and edit the role by attaching the system manager policy to it.


![Project Image](project-image-url)
 
- Under `vprofile Build` job, got to `start Build`

![Project Image](project-image-url)


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


### :email: Create notifications for SNS or slack
- On you AWS console reach for SNS.
- Create an SNS topic from SNS service and subscribe to topic with email.


```sh
Topic Name: vprofile-pipeline-notification
Subscription: email
Endpoint: <your email address>
```
- Go to your email inbox and confirm the subcription 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/> 


### :hole: Create Pipeline
- Create CodePipeline with the following details

```sh
Name: vprofile-CI-Pipeline
SourceProvider: Codecommit
Respository name : vprofile-code-repo
branch: ci-aws
Change detection options: CloudWatch events
Build Provider: CodeBuild
ProjectName: vprofile-Build-Aetifact
BuildType: single build
Deploy provider: Amazon S3
Bucket name: vprofile98-build-artifact
object name: pipeline-artifact
``` 
- Under your vprofile-CI-Pipeline go to `edit`->`add stage` and add Test stages to your pipeline

```sh
Name: Test
Action Name: Snar-Code-Annalysis 
Action Provider: CodeBuild
Input Acrtifact: SourceArtifact
Project Name: vprofile-build
Build type: Single build.
``` 

- Under your vprofile-CI-Pipeline go to `edit`->`add stage` and add Deploy stages to your pipeline


```sh
Name: Deploy
Action Name: Deploy-To-S3 
Action Provider: Amazon S3 
Input Acrtifact: BuildArtifact
Create an S3 bucket and a folder to store our deploy artifacts
Bucket: <give the s3 bucket name you created>
S3 bucket key <give the name of the folder you created in S3>
Select extract file before deploy
``` 


- Go to `settings`->`notification` under Pipeline and create a notification rule 

Now, under your vprofile-CI-pipeline click on `release changes` and watch the pipeline execute 

![Project Image](project-image-url)


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: CodeCommit

- Make some code changes using your IDE and push it to your repo, go to AWS and watch the pipeline auto execute.

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>



### :package: Create Beanstalk and RDS
stalk and RDS
- On the console, search for `elastic beanstalk`->`Applicatio`-> `create application`
- Create an elatic Beanstalk environment for our vprofile application with the following details.



 ```sh
Name: vprofile-app
Platform: Tomcat
Application code: Sample code
Click create.

Capacity: LoadBalanced
Min: 2
Max: 4
EC2 key pair: ci-vprofile-key 
Tags: 
Name:Project
Value: vprofile
click create app
```

### :package: Create RDS
- On the console, search for `RDS` -> `create database`->``standard create`
- 
- Create an RDS service with the details below



 ```sh
Engine: MySQL
version: 5.7
Template: Free-Tier
DB Identifier: vprofile-cicd-mysql
credentials: admin
Auto generate password (write down your password)
db.t2.micro
Create new Security Group: 
Name: vprofile-cicd-rds-mysql-sg
initial db name: accounts
Scroll down and click on create db
``` 
- Click `View credential details` and write down your password.

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Update RDS sec grp
- On your console, goto `EC2`->`Security group` search for DB security 
- Update RDS Security Group Inbound rules to allow access to Beanstalk instances on port 3306.


<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Deploy DB in rds

- Go to Beanstalk security group, and allow access to port 22 from  MyIP
- SSH into your beanstalk instance to install mysql client in this instance to be able to connect RDS
- Use the following scripts to create schema in our database.



 ```sh
sudo -i
yum install mysql git -y
mysql -h <RDS_endpoint> -u <RDS_username> -p<RDS_password>
show databases;
git clone https://github.com/rumeysakdogan/vprofileproject-all.git
cd vprofileproject-all/
git checkout cd-aws
cd src/main/resources
mysql -h <RDS_endpoint> -u <RDS_username> -p<RDS_password> accounts < db_backup.sql
mysql -h <RDS_endpoint> -u <RDS_username> -p<RDS_password>
use accounts;
show tables;
``` 

- In your Beanstalk environment under `Configuration` -> `load balancer` -> `Processes` , update Health check path to `/login`

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Update settings.xml and pom.xml
Go to CodeCommit on the AWS console, select `cd-aws` branch updates pom and settings.xml files. 

Change the url of your pom.xml and add the correct url from your code artifact connection steps shown earlier.


 ```sh
<repository>
        <id>codeartifact</id>
        <name>codeartifact</name>
    <url>https://visualpath-392530415763.d.codeartifact.us-east-1.amazonaws.com/maven/maven-central-store/</url>
      </repository
``` 


Change the url of your setting.xml and add the correct url from your code artifact connection steps shown earlier.
 


 ```sh
<<profiles>
  <profile>
    <id>default</id>
    <repositories>
      <repository>
        <id>codeartifact</id>
    <url>https://visualpath-392530415763.d.codeartifact.us-east-1.amazonaws.com/maven/maven-central-store/</url>
      </repository>
    </repositories>
  </profile>
</profiles>
<activeProfiles>
        <activeProfile>default</activeProfile>
    </activeProfiles>
<mirrors>
  <mirror>
    <id>codeartifact</id>
    <name>visualpath-maven-central-store</name>
    <url>https://visualpath-392530415763.d.codeartifact.us-east-1.amazonaws.com/maven/maven-central-store/</url>
    <mirrorOf>*</mirrorOf>
  </mirror>
</mirrors>
``` 
  
  
  
<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Create another build job to create artifact 

- Go to AWS console and search for `CodeBuild` and change the branch from `ci-aws`to `cd-aws`
- Create a new job and  called it  `Build Project` to deploy artifacts to BeanStalk.


 ```sh
Name: Vprofile20 BuildAndRelease
Source: CodeCommit
Repository: vprofile-code-repo
branch: cd-aws
Environment
Managed image: Ubuntu
Standard
Image 5.0
use the existing role from previous Build project 
Insert build commands: 
From source code we will get spec file under `aws-files/buildAndRelease_buildspec.yml`.
Logs:
LogGroup: vprofile-cicd-logs
Stream name: BuildAndReleaseJob
``` 

- Add 3 new parameters of our RDS instance to SSM Parameter store
- On you AWS console search for SSM and add the following. 

 ```sh
RDS-Endpoint: String
RDSUSER: String
RDSPASS: SecureString
``` 

- Test our build project 


![Project Image](project-image-url)
 
 
<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


### :package: Create a build job for software testing

- Let's start by creating an S3 bucket through the AWS console. 


 ```sh
Name: <give it a unique name>
Region: <region were our pipeline exist>
``` 

- Create a new Build job for Selenium code Testing with details below. 

 ```sh
Name: SoftwareTesting
Source: CodeCommit
Repo: vprofile-code-repo
Branch: seleniumAutoScripts
Environment:
Windows Server 2019
Runtime: Base
Image: 1.0
use the existing role 
Insert build commands: Go to the folder `aws-files/win_buildspec.yml`from the source code you clone and copy the content .
Update url part to our Elastic Beanstalk URL.
Artifacts:
Type: S3
Bucketname: vprofile-cicd-test123 (used your own name)
Enable semantic versioning
Artifcats packaging: zip
Logs:
LogGroup: vprofile-cicd-logs 
Streamname: SoftwareTestingJob
``` 



<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


### :package: Create Pipeline

- Create CodePipeline with name `vprofile-cicd-pipeline` 


 ```sh
Name: <give it a unique name>
Source:CodeCommit
Repo: vprofile-code-repo
Breanch: cd-aws
Change detection options: CloudWatch events

Build
BuildProvider: CodeBuild
ProjectName: Vprofile-BuildAndRelease
BuildType:Single Build

Deploy
Deploy provider: Beanstalk
application: vprofile-app
Environment: vprofile-app-env
``` 

- Disable transitions and Edit pipeline to add more stages.

- On our code pipeline, goto `edit` and add a stage

- Add a Code Annalysis stage to our codepipeline withe the details below. 




 ```sh
Name: CodeAnalysis
Action provider: CodeBuild
Input artifacts: SourceArtifact
Project name: Vprofile-Build
``` 

- Add a BuildAndStore stage to the codepipeline:


 ```sh
Name: BuildAndStore
Action provider: CodeBuild
Input artifacts: SourceArtifact
Project name: Vprofile-Build-artifact
OutputArtifact: BuildArtifact
```  

- Add a  DeployToS3 stage to the codepipeline:



 ```sh
Name: DeployToS3
Action provider: Amazon S3
Input artifacts: BuildArtifact
Bucket name: vprofile98-build-artifact
Extract file before deploy
```  

- Go to Build stage `Edit` Stage. Change Output artifact name` as `BuildArtifactToBean`
- Go to Deploy stage, `Edit` stage. We will change `InputArtifact` to `BuildArtifactToBean`


- Add a SoftwareTesting stage to the codepipeline:


 ```sh
Name: Software Testing
Action provider: CodeBuild
Input artifacts: SourceArtifact
ProjectName: SoftwareTesting
```

- Save all change and RUN the CodePipeline




<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package:  SNS Notification
- create an SNS notification for your pipeline 
- Click `notify`-> `Manage Notification` and use the following details

 ```sh
vprofile-aws-cicd-pipeline-notification
Select all
Notification Topic: use same topic from CI pipeline
```

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


### :package: Test Pipeline

- Time to test our pipeline.
<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


## :earth_africa: Verify from browser

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>


## :page_facing_up: Resources

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


## :star2: Acknowledgment


<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

