# Wordpress_on_AWS
#1. VPC Setup
Defined the Ip addresses for my VPC
Create a private and public subnets
Created route tables for each subnet


#2. Public and Private Subnet with NAT Gateway
Created a NAT gateway for components in the private subnet to be able to access internet, by connecting it to the public internet gateway


#3. AWS MySQL RDS Setup
Created a Relational Database and created a security group for it, so I can be able to connect to the database from MySQL workbence
This is used to store the Wordpress files


#4. EFS(Elastic File System) Setup for Wordpress files
Created an  EFS
Mounted this EFS unto my instance, but it gave me problems as I did not properly configure my mount target security group to accept NFS inbound traffic


#5. AWS Load balancer
Created a Target group and created ALB so as to distribute the load among multiple instances once I integrate the ALB to the Auto-Scaling group I will be creating


#6. Auto-Scaling Group
First I created an AMI image from the instance in which I installed the wordpress
Then I add the AMI image unto the a template I create, I make sure the VPC, the subnet, and the Security group tallies with the first EC2 Instance
Created an Autoscaling group and made sure to add the newly created template to the autoscaling group, this is to make sure that any new EC2 instance being created is not a fresh instance without any installations, but an EC2 instance that has all settings and installations kept
Made sure to attach the ALB to the Autoscaling group
Made sure my Target Policy to create new instances is set to CPU utilization
