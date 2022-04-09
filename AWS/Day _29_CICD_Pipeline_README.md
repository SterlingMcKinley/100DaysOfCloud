#100DaysOfCloud Day 29


In today's lab, I wil be buidling a CI/CD pipeline. I will be using AWS CodePipeline, AWS CodeBuild, and GitHub.

CI/CD is the combined practices of continuous integration and either continuous delivery or continuous deployment. 
CI/CD bridges the gaps between development and operation activities and teams by enforcing automation in building, testing and deployment of applications. 
CI/CD services compile the incremental code changes made by developers, then link and package them into software deliverables. 
Automated tests verify the software functionality, and automated deployment services deliver them to end users. 
The aim is to increase early defect discovery, increase productivity, and provide faster release cycles. 
CI/CD pipeline, forms the backbone of modern day DevOps operations.


![CICD_Pipeline](https://user-images.githubusercontent.com/91057035/162591095-c7446407-fed8-488c-85af-2f712d596caf.png)


Step 1: In the AWS Console, search for S3 then Create a S3 bucket
*Create a unique Bucket name

![bucket1](https://user-images.githubusercontent.com/91057035/162590796-5654eb08-1bd0-4048-820d-c497976f6043.png)


Please be sure to un-check "Block all public access and check I acknowledge"

Then Click Create


![bucket2](https://user-images.githubusercontent.com/91057035/162591034-6b5b3655-47b0-4274-8d5c-8f4ff2b0d399.png)

![bucket3](https://user-images.githubusercontent.com/91057035/162591817-aabc3664-7a3f-4a3a-ad19-57ac855d957a.png)



Navigate to S3 bucket, Amazon S3 > Buckets > mckinley1

Click on the properties tab, Scroll down to configure the following:

Static Website Hosting: Enable

Hosting type: Host a static website

Index document: (this must be a .html document)

![bucket4](https://user-images.githubusercontent.com/91057035/162592054-1bd84cda-acd8-4c10-9a5d-c37674c2b1ed.png)


Save Changes


***Remain in the S3 bucket

STEP 2: Click the Permissions tab for your S3 bucket. Scroll down to Bucket policy section, click edit Bucket Policy

~Erase the current policy. Copy & paste the following JSON policy:


    {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::mckinley1/*"
            ]
        }
    ]
    }   

There is an option to use the Policy Generator to configure the policy, however an issue may surface. 

After running into that issue, I had to research a solution and found a work-around which I provided above.






Step3: Create the pipeline

~Navigate to AWS CodePipeline and click Create Pipeline

Create a name the Pipeline and click Next


![pipeline1](https://user-images.githubusercontent.com/91057035/162592899-86eb9bdd-1a5c-4712-9390-63a3ed262f5a.png)



A source provider must be chosen while creating the pipeline, I will choose GitHub (Version 2).

Connect to my GitHub account.

Choose the repository name.

Branch name for this project will be master.

Click Next


![pipeline2](https://user-images.githubusercontent.com/91057035/162592904-811ab5f5-74a7-4a51-bf69-f3173419264c.png)



~Now Building is the next step in this process, Navigate to AWS CodeBuild and configure the following:

   -Build provider: AWS Codebuild
   
   -Region: US East (Ohio) MY REGION
   
   -Project name: I created a project. My project name is CICD Pipeline 
   
   **another window will pop-up to create a new project**
   
   
![build1](https://user-images.githubusercontent.com/91057035/162593114-344bf876-4840-4309-b440-c6ea2e1efad4.png)



![build2](https://user-images.githubusercontent.com/91057035/162593132-b650a400-f1e5-43a3-bdaf-ac7b090c37b5.png)

~Scroll down to Environment:

   -Select Managed Image.
  
   -Select your operating system preference. Ubuntu
  
   -Select the Runtime. Standard is the only option available currently.
  
   -Select the latest Image version.
  
   -Select Linux as the Environment type.
  
   -Click New service role, to allow AWS to create the role.
   
   -Click Continue to Pipeline
  
![build3](https://user-images.githubusercontent.com/91057035/162593246-9fa32eb3-867a-45e6-9cce-e45fd3fac111.png)


Final step in step 3 -  Deploy stage

Deploy provider: Amazon S3

Region: US East (Ohio)

Bucket: mckinley1 (my bucket name)

Click Next


![build4](https://user-images.githubusercontent.com/91057035/162594005-14f1aff8-857c-48f6-8358-2c0142eec74b.png)


Review all details & click Create pipeline


![build5](https://user-images.githubusercontent.com/91057035/162594201-50de7f7e-f3cc-4316-8dcc-f65ef6a06473.png)


![build6](https://user-images.githubusercontent.com/91057035/162594202-a548e8af-fe31-43e1-98a6-8430e9dce573.png)


My site is up and running....

![app1](https://user-images.githubusercontent.com/91057035/162594304-0144608f-9924-4843-947f-be01c3ac83e1.png)


Now I will edit the site...
***I must admit this project was FUN!***

![app2](https://user-images.githubusercontent.com/91057035/162594592-061219ea-769c-4c6f-8ace-8fc1502cafbe.png)
