# Django-AWS
How to deploy a Django Project on AWS


## AWS
Amazon Web Services, AWS is in general a Infrastructure-As-A-Service (IAAS), in contrast to e.g. Heroku, which is a Platform-As-A-Service (PAAS). IAAS allows you to choose yourself the architecture of your infrastructure and has
many well tested products which you can include in your project. The disadvantage of IAAS is that you need to manage your infrastructure yourself.

## Creating an AWS account
When it is the first time that you create an AWS you are automatically inscribed for the free tier. You will need to
provide a credit card credential.

## Amazon EC2 - Elastic Compute Cloud = ECC = EC2
An Ec2 is a scalable web service, which you can use to serve files from the cloud.
You can either use a
- pre-configured, templated Amazon Machine Image (AMI), preconfigured with Python and Django
OR
- a plain EC2 instance where you only choose the operating system.

__How much will you be paying for ?__
There are  a lot of options, which make it quite complicated, depending on the Region and which servers you use it
changes the pricing [amazon ec2 pricing](https://aws.amazon.com/ec2/pricing/).
Rule of thumb: In order to estimate the monthly price for an EC2 instance you can calculate it by multiplying the hourly price by __730__.  

__hourly price__ * __730__  

You should stick to using Micro - as you can easily scale up later. The cheapest price is for reserved instances but you will also be fixed with the instance in a 1/3 year contract.


## Launching a PreConfigured Django Server  
Login to AWS. Select EC2. On your Dashboard you can see how many running instances you have.
You are prompted with the possibility to use an Amazon Machine Image - a preconfigured machine with different environments.

Choose AWS Marketplace, which has 3rd Party AMIs with a configuration including Django !
- Check that the 3rd party is trustworthy, Bitnami is trustworthy.
- Make sure to use a t2.micro instance
- Next: Configure Instance Details
  - Stopping an Instance will release its IP Address, but you will not be charged for the instance and you can start it up later again.
  - Terminating a server removes the instance completely from your dashboard
- Next add Storage - keep it to default to stick to free tier
- Next: Add Tag - "Main site" for example.
- Next: Configure Security Group
  - for now leave it to default
- Launch the Server
  - create a new key pair
  - or reuse the old one
- Test that your instance is working. Copy the IP address and look it up with your browser.
- Django server is up and running =D

## How to setup a plain Ubuntu EC2 Server with Django

- Set up a plain Ubuntu server - use same settings as previously described.
- fire up a terminal / git bash / powershell and navigate to your key
- check on your ec2 dashboard the instance you want to connect to and press "Connect"
- copy the ssh command (something similar to this):
````
ssh -i "my_secret_key_aws.pem" ubuntu@ec2-XX-XXX-XXX-X.eu-central-1.compute.amazonaws.com
````
- confirm
- you should be connected with your instance !! =D


_to be continued ... _
