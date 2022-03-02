In this lab I have deployed two CloudFormation templates. The first CloudFormation deployment, created an Amazon Virtual Private Cloud (VPC). The second CloudFormation template deployed an application into my VPC. To ensure reliability, one EC2 instance was deployed in my availbility zones, Elastic Load Balancing utilized to distribute it among te available EC2 instances across AZs. Lastly, the EC2 instances reside in an EC2 Auto Scaling Group, which detects the health of an instance. If any instance becomes unhealthy, it will be replaced.


Log in to AWS Console, I chose us-east-2 (Ohio) region.


![region](https://user-images.githubusercontent.com/91057035/156443964-0986e757-b2d2-409e-8ffc-4601b53562bf.PNG)


Downloaded an AWS CloudFormation Sample Template for VPC. (yaml file)
This template creates a multi-tier network appropriate for a web application including subnets for application, application load balancer database, and shared services.

![screenshot_yaml_file](https://user-images.githubusercontent.com/91057035/156443637-4cc3f4ca-8b6f-4c9d-996a-cc2f77d29452.PNG)




Deploy VPC infrastructure by uploading template file
	
  -Choose “template is ready”
	
  -Upload a template file then select yaml file
	
  -Click “Next”

![VPC1](https://user-images.githubusercontent.com/91057035/156446280-de912266-b728-4312-99c6-28042a29f82d.PNG)



Stack details

-Stack Name: WebApp1-VPC

-Some parameters are populated from the yaml file. Leave additional options at default.

-Click Next


![VPC2](https://user-images.githubusercontent.com/91057035/156446314-5bf23638-3551-4a3f-9a93-c1ee98318f83.png)



Update the Tags section
-Key: Owner

-Value: personal email address
  
![VPC3](https://user-images.githubusercontent.com/91057035/156446423-e118fd03-f49a-4f7a-9149-0dd28d5f7a0c.PNG)

  

Review, check the checkbox for the acknowledge and Click “Create stack”

![VP4](https://user-images.githubusercontent.com/91057035/156446611-b0589c7e-dcd5-47d8-9b96-c083cfd8ced4.PNG)



Creating the VPC stack will take a few minutes.

The WebApp1-VPC status will change from CREATE_IN_PROGRESS to CREATE_COMPLETE. 

![VP5](https://user-images.githubusercontent.com/91057035/156447015-0f31fae4-d8c1-42a6-8688-00b48d7a8fe2.PNG)
![VP6](https://user-images.githubusercontent.com/91057035/156447048-db5e4cda-53ba-4583-9b65-86459efc603d.PNG)



Now its time to deploy a sample application

-Create a new CloudFormation Stack with new resources via CloudFormation sample application template
	
  -Create stack > with new resources (standard)
  
![CloudFormation2](https://user-images.githubusercontent.com/91057035/156449079-16a69efc-54dc-48e0-bcde-76f1615e1071.PNG)


-Leave Prerequisite – Prepare template as default

-Select Upload a template file (staticwebapp.yaml)

![CloudFormation3](https://user-images.githubusercontent.com/91057035/156449194-7460b0a9-5515-479d-ba24-7a38275817ec.PNG)
![screenshot_yaml_file2](https://user-images.githubusercontent.com/91057035/156449223-65123966-6ee5-4452-9b53-792c50e752c6.PNG)


-Update the Stack Name to “ CloudFormationLab “ and leave additional parameters set to default values.
  
  -Click Next
  
  
![CloudFormation4_](https://user-images.githubusercontent.com/91057035/156449616-ea40d4a2-c2c7-4433-a5bf-4584a85ca532.png)


Key: Owner

Value: personal email address

![CloudFormation4](https://user-images.githubusercontent.com/91057035/156449313-c432055f-d63d-446f-beff-419d4dd1d9a0.png)


-Review CloudFormationlLab then check the acknowledgement checkbox

  -Click Create stack
  
![VP4](https://user-images.githubusercontent.com/91057035/156449732-9936fcf8-7c27-46be-a362-46c17f26184f.PNG)



The CloudFormationLab stack status will change from CREATE_IN_PROGRESS to CREATE_COMPLETE
  
  
![CloudFormation5](https://user-images.githubusercontent.com/91057035/156449881-cc94e4be-b137-458a-a5fd-55a3dad58e20.png)
![CloudFormation6](https://user-images.githubusercontent.com/91057035/156449928-6223d6e8-79ad-4101-8254-d22e30a12df2.png)
  
 
 Now that the VPC stack and CloudFormationLab app has been configured, lets review the application...
  
-Navigate to CloudFormation > Stacks > CloudFormationLab
  
-Click the “Outposts” tab and copy the URL into a browser


![CloudFormation7](https://user-images.githubusercontent.com/91057035/156450036-8fc7fb0b-0729-4cde-abae-ac8d45499902.png)

  
 
 Below the application URL

 ![URL](https://user-images.githubusercontent.com/91057035/156450569-9a77517a-1b3d-4a10-b144-3f4bfec198d4.PNG)


