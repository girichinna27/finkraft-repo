# ONLINE TEST - FINKRAFT

## My public Git repo details:
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
	*`chmod 600 finkraft-keypair.pem`* 

3. Run the following command from your terminal to connect to EC2 instance:
   `$ ssh -i "finkraft-keypair-new.pem.pem" ubuntu@ec2-13-49-245-183.eu-north-1.compute.amazonaws.com`


## Note: 
I had given load to the server for testing the auto-scaling, it's working as expected. See the attached screenshot for reference:
Command for load:
## `stress --cpu 4 --timeout 60`


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
