
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
  - [Create a deploy job to beanstalk](#package-create-a-deploy-job-to-beanstalk)
  - [Create a build job for software testing](#package-create-a-build-job-for-software-testing)
  - [Upload screenshot to s3 bucket](#package-upload-screenshot-to-s3-bucket)
  - [Update Pipeline](#package-update-pipeline)
    - [Codecommit](#package-codecommit)
    - [Testcode](#package-testcode)
    - [Build and Store](#package-build-and-store)
    - [Deploy to s3 bucket](#package-deploy-to-s3-bucket)
    - [Build and Release](#package-build-and-release)
    - [Deploy to Beanstalk](#package-deploy-to-beanstalk)
    - [Build Job for Selenium test scripts](#package-build-job-for-selenium-test-scripts)
    - [Upload result to s3](#package-upload-result-to-s3) 
  - [Test Pipeline](#package-test-pipeline)

- [Resources](#page_facing_up-resources)
- [Credit/Acknowledgment](#star2-creditacknowledgment)


## :beginner:About The Project

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

## :question: Problem that this project solves 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

## :key: Solution to the problem.

<<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

## :hammer_and_wrench: Tools
- A tool
- B tool

| Name | Description |
| --- | --- |
| [`@toast-ui/editor-plugin-chart`](https://github.com/nhn/tui.editor/tree/master/plugins/chart) | Plugin to render chart |
| [`@toast-ui/editor-plugin-code-syntax-highlight`](https://github.com/nhn/tui.editor/tree/master/plugins/code-syntax-highlight) | Plugin to highlight code syntax |
| [`@toast-ui/editor-plugin-color-syntax`](https://github.com/nhn/tui.editor/tree/master/plugins/color-syntax) | Plugin to color editing text |
| [`@toast-ui/editor-plugin-table-merged-cell`](https://github.com/nhn/tui.editor/tree/master/plugins/table-merged-cell) | Plugin to merge table columns |
| [`@toast-ui/editor-plugin-uml`](https://github.com/nhn/tui.editor/tree/master/plugins/uml) | Plugin to render UML 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


## :beginner: Architecture of this project.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

## :zap: Steps to Execute the project. 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :key: Login to AWS Account

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>
### :package: Code Commit


<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Create CodeCommit repository

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create IAM user with CodeCommit policy

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate SSH keys locally

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Exchange keys with IAM user

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Pull source code from github repository 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Code Artifact

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create an IAM user with code artifact access

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Install AWS CLI configure

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Export authentication token

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Update settings.xml file in source code 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml file with repository details

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>


### :cloud: Sonar cloud 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :cloud: Create sonar cloud account

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate token

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Create SSM parameters with sonar details

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Create Build project

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Update CodeBuild role to access SSM parameter store

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :email: Create notifications for SNS or slack

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Build Project

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml with artifact version with timestamp

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Create variables in SSM parameter sore

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Create build project

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :key: Update CodeBuild role to access SSM parameter store 

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :hole: Create Pipeline

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: CodeCommit

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :test_tube: Test code

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Build

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :rocket: Deploy to s3 bucket

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :test_tube: Test Pipeline

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
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

### :package: Create a deploy job to beanstalk

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

### :package: Upload screenshot to s3 bucket

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Update Pipeline

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Codecommit

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Testcode

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Build and Store

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Deploy to s3 bucket

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Build and Release

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Deploy to Beanstalk

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Build Job for Selenium test scripts

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

#### :package: Upload result to s3

<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
</div>
<br/>

### :package: Test Pipeline


<br/>
<div align="right">
    <b><a href="#Project-09">↥ back to top</a></b>
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

