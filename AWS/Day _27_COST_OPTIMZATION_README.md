Day 27

This lab continues my dedicated effort to obtain a better understanding of the AWS Well-Architected Framework 6 Pillars.

Today, I will focus on COST OPTIMZATION.

This hands-on lab displays the steps to perform visualization of your AWS cost and usage. I will discover how to help monitor the cost and usage incurred, in alignment with the AWS Well-Architected Framework. After obtaining a visualiztion of the cost and usage of the AWS services being utilized I can perform analysis as well as cost optimization.


Log into AWS console then navigate to Cost Explorer

AWS Billing > [Cost Management] Cost Explorer


![explorer1](https://user-images.githubusercontent.com/91057035/162063911-426a82c5-dd01-497e-807f-68b4f99e52d4.png)



Click on Launch Cost Explorer

![explorer2](https://user-images.githubusercontent.com/91057035/162063988-a0efda6e-8f9e-45fc-8511-5e4130e3a8b6.png)


![explorer3](https://user-images.githubusercontent.com/91057035/162064093-d29c7db3-83b9-40d1-9f51-f14a8aa978bd.png)


On the left panel, click Reports (This will be my first time visiting AWS Cost Mgmt, so I will have to wait to generate the report) After 24 HOURS, here is my report displaying my recent activity.

![explorer5](https://user-images.githubusercontent.com/91057035/162064168-cdba349d-4cc1-48c9-9ab8-27cf42f56a88.png)


Click on Monthly costs by service. Below is my monthly activity and costs by service for the last 6 months. (After passing the AWS Certified Cloud Practitioner exam, I utilized the free tier to complete projects so cost has remained low.)

Reports can be filtered and customized in many different ways that apply to the service(s) being utilized.*


![explorer7](https://user-images.githubusercontent.com/91057035/162064333-d299c8cb-c2cf-4aa9-a0ba-4a1026e67c94.png)
![explorer8](https://user-images.githubusercontent.com/91057035/162064334-6a8262c3-c8a1-4890-a27a-0b8226e3114e.png)


Now I will create some custom EC2 reports, which will help to show costs and usage related to EC2 instances. Navigate to Cost Explorer > click Reports, and click Monthly costs by service. 

Then, click on the Service filter on the right panel, select EC2-Instances (Elastic Compute Cloud - Compute) and EC2-Other, then click Apply filters.

![explorer9](https://user-images.githubusercontent.com/91057035/162064408-4bf548dc-b871-4cf4-acd6-4c47154b9de4.png)

Below ONLY monthly EC2 Instance(s) and Other costs are displayed.
![report1](https://user-images.githubusercontent.com/91057035/162064474-71330d39-cc80-4f04-8a9c-01aa61d901d1.png)


Now change the “Group by:” to “Usage Type” to display monthly EC2 Instance(s) and Other costs by usage type.
![report1](https://user-images.githubusercontent.com/91057035/162064514-990bf6b7-79e0-4d3e-96f3-b0b49d2c1e66.png)


Let's change the bar graph to a line graph and display ONLY On-Demand costs for monthly EC2 Instance(s) and Other costs. 

Click on Purchase Option, select On Demand and click Apply filters, which will ensure we are only looking at On-Demand costs:

![report2](https://user-images.githubusercontent.com/91057035/162064667-9dab01fa-f4c5-47df-93fe-03364e170020.png)

![report4](https://user-images.githubusercontent.com/91057035/162065203-94bf9c21-3bf3-43ca-a0f4-4ec230f1353e.png)

Lets Save the report by clicking the blue “Save as…” button then name the report “Monthly EC2 Costs”








