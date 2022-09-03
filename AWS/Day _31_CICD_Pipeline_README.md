CI/CD (Continuous Integration/Continuous Delivery) a method to deliver apps to customers by introducing automation into the stages of app development. Continuous integration is the process of merging changes to the main branch of a repository as often as possible. These changes are then validated by creating a build and running automated tests against the build. Continuous delivery is an extension of continuous integration since it automatically deploys all code changes to testing and/or production environments after the build stage.
In this project, I created a CI/CD pipeline to deploy a Flask application. The goal of this project is creating the pipeline according to specific instructions, meanwhile identifying ways to improve or further automate. 

The tools I used in this project:
*  Git
*  GitHub
*  Jenkins
*  AWS EC2
*  AWS Elastic Beanstalk


![CICD_pipeline](https://user-images.githubusercontent.com/91057035/188248400-ca98031b-c75d-4531-acbb-9e898208f947.png)



# **Step1: Code Development**

o	In GitHub, fork/copy a repository containing application and config files to GitHub profile.

![Picture1](https://user-images.githubusercontent.com/91057035/188269197-602b4f89-3610-47f4-a7e2-b3c95cb223e2.png)

 
o	Create a local git repository (on ubuntu virtual machine) then connect my local repository to remote repository (GitHub)

o Command to create a git repo:

      git init

- Commands to connect local git rep to GitHub:

	`ssh-keygen -t rsa -b 4096 -C "myemail@mail.com"`

	`eval "$(ssh-agent -s)"`

	`ssh-add ~/.ssh/id_rsa`

  (cat id_rsa.pub then Add the ssh public key to GitHub)
		
      git remote add origin git@github.com:SterlingMcKinley/kuralabs_deployment_1.git

o Command to test connection from local to GitHub:
	
      ssh -T git@github.com
 
 ![Picture2](https://user-images.githubusercontent.com/91057035/188270152-2cbffc4e-274d-4077-be04-f7d89e92d175.png)

 
o	Cloned a repository from GitHub ( https://github.com/SterlingMcKinley/kuralabs_deployment_1.git) to my local git repository

      git clone https://github.com/SterlingMcKinley/kuralabs_deployment_1.git
      
      
 ![Picture3](https://user-images.githubusercontent.com/91057035/188270360-b180612d-ae95-4039-9c6e-dd9177a53b80.png)



  (The above steps allow version control for any changes made to the application and/or configuration files.)

Now that I have pulled the original version of the application, I can either modify or test the application. I choose to test the application to determine functionality or if any updates are required. In order to locally test the application, I must create a virtual environment. Virtual environments are beneficial to prevent configuration drift. 

o	The following command will create and activate my virtual environment (be sure the current location is the local git repo)
-	sudo apt install pip	 #Pip a tool for installing Python packages
-	pip - -version 		#Checking version of pip
-	pip install virtualenv 	pip #Tool that creates virtual env for Python app
-	vim .bashrc

(-Add the below line to the BOTTOM of .bashrc file)

PATH=$PATH:/home/<your username>/.local/bin	#Sets env variable
  
-	pip list				              (#Lists installed packages)
  
-	virtualenv venv		            (#Creates virtual environment)
  
-	export FLASK_APP=application	(#exports the variable for the application)
  
-	source ./venv/bin/activate	  (#activates the virtual environment)
  
-	pip install Flask 		        (#install Flask package)
  
-	flask run		                  (#start the flask app within virtual environment)

	
	![Picture4](https://user-images.githubusercontent.com/91057035/188270406-debea650-5e9a-41cb-80f4-3e5e7be2c008.png)

	
The virtual environment is running allowing the flask app to be served locally, I will attempt to access the application. The url to the application will be: 

localhost:5000 or http://127.0.0.1:5000

	
![Picture5](https://user-images.githubusercontent.com/91057035/188270435-1e00b9d9-62d3-4720-8333-80bc7a0423c5.png)

	
**THE APPLICATION WORKS!** Now I can integrate the application to the next phase as well as another tool to perform additional tests.



 # **Step2: Continuous Integration**
  
  
In order to merge any changes into the test and automation process, I must build the integration environment. I will be building an EC2 instance. On that instance I will install Jenkins.
  
o	To create an EC2 instance we must complete a couple step that I will explain below.
  * Go to AWS console, sign in and navigate to the EC2 service/console
  
    https://console.aws.amazon.com/ec2/

o	On the left panel, navigate to Network & Security then select Key Pairs
  *	Create a key pair with a uniquely identifiable name.
  *	Download the key pair and save it locally.
  *	Permissions must be closed/private. (chmod 400 <keyfile>.pem)
 
	
	![Picture6](https://user-images.githubusercontent.com/91057035/188270455-01edb865-5485-467f-bc09-dba41674463f.png)

	
o	On the left panel, navigate to Network & Security then select Security Groups
  * Click Create Security Group
  * Enter an identifiable name for the security group
  * On the Inbound section, rules must be configured. 
o	Add 3 rules and the following configs
  * Type: SSH | Source: Custom & in the drop-down box, select 0.0.0.0/0
  * Type: Custom TCP Rule | Port: 8080 | Source: Custom & in the drop-down box, select 0.0.0.0/0
  * Type: HTTP | Port: 80 | Source: Custom & in the drop-down box, select 0.0.0.0/0
o	Lastly, select Create

 
![Picture7](https://user-images.githubusercontent.com/91057035/188270473-732cfddd-e0e3-4bd4-aba9-1b32903c8862.png)

 
![Picture8](https://user-images.githubusercontent.com/91057035/188270489-1dc694b8-caba-4405-b284-4255bae344ab.png)

	
	
The pre-steps for creating the EC2 instance is complete.

o	Go to EC2 Dashboard, then select Launch Instance and 
  * Name the instance ( ie ubuntu_jenkins)
  * Application and OS Images: Ubuntu
  * Instance type: (in this example t2.micro – Free tier eligible)
  * Key pair: (select the key pair previously created)
  * Network settings: select existing security group then choose the security group we previously created
  * Select Launch Instance
  
    (EC2 instance will take a few minutes to complete. On completion, the instance will be running)
 

![Picture9](https://user-images.githubusercontent.com/91057035/188270590-ee65b083-b510-4a92-b900-325f192b30cf.png)


Lets connect to the EC2 instance. The EC2 instance will be the computing platform in which Jenkins will be installed.
* Connect to EC2 instance (Ubuntu Linux)
 - Navigate to EC2 > Instances and Select the “instance name”
 - The lower half of the console will display an instance summary.
 - Copy the Public IPv4 DNS

 
![Picture10](https://user-images.githubusercontent.com/91057035/188270666-1c7feee5-d970-452f-b2d4-aefb2ea2df33.png)


o	Go to your terminal or ssh client to ssh into the EC2 using port 22
  * Execute ssh command to connect to the EC2 instance

    ssh -i </the/location/of/keypair>.pem ubuntu@ec2-XX-XXX-XX-XXX.compute-1.amazonaws.com


![Picture11](https://user-images.githubusercontent.com/91057035/188270744-a0f5f133-da1b-4e4e-acdb-793b3536232b.png)


  * Installing Jenkins in the EC2 instance
  * Execute the following commands on the fresh EC2 Ubuntu Linux instance

#installs java runtime engine for java apps like Jenkins

    sudo apt update && sudo apt install default-jre  

#Adds the repository key to your system/EC2 instance

    wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key |sudo gpg --dearmor -o /usr/share/keyrings/jenkins.gpg

#Append the Debian package repository address the EC2 Ubuntu Linux source.list 

    sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.gpg] http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

#updates packages and dependencies 

    sudo apt update

#install Jenkins and its dependencies

    sudo apt install jenkins
  
o	Start Jenkins

    sudo systemctl start jenkins.service

#command to check if the Jenkins services is active/running

    sudo systemctl status jenkins

 
![Picture12](https://user-images.githubusercontent.com/91057035/188270766-e22689ba-0ab9-4a96-9abf-87ac0d484de5.png)


o	Go to your browser to use the Jenkins GUI
  * The Jenkins GUI URL is the Public IPv4 IP address of the EC2 instance using port 8080
  
        http://XXX.XX.XXX.XXX:8080 
  
![Picture13](https://user-images.githubusercontent.com/91057035/188270799-fb69fea5-b1ad-46b5-81d5-98e02ae14349.png)
	
	
  *	Create user credentials and login
  *	In order to connect Github to Jenkins an access token must be created.
  *	In GitHub, navigate to GitHub settings > developer settings > SSH and GPG keys
  *	Select personal access token and create a new token
  *	Create a name for the token and select the below settings for access token permissions:
        -	Repo
        -	Admin:repo_hook
  * Select Generate token

	
![Picture14](https://user-images.githubusercontent.com/91057035/188270830-e50b9ac0-8214-4dc4-9c1d-6b47d7ab91f9.png)
	

o	Lets prepare a multibranch build
  *	Select “New item”
  *	Select multibranch pipeline then select ok
  *	Enter a display name & brief description
      -	Display Name: Build Flask
      - Description: CI/CD pipeline deployment 1
  *	Under Branch Sources, select Add Source and select GitHub
 

![Picture15](https://user-images.githubusercontent.com/91057035/188270878-a130078f-29ea-424f-854a-f633a4b68563.png)

 
The Jenkins console window will change
  *	Select Jenkins

 
 ![Picture16](https://user-images.githubusercontent.com/91057035/188270889-bd34678f-37b9-4a40-8a37-7d562c338d87.png)



o	In the middle of the page, 
  * Username: enter your GitHub username
  *	Password: enter the token
  *	Then select save


![Picture17](https://user-images.githubusercontent.com/91057035/188270963-5d30e126-431e-44bd-b0e3-180f32325388.png)

 
o	Under Repository HTTPS URL
  * Provide the GitHub repository URL and press validate 
      - You will see output to confirm the repo URL


 ![Picture18](https://user-images.githubusercontent.com/91057035/188270979-00f7c8b4-bc54-4582-ae22-4ebfe6892026.png)


	**IMPORTANT! PLEASE BE SURE BUILD CONFIGURATION is consistent with the below screenshot **
 
	
![Picture19](https://user-images.githubusercontent.com/91057035/188271005-3b1682ea-f009-4178-854e-22e74fef920c.png)


  * Select Apply then select Save
  *	Immediately, a build will be triggered. If no build is in progress, select “Scan Repository”

 
![Picture20](https://user-images.githubusercontent.com/91057035/188271031-53afe892-0920-4bb4-b97f-a2ce01dcda2b.png)
	

If the build fails, the result will show. In this case, I test the application locally using a virtual environment to ensure the application was functional. 
Jenkins is used to build and test software applications. This process makes tasks easier for developers to integrate or update projects. Jenkins automating task will save time also increase business productivity.


# **Step3: Continuous Delivery**
  
The application has been built, tested and validated via Jenkins (running on an EC2 instance). Now, delivering the application to an environment is next. The service that will be used is AWS Elastic Beanstalk.
  
AWS Elastic Beanstalk is an easy-to-use platform/service offered by AWS to deploy applications. The process is very simple, upload the code and Elastic Beanstalk will take care of the rest.
o	Prepare the application file to be upload to AWS Elastic Beanstalk.
  *	Clone a copy of the GitHub Deployment 1 repo. This step was completed after forking the repository to my GitHub profile.
  *	Compress the files within the repository into a .zip file. If using git, use the following command:

	git archive -v -o <cclmyapp>.zip --format=zip HEAD


The above command git archive only includes files stored in git. The command will exclude ignored files and git files.


![Picture21](https://user-images.githubusercontent.com/91057035/188271083-737279e2-380d-46dc-ad32-8592b5e85101.png)

	
o	Navigate to AWS Elastic Beanstalk
  *	On the left panel, select Environments
       - Please be sure Environments is selected. (NOT Applications)
       - Select Create a new environment
       - A new page will appear, choose Web server environment then click Select
  *	Enter the following configurations in the appropriate fields
       - Application name: url-shortner
       - Environment name: Urlshortner-env
       - Platform: Python
       - Platform branch: 3.8
       - Platform version: 3.3.17 (recommended)
       - Application code: Select upload you code

    (Upload the compress file which will serve as code)
  
  * Select Create environment
 
	
![Picture22](https://user-images.githubusercontent.com/91057035/188271104-bfee6e3f-f8e7-4975-8909-a01fd6e01cde.png)

	
![Picture23](https://user-images.githubusercontent.com/91057035/188271135-e20b9c55-e891-48b2-8bac-3e28b2543945.png)


•	Creating the environment and deploying the application will take several minutes. Updates will appear on in the Elastic Beanstalk console as it completes.

 
![Picture24](https://user-images.githubusercontent.com/91057035/188271153-a7947681-bab6-4a81-bde2-141c8fc8fa19.png)
	

![Picture25](https://user-images.githubusercontent.com/91057035/188271182-32bbb9c0-f265-4035-b09c-c5a19aba8768.png)

	

# **Project Overview:**
	
This deployment was fun and exciting. I truly enjoyed building this CI/CD pipeline. All the different systems working together to achieve a goal, intrigues me. 
I did not have many errors completing this deployment the first time through. I looked over what needed to be executed and prepare an outline. Two parts slowed me down a tad. 1- connecting Jenkins to GitHub. For some reason, I forgot my username. I changed it sometime ago and I always revert to my origin GitHub username. (very minor hiccup) 2- When creating the environment in Elastic Beanstalk, I would select Environments (in the left panel) but Applications continued to be selected. I was in my virtual machine and that could have been the issue. So, I cleared my cache, restarted Firefox and that fix that issue.

3 way I would automate this CI/CD pipeline is:
  
   1- Create the AWS EC2 instance via Python or Terraform 
  
   2- Configure a GitHub to Jenkins webhook to move code to be tested 
  
   3- Utilize the AWS Elastic Beanstalk publisher Jenkins plugin to configure a conditional and continuous post-build action to deploy into AWS Elastic Beanstalk




