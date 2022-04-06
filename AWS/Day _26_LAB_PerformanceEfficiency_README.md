Day 26

This lab continues my dedicated effort to obtain a better understanding of the AWS Well-Architected Framework 6 Pillars.

Today, I will focus on PERFORMANCE EFFICIENCY.


I will create an Amazon EC2 instance running Amazon Linux. Then configure an Amazon CloudWatch Dashboard to gather views of the health and performance information for that instance.

-Log into AWS console (using new/updated loadout)
-First, deploy a VPC via a CloudFormation template

CloudFormation > Stacks  > Create Stack

Prerequisite - Prepare template: Template is ready
Specify template: Upload template file

Next


![vpc_cloudformation1](https://user-images.githubusercontent.com/91057035/161576108-467d6115-636d-4907-a118-2c6e00e1d190.png)

![vpc_cloudformation2](https://user-images.githubusercontent.com/91057035/161576135-dce2753b-60e8-4a06-9aaf-1e42eb35fa41.png)




Updated the “Stack Name” to be identified and the parameters being populated from the yaml file. Click Next

Stack name: PerfLab-VPC
Parameters: All defaults

![vpc_cloudformation3](https://user-images.githubusercontent.com/91057035/161576196-3048b7b6-aee6-425d-acca-ecb59eb13dd4.png)




Updated Tags parameter which will help identify my stacks
Key: Owner
Value: <email address>

Press “Add Tag”
Press Next


![vpc_cloudformation4](https://user-images.githubusercontent.com/91057035/161576930-c5e98cc5-cf0c-4c17-ac03-64202ba44362.png)
  


Last step in deploying the infrastructure will be to review, check the checkbox to  acknowledge that Cloudformation will create IAM roles. Then press “Create Stack”

Status update from CREATE_IN_PROGRESS to CREATE_COMPLETE



![vpc_cloudformation5](https://user-images.githubusercontent.com/91057035/161577102-bd95fe99-9d04-4ae0-bd72-9675f64580c0.png)


Next, I will be deploying a Linux instance via a CloudFormation template. Navigate to CloudFormation:

CloudFormation > Stacks  > Create Stack
Prerequisite - Prepare template: Template is ready
Specify template: Upload template file

Press “Next”


![linux1](https://user-images.githubusercontent.com/91057035/161577154-f4398129-5a36-490a-b1e8-963c54cbf3d4.png)


![linux2](https://user-images.githubusercontent.com/91057035/161577172-8c451041-5d03-4988-966d-968815d8040d.png)


Update the stack details with the following

Stack name: LinuxMachineDeploy
Parameters: All default

Press Next

![linux3](https://user-images.githubusercontent.com/91057035/161577254-d9bc4332-c23e-4f77-8196-d1ab4825d994.png)

  
Update Configure Stack Options with tags which will help identify my stacks
Key: Owner
Value: <email address>

Press “Add Tag”
Press Next



Last step in deploying the infrastructure will be to review, check the checkbox to  acknowledge that Cloudformation will create IAM roles. Then press “Create Stack”

Status update from CREATE_IN_PROGRESS to CREATE_COMPLETE


![linux5](https://user-images.githubusercontent.com/91057035/161577884-594c1686-1d55-4596-9343-29983b4cb965.png)
 
![linux6](https://user-images.githubusercontent.com/91057035/161577951-c85dca65-9730-42df-99e1-8abd7286fab7.png)


At this point, I have deployed an infrastructure and a single Amazon Linux 2 EC2 instance. Now, I will create a CloudWatch Dashboard to monitor the memory and CPU resources consumed by the instance.

Navigate to CloudWatch service -  Dashboards > Create dashboard

Under Dashboard Name, type in “LinuxEC2Server” and then click “Create Dashboard”


![cloudwatch](https://user-images.githubusercontent.com/91057035/161578814-901a1822-f7c4-49cf-b8b2-6b186d494b54.png)

  

Click “Add widget”

Two windows with different options will appear to add to the dashboard. I selected the following options:
1- line
2- metrics

Then click Configure

![cloudwatch2](https://user-images.githubusercontent.com/91057035/161578864-d03dfec0-246b-4d57-914d-bd3121aea8b8.png)



Under Browse tab and  “Metrics”, scroll down to “Custom Namespaces” and click on “PerfLab”

![cloudwatch 3](https://user-images.githubusercontent.com/91057035/161578991-0e6d99a1-e5e3-4e70-b6e9-8a1c89e5a025.png)

Select/click “ImageId, InstanceId, InstanceType, cpu”

![cloudwatch4](https://user-images.githubusercontent.com/91057035/161579002-fcfecedb-3e65-427e-a923-5e685ac18ac2.png)


![cloudwatch5](https://user-images.githubusercontent.com/91057035/161579050-ca9e1366-8d1e-4e44-a0e4-b08b749a37b2.png)



In the  Instance Name column that starts with “LinuxMachineDeploy”, click on one of the InstanceIds. A small window will appear, select “Search for this only”. 
![cloudwatch6](https://user-images.githubusercontent.com/91057035/161579161-0d555a62-4025-4dd5-82c6-cf010ba17389.png)


Under the Metric Name column, look for “cpu_usage_user” and then click “Add to search”.  Once added to the search, there will only be 2 visible options.


![cloudwatch7](https://user-images.githubusercontent.com/91057035/161579205-a21b2654-f98e-43c0-9305-0c8aa5eeedf9.png)


Click the checkbox next to BOTH metrics then navigate to the “Graphed Metrics (2)” tab, and on the right side next to Period, select “5 seconds”

Click Create Widget


![cloudwatch8](https://user-images.githubusercontent.com/91057035/161579326-b346d9c4-151a-4945-b3cc-b62985ee9607.png)

![cloudwatch9](https://user-images.githubusercontent.com/91057035/161579415-1742e1ff-cfa3-4ee7-9002-6f4f68787fc0.png)




Adding metrics for available memory is next for our Linux EC2 dashboard.
Click on the “Add Widget” button (in the upper right corner) using the following options:
-Click Line
-Click Metrics and then Configure
-Select “PerfLab” under Custom Namespaces and then select the metric group “ImageId, InstanceId, InstanceType” (search only for the InstanceId)
-In the Metric Name column, select the “mem_used” and “mem_total” and click the check box next to it
-Click on “Graphed Metrics (2)” tab  and  change the period to “5 seconds” 
-Click Create widget and then click Save Dashboard

 ![cloudwatch10](https://user-images.githubusercontent.com/91057035/161579525-f3dcb728-8b68-47b3-a972-d76399fc4a96.png)


Both widget can be modified and/or adjusted.

![cloudwatch11](https://user-images.githubusercontent.com/91057035/161579715-56d9ebe4-c0b4-4b46-88ba-7b1631df92e7.png)

  
  
The dashboard displays CPU and Memory stats, now I will add activity that can be visible on the dashboard.

First I will connect to my ec2 instance via Session Manager and install tools to add load/activity.


![stress1](https://user-images.githubusercontent.com/91057035/161579769-3d81d096-cdf0-4126-9fac-29fb8eb6be8d.png)




After installing stress tools, I executed the below command

sudo stress --cpu 8 --vm-bytes $(awk '/MemAvailable/{printf "%d\n", $2 * 0.9;}' < /proc/meminfo)k --vm-keep -m 1


Below you will see an increase in activity then a decrease due to the load being terminated via command


![stress2](https://user-images.githubusercontent.com/91057035/161579920-3d97d9ca-39ba-44b3-a1c6-6877e7d4bf31.png)


In this lab dedicated to PERFORMANCE EFFICIENCY, I was able to create an EC2 instance and generate simulated high-load events to observe how CloudWatch can be used to monitor those resources. 

![stress 3](https://user-images.githubusercontent.com/91057035/161579963-470f8591-388f-4822-a3a6-a447120e4364.png)
