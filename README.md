# ONLINE TEST - FINKRAFT

## My public Git repo details:      ### First comment
https://github.com/girichinna27/finkraft-repo.git

This repo contains 4 main files:
1. requirements.txt  ### Contains the required tools for python linting
2. app.py 		### Main web application
3. test_app.py  ### Test cases application
4. ~/.github/workflows/python.yml   ####Configured a Github actions workflow file to trigger for every commit to my git repo

- To test this web application - We need to trigger the Github actions workflow (https://github.com/girichinna27/finkraft-repo/actions/workflows/python.yml) manually or if we make any commits to the above repo - workflow automatically triggers and Deploy the web application; If we access it(http://13.49.245.183:5000/), it will print the "Hello World" message on browser window:

- You can monitor the each stage (Linting, Testing and Deploying) status:

- We can access my web application by using url: http://13.49.245.183:5000/    ### It will print "Hello World" message on browser window



## To connect to my EC2 instance follow this steps:
1. Download the .pem file from my email / git repo & change the permissions to the .pem file as follows:
	i) Open your terminal & go to the location of .pem file
	ii) Run the following command to set the required permissions:
	*`chmod 600 finkraft-keypair-new.pem.pem`* 

3. Run the following command from your terminal to connect to EC2 instance:
   `$ ssh -i "finkraft-keypair-new.pem.pem" ubuntu@ec2-13-49-245-183.eu-north-1.compute.amazonaws.com`


## Note: 
I had given load to the server for testing the auto-scaling, it's working as expected.
Command for load:
## `stress --cpu 4 --timeout 60`    ### Run this command from EC2 instance terminal


# For manual Auto scaling - There are 2 ways:
## Method-1: Using the AWS Management Console:
- Open the **Auto Scaling Groups** Page:
- Navigate to the **Auto Scaling Groups** page.
- Select the **Auto Scaling Group**:
- Click on the name of the Auto Scaling group you want to adjust.
- Adjust the **Desired Capacity**:

- In the Auto Scaling group details, locate the "**Desired capacity**" field.
- Click on "**Edit**" and change the desired capacity to the desired number of instances.
- Apply Changes:
- Click on "**Save**" to apply the changes.

## Method-2: Using the AWS CLI:
- Open a Command Line Interface:
- Open your preferred terminal or command prompt.
- Set the Desired Capacity:
- Use the update-auto-scaling-group command to set the desired capacity of your Auto Scaling group.
- {::comment}
// Replace <AutoScalingGroupName> with the name of your Auto Scaling group and <DesiredCapacity> with the desired number of instances.
{:/comment}
- `$ aws configure set aws_access_key_id AKIAT3JIFM5XREWHVO6P`
- `$ aws configure set aws_secret_access_key 731xgQljvSuNIowawX9DBeedvtbo5ArfxiUVOHfq`
- `aws configure set region eu-north-1  # Set your AWS region`
	`aws autoscaling update-auto-scaling-group --auto-scaling-group-name <AutoScalingGroupName> --desired-capacity <DesiredCapacity> 
- Verify the Change:`
- You can confirm that the changes were applied by checking the Auto Scaling group details in the AWS Management Console.


## Limitations:
1. In case application deployment failed due to port is already in use - We need to stop the exiting runs from the EC2 instance console:
	For eg: 
	`$ lsof -t -i:5000   ### Get the list of process-id's running on port: 5000`
	   4742
	   4936

	### Kill all the process running on port: 5000 by running the sudo kill command - for eg:
		`ubuntu@ip-172-31-22-138:~$ `sudo kill -9 4742 4936`
		
	Make sure you don't have any process id running on port number 5000
		`ubuntu@ip-172-31-22-138:~$ `lsof -t -i:5000`

2. For any reason if my ec2 instance url or public ip changes - We need to get the latest IP address (Please contact me for these kind of issues, I can resolve quickly) - No time to allocate static IP for my instance. So whenever the EC2 instance restarts IP address will get change
