Day 28

This lab continues my dedicated effort to obtain a better understanding of the AWS Well-Architected Framework 6 Pillars.

Today, I will focus on SUSTAINABILITY

AWS is responsible for sustainability OF the cloud. Customers are responsible for sustainability IN the cloud.

In this lab I will draw proxy metrics from AWS Cost & Usage Report (sample data) using Amazon Athena to prepare the data for analysis.



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
 
  -select Settings tab on the navigation bar.
  
  -Choose Manage
  
  -In the Location of query result box, enter the path to the bucket that created in Amazon S3 for query results. Prefix the path with s3://. 
      
  -Save


![athena3](https://user-images.githubusercontent.com/91057035/162262877-e406b1df-2b7a-40fb-94a2-6828268ee10f.png)

![athena4](https://user-images.githubusercontent.com/91057035/162265128-6ac2a848-a30e-4961-81f3-3e9a4e6b3797.png)



In the previous steps, I have provided AWS Cost & Usage Report data in an Amazon S3 bucket. Now I must make usage data available in the AWS Glue data catalog for Amazon Athena. In order to do this, Amazon Athena allows SQL (Structured Query Language) queries to be executed on the data without loading it into a database. 

In an effort to expand my AWS knowledge and use new services, I chose to utilize AWS Glue to create the connection to S3 bucket,  use AWS Glue Crawler to locate the S3 database and pull data into AWS Glue data catalog for Amazon Athena. Once the database was located, I created tables via a DDL (Data Definition Language) SQL statement in Amazon Athena.

Here is the process I used:

-Create a new AWS Glue database via the Amazon Athena’s query editor. Amazon Athena can connect to your data stored in Amazon S3 using the AWS Glue Data Catalog to store metadata such as table and column names. After the connection is made, your databases, tables, and views appear in Athena's query editor

First I must create an AWS Glue Crawler. In the query editor, next to Tables and views, choose Create, and then choose AWS Glue crawler.
    
![athena5](https://user-images.githubusercontent.com/91057035/162276181-2a979258-cfee-4bb8-b951-133c8170bd4a.png)




-Update the Crawler name: mckinley-proxy-metrics-crawler then click Next

![glue1](https://user-images.githubusercontent.com/91057035/162276901-2c057f84-eaf1-45cc-af87-b9b16af4f31b.png)


Leave all defaults. Next

Crawler source type: Data

Repeat crawls of S3 data stores: Crawl all folders

![glue2](https://user-images.githubusercontent.com/91057035/162278021-720f2add-1d42-4835-82d3-563799b3ec2f.png)



Add a data store by updating the Include path to location the S3 bucket

Click Next

![glue3](https://user-images.githubusercontent.com/91057035/162279182-e18aaed1-34a5-4a08-8429-75480dc4653c.png)



Click Next; -Answer: No Only adding one datastore at this time

![glue4](https://user-images.githubusercontent.com/91057035/162279458-1744b90d-3b22-41d5-9ed9-5ecabc8dbc9b.png)



Create an IAM role. There are 3 different options, however creating an IAM role will provide me all permissions neccesary. The role id must be UNIQUE

Click Next
![glue5](https://user-images.githubusercontent.com/91057035/162279981-50de1d12-f9f5-4358-8db2-769fe8a83bf8.png)



Select Frequency: On Demand then click Next

![glue6](https://user-images.githubusercontent.com/91057035/162280181-0aa0e95c-b86c-4639-9f2a-7c94392de19a.png)


Configure the crawler's output

Click Add database

Database name: mckinley-proxy-metrics-lab

*I name the database after the S3 bucket to keep consistently. This will help me to correlate activity/tasks.


Click Next

![glue7](https://user-images.githubusercontent.com/91057035/162281507-e59c11b0-02f2-43df-b936-b7b24855619a.png)


Review details and click Finish

![glue8](https://user-images.githubusercontent.com/91057035/162281631-b2583a0d-a8e2-4eff-a98d-56b1eb856320.png)

![glue9](https://user-images.githubusercontent.com/91057035/162281747-1a93f6c9-220e-4cb2-9939-8dd280874f96.png)


Now click "Run it now?" in the banner.
  -Status will update to "Start" then "Ready"

![glue 10](https://user-images.githubusercontent.com/91057035/162282020-6dd4917f-686d-4ab6-b97b-ec488f43ae56.png)

![glue11](https://user-images.githubusercontent.com/91057035/162282110-7ee65487-7586-41d6-90e0-03035b0b62ca.png)


To confirm that the crawler parsed and ingested the data, we must verify.

On the left panel, select Database and you will see the S3 bucket name

![glue12](https://user-images.githubusercontent.com/91057035/162283454-1a0b1976-78a3-45f2-b85d-8cc8d3426e5e.png)


Click the S3 bucket name > Tables in mckinley-proxy-metrics-lab > mckinley-proxy-metrics-lab


![glue13](https://user-images.githubusercontent.com/91057035/162283667-172d967b-9ce6-405b-876e-c037edd0ed69.png)

![glue14](https://user-images.githubusercontent.com/91057035/162284248-743cf091-2d72-4b59-8219-d6aca7026bd7.png)

![glue15](https://user-images.githubusercontent.com/91057035/162284502-029a8c25-1055-4fc2-987c-467b9cdb6d32.png)

![glue16](https://user-images.githubusercontent.com/91057035/162284630-bb30fe8d-062f-4703-96e0-d9f406a402f6.png)


I have refreshed the AwsDataCatalog and mckinley-proxy-metrics-lab database populated. Utilizing Amazon Athena's query editor, I created tables via a DDL (Data Definition Language) SQL statement. Please note that I provided the location of the S3 bucket in the SQL statement.


![job1](https://user-images.githubusercontent.com/91057035/162329128-08b3e542-feba-42ac-9002-186864f8c36f.png)


Using the same database and table, I will aggregate the usage data by type and AWS account. I will be able calculate proxy metrics for SUSTAINABILITY & Key Performance Indicators (KPI) of application teams. 


![job2](https://user-images.githubusercontent.com/91057035/162332980-bb5220d5-d842-44ac-8811-1af87fae0a1e.png)

