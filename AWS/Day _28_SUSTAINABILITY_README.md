Day 28

This lab continues my dedicated effort to obtain a better understanding of the AWS Well-Architected Framework 6 Pillars.

Today, I will focus on SUSTAINABILITY

AWS is responsible for sustainability OF the cloud. Customers are responsible for sustainability IN the cloud.

In this lab I will draw proxy metrics from AWS Cost & Usage Report (sample data) and prepare the data ready for dashboarding with Amazon QuickSight. Then I will add data and combine it with the AWS Cost & Usage Reports. 



-Create a new bucket in the Amazon S3 console. (Amazon S3 >  Buckets > Create bucket)

Update the bucketname and the region, leaving the rest of the paramter with the default settings. 

  - BucketName: mckinley-proxy-metrics-lab
  - Choose a region in which you will also run the Amazon Athena queries (later): US-East (Ohio) us-east-2
  - Press "Create"
 
![bucket1](https://user-images.githubusercontent.com/91057035/162256574-271c1c9b-ec5f-4f72-8d04-0f3a7155a834.png)


![bucket2](https://user-images.githubusercontent.com/91057035/162256901-1bd8505d-4a5f-4b60-a93a-d5ab2b1f8bfc.png)


-Upload sample data files to newly created S3 bucket (parquet files from a repository). The sample data or AWS Cost & Usage Report data "mckinley-proxy-metrics-lab" Amazon S3 bucket can be queried in the next steps.

![bucket3](https://user-images.githubusercontent.com/91057035/162259138-9a4c313b-9ca8-419d-a8ae-c55753bb7347.png)


-Navigate to Amazon Athena console ( ensure the previously utilized region is set to the same region my S3 bucket resides.)
  -choose Explore the query editor, then choose set up a query result location in Amazon S3 and follow the steps from the Amazon Athena docs to specify a query result location.
  
 
 ![athena1](https://user-images.githubusercontent.com/91057035/162260566-931f73b1-1bf4-4d86-8067-1fcc27c1bfdc.png)
 ![athena2](https://user-images.githubusercontent.com/91057035/162261039-81eebb65-be88-4af5-ac0d-555cf7cacb49.png)
 
 
 
 -Since its my first time using Amazon Athena, I must set up a query result location in Amazon S3.

 


