In today's lab/project I will be demonstrating how to leverage Amazon AWS S3 & AWS Cloudfront to host a static webpage.

![lab_image](https://user-images.githubusercontent.com/91057035/155307248-0697f365-441f-4ae1-b707-827d1d6f731e.png)


Create a S3 bucket. Under “Block Public Access settings” uncheck “Block all public access”.


![s3_bucket](https://user-images.githubusercontent.com/91057035/155307884-e6f660e1-735a-4da5-a232-7cf6a5a9c7a9.png)

![s3_bucket_1](https://user-images.githubusercontent.com/91057035/155308187-7e6ff727-8a5e-412a-88b8-2e6d825264ba.png)


Create a simple html file using Visual Studio Code


![vsc](https://user-images.githubusercontent.com/91057035/155308473-b4b00e13-e729-49a5-9825-f59834b57e7c.png)


Upload the html file to my S3 bucket


![upload](https://user-images.githubusercontent.com/91057035/155308562-58050ae5-bafc-442c-8660-d1920adf960d.png)
![upload2](https://user-images.githubusercontent.com/91057035/155308614-02f8e82b-a95b-46db-b965-3bca1b3f3352.png)


Click “Close” and reopen the s3 bucket to navigate to the “Properties” tab

![mckinleybucket](https://user-images.githubusercontent.com/91057035/155308700-875df0c5-3db7-41cb-bb68-577db9c649ca.png)


Scroll down until you locate the “Static website hosting” section. Select Edit, then click Enable.
This will bring you into the menu where you will be able to type your index document, which is what will be shown as the home page. I updated this file with the web_content file that I uploaded. 
Click Save Changes.


![Static_website_hosting](https://user-images.githubusercontent.com/91057035/155308917-fbbf9f94-c159-4adc-8764-3bf97c137a87.png)
![permissions_tab](https://user-images.githubusercontent.com/91057035/155309118-0fffc797-81a8-40b9-bfce-2492c1678de3.png)


Scroll down to “Bucket Policy” section. This step is vital in allowing access to the content in this bucket even though access was unblocked in a previous step.
Click edit then update the bucket policy with below JSON code and ensuring the “Resource” element references my bucket ( mckinleybucket ). Click Save Changes.


![json_code](https://user-images.githubusercontent.com/91057035/155309319-e2aa9352-9ebe-4ea7-8401-285a6062d488.PNG)


Navigate back to the Static website hosting section ( Amazon S3 > mckinleybucket ) within the “Properties” tab and click the link to view the S3 bucket contents for your HTML file to appear.
Please aware that the specific name of the AWS S3 bucket is shown in the url. This is not an acceptable practice as we do not want the public to directly access this bucket. 


![mckinleybucket2](https://user-images.githubusercontent.com/91057035/155309685-523677f1-eafa-4f6f-9acc-193c047539ff.png)

![Static_website_hosting2](https://user-images.githubusercontent.com/91057035/155309741-107d7d1c-7786-4161-bc2f-d944cd5418a9.png)



I can use AWS CloudFront to fix this. Below I am creating an Amazon CloudFront distribution and configuring it to serve the S3 bucket.

![cloudfront](https://user-images.githubusercontent.com/91057035/155309811-988a5788-159d-43ff-93a0-d59ce349296c.png)

![cloudfront2_](https://user-images.githubusercontent.com/91057035/155311131-9392feba-aa95-4778-a539-11c669a71b2e.PNG)


AWS Cloudfront distribution has been completed and is ready to be deployed to user endpoints.

![cloudfront3_](https://user-images.githubusercontent.com/91057035/155311686-3f851532-251f-40c5-b168-0ef2ffcaf32f.PNG)


In order to properly remove public access for the AWS S3 Bucket, navigate back to the S3 Bucket ( mckinleybucket) console and check block all public access.  
( Amazon S3 > mckinleybucket > [Permissions tab] > Block public access  )
Click Save Changes, then type “confirm” when prompted.

![block_public_access](https://user-images.githubusercontent.com/91057035/155310048-d0131f43-c920-4f16-b405-4c88c54e67a5.png)


the access is now “Only authorized users of this account”.
![permission_authorized](https://user-images.githubusercontent.com/91057035/155310123-c58f889d-8fe4-4fd6-ac37-df834f0bd80c.png)


Validate access to the content (html file) by using the new CloudFront Domain Name found in the console. Copy the Domain Name into a web browser to test.

![domain_name_](https://user-images.githubusercontent.com/91057035/155313173-efd87f42-4cde-4cbf-89ae-6d5e569bfdf2.PNG)


Testing the domain name…

![domain_name2](https://user-images.githubusercontent.com/91057035/155310441-65e1014b-67f1-4df9-9479-e02d2c7178ff.png)
