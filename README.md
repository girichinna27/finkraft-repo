My public Git repo details:
https://github.com/girichinna27/finkraft.git

1. requirements.txt  ### Contains the required tools for python linting
2. app.py ### Main web application
3. test_app.py  ### Test cases application
4. ~/.github/workflows/python.yml   ####Configured a Github actions workflow file to trigger for every commit to my git repo


We can trigger the Github action workflow by commiting the code or manually  - Open the following url from browser: https://github.com/girichinna27/finkraft/actions/workflows/python.yml 
Click on: Run workflow drop down option and run the workflow - You can monitor the each stage (Linting, Testing and Deploying) status

We can access my web application by using url: http://16.170.172.127:5000/    ### It will print "Hello World" message on browser window


To connect to my EC2 instance follow this steps:
1. Download the .pem file from my email / git repo & change the permissions to the .pem file as follows:
	i) Open your terminal & go to the location of .pem file
	ii) Run the following command to set the required permissions:
		chmod 600 finkraft-keypair.pem 

2. Run the following command from your terminal to connect to EC2 instance
	$ ssh -i "finkraft-keypair.pem" ubuntu@ec2-51-20-184-200.eu-north-1.compute.amazonaws.com

3. There you can see different files required to run the given python web application






For manual Auto scaling - There are 2 ways:
1. We can open AWS EC2 console from browser and can stop the EC2 instance

OR

2. We can execute the following commands to shutdown the instance:
	i) Run the following commands from terminal
		$ aws configure set aws_access_key_id AKIAT3JIFM5XREWHVO6P
		$ aws configure set aws_secret_access_key 731xgQljvSuNIowawX9DBeedvtbo5ArfxiUVOHfq
		$ aws configure set region eu-north-1  # Set your AWS region


