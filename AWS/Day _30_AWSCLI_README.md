#100DaysofCloud Day 30

In today's lab I will be creating EC2 instance via AWS CLI.

EC2 is one of the most significant services provided by AWS. EC2 can be provisioned and/or managed by via GUI or CLI. 
CLI can be more efficient and faster if multiple EC2 instances are being launched at a time. AWS CLI is one method in managing everything about an instance using the command-line interface of AWS. 

In an effort to get more hands-on experience with AWS, I will be using AWS CLI to create/launch an EC2 instance.


***Step 1: Creating a key pair***

aws ec2 create-key-pair --key-name <your key name>
  
  
![awscli2](https://user-images.githubusercontent.com/91057035/162811614-f9001304-b9b2-4e23-b455-8dc3c40fdc02.png)

 
  
To confirm we can check AWS console.
  
  ![awscli3](https://user-images.githubusercontent.com/91057035/162811717-553bfcad-041f-4bd7-a9bc-1163c8c52153.png)

  
***Step 2: Creating the security group***

aws ec2 create-security-group --group-name <your group name>

 
![awscli4](https://user-images.githubusercontent.com/91057035/162811932-46c60906-8235-4065-8504-396bb3e77123.png)


  To confirm we can check AWS console.
  
  ![awscli5](https://user-images.githubusercontent.com/91057035/162812028-45bf1446-0ddc-4b08-8c20-2243e4ca929d.png)

  
***Step 3: Launching EC2 instance***

aws ec2 run-instances --image-id <your imageid> --instance-type <your instance type> --count <total no. of instance> --subnet-id <subnet id of preferred zone> --security-group-ids <id of securitygroup> --key-name <name of key value pair>

![awscli6](https://user-images.githubusercontent.com/91057035/162812209-1b7cb293-0990-4890-8a8d-26e06b899ebf.png)

  
To confirm we can check AWS console.
 

  ![awscli6_1](https://user-images.githubusercontent.com/91057035/162812647-d519996b-c8e5-4b01-9c5d-bff1e67edadd.png)

  
Step 4: Creating the EBS volume

aws ec2 create-volume --volume-type<the type of storage volume> --size <size of storage>


 ![awscli7](https://user-images.githubusercontent.com/91057035/162812799-b9f64ccd-8599-4321-a804-09a81ff74c3b.png)

 To confirm we can check AWS console.
  
 ![awscli9](https://user-images.githubusercontent.com/91057035/162813135-1bd2d02b-153d-4584-b6a4-fddc7d22631f.png)

  
***Step 5: Attaching that EBS Volume to the EC2 instance***
  
aws ec2 attach-volume --volume-id <id of created volume> --instance-id <id of instance where volume is to be attached> --device <device name>

  
 ![awscli8](https://user-images.githubusercontent.com/91057035/162813385-47060b9b-5353-43a1-9246-60183db961aa.png)
  
 
 To confirm we can check AWS console.
 
![awscli8_1](https://user-images.githubusercontent.com/91057035/162813750-071e24f3-98da-4091-9f5c-009280bb1ec8.png)
  
  
 
  ***Managing EC2 instances using AWS CLI***
  
  
 Stopping/Starting EC2 instances 

  
 aws ec2 stop-instances --instance-ids <instance-id>
  
 ![awscli12](https://user-images.githubusercontent.com/91057035/162814064-eeaf55e1-f082-4352-ac8d-af1abb622ce9.png)

  
  
  aws ec2 start-instances --instance-ids <instance-id>
  
  ![awscli13](https://user-images.githubusercontent.com/91057035/162814104-71eba21d-c602-4308-a105-584135cab4a0.png)

  
 Retrieving the ec2 instance status
  
aws ec2 describe-instance-status --instance-id
  

![awscli14](https://user-images.githubusercontent.com/91057035/162814295-013fc4e5-4e82-4435-a469-ff2d38439689.png)

  
AWS user-friendly GUI is good way to see all services and options of a service. However, ***AWSCLI is faster, more efficient and powerful.***
