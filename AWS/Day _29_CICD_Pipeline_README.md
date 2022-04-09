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
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
    }   
