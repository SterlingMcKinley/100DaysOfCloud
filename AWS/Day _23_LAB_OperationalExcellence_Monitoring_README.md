This lab continues my dedicated effort to obtain a better understanding of the AWS Well-Architected Framework 6 Pillars.

Today, I will focus on OPERATIONAL EXCELLENCE .


Deploying infrastructure using AWS CloudFormation

![cloudformation_deploy](https://user-images.githubusercontent.com/91057035/152604078-cb2171c4-7571-41d2-83d2-5133a9463e05.png)

S3 bucket will be created during the CloudFormation deployment

![s3_bucket_creation](https://user-images.githubusercontent.com/91057035/152604145-9cf70d7c-82f6-4c3e-80c7-458885259c38.png)

![s3_bucket_creation2](https://user-images.githubusercontent.com/91057035/152604200-c2cbd4f8-ad8a-419d-a0cf-c3a6191fa35a.png)


Via Cloudwatch, made some config updates for monitoring

-	the metric Invocations range updated to 15 minutes

-	Graph metric period updated to 1minute intervals

![config_cloudwatch](https://user-images.githubusercontent.com/91057035/152604388-f106fd4c-bfe4-476c-8737-a3d6d8b50dad.png)



Creating an alarm

![alarm](https://user-images.githubusercontent.com/91057035/152604453-fb01fd64-db9f-4a61-9d91-5adeda2ee292.png)

![alarm2](https://user-images.githubusercontent.com/91057035/152604493-bf2f263a-ece2-49dc-b406-60f405e0ee9a.png)




Testing a Fail Condition – Loss of connectivity

![fail_condition_test](https://user-images.githubusercontent.com/91057035/152604576-72f113b2-8377-4f04-b81a-a8b2ab393b61.png)


SNS Failure notification via email

![failure_notification](https://user-images.githubusercontent.com/91057035/152604764-eed23ab0-d387-4298-8392-e03aba5cfe45.png)



Fixing issue and displaying monitoring/alarm recovery

-This was achieved by adding the route back to the routing table.

-Alarm state has updated/return to “OK” status.



![alarm_recovery](https://user-images.githubusercontent.com/91057035/152605077-6005afe9-fdae-4ba2-889e-7f0041060582.png)

![alarm_recovery2](https://user-images.githubusercontent.com/91057035/152605146-504295ac-adac-4601-824b-ffd43f4542d8.png)


