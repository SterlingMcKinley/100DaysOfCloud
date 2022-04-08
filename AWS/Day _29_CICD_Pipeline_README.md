#100DaysOfCloud Day 29

In todays lab, I wil be buidling a CI/CD pipeline. I will be using AWS CodePipeline, AWS CodeBuild, and GitHub.

CI/CD is the combined practices of continuous integration and either continuous delivery or continuous deployment. 
CI/CD bridges the gaps between development and operation activities and teams by enforcing automation in building, testing and deployment of applications. 
CI/CD services compile the incremental code changes made by developers, then link and package them into software deliverables.
Automated tests verify the software functionality, and automated deployment services deliver them to end users. 
The aim is to increase early defect discovery, increase productivity, and provide faster release cycles. 
CI/CD pipeline, forms the backbone of modern day DevOps operations.


![CICD_Pipeline](https://user-images.githubusercontent.com/91057035/162497552-2692a8cb-e227-4082-8bb6-5c012145dac8.png)



Step 1: In the AWS Console, search for S3 then Create a S3 bucket 

*Create a unique Bucket name

![bucket1](https://user-images.githubusercontent.com/91057035/162499870-df9adcb8-eb4e-41bf-80ba-3d92aee3f9fb.png)


*Please be sure to un-check "Block all public access and check I acknowledge"*

Then Click Create


![bucket2](https://user-images.githubusercontent.com/91057035/162500314-9228c28b-116d-4196-b8b9-62add032a291.png)


![bucket3](https://user-images.githubusercontent.com/91057035/162501483-f94a4d38-8058-48ed-9c82-d15e5336a272.png)


Navigate to yout S3 bucket, Amazon S3 > Buckets > mckinley1

Click on the properties tab, Scroll down to configure the following:

Static Website Hosting- Enable

Hosting type- Host a static website

Index document (this must be a .html document)

Save Changes


![bucket4](https://user-images.githubusercontent.com/91057035/162502056-a058ddd6-3fe1-4cd1-adfd-0a82f3e38128.png)

****Remain in the S3 bucket and select the PERMISSIONS tab*


STEP 2: Scroll down to Bucket policy section, click edit Bucket Policy

~Erase the current policy. Enter the following JSON policy:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::BUCKET-NAME/*"
        }
    ]
}


~ Click Save Changes

![json](https://user-images.githubusercontent.com/91057035/162511109-b900f627-5f6a-4a1d-aff3-1a429ed047ef.png)


**There is an option to use the Policy Generator to configure the policy, however an issue many surface. After running into that issue, I had to research a solution and found a work-around in which I provided above.**



Step3: Create the pipeline 

~Navigate to AWS CodePipeline and click Create Pipeline

Create a name the Pipeline and click Next


![pipeline1](https://user-images.githubusercontent.com/91057035/162514386-b0222670-3bb6-4748-a8e3-ec188c2d80b0.png)


A source provider must be chosen while creating the pipeline, I will choose GitHub (Version 2).

~Connect to our GitHub.

~Choose the repository name.

~Branch name for this project should be master




