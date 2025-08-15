**Author:** Alexandre St-fort  
**Email:** stforta1@gmail.com

---

## VPC Peering

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_88727bef)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is your own private or public network inside my AWS cloud region

### How I used Amazon VPC in this project

I uses Amazon VPC today to create to seperate vpc with an ec2 instance in each and settint up a Peering Connection so they can communicate without going to the public internet

### One thing I didn't expect in this project was...

I didn't expect to have to indicate to each vpc in the same region the ipv4 pravate address of the vpc perreing connection

### - Set up my VPC

I created the 2 VPC using 'VPC and more' mode so it can be faster and clearer.

### - Create a Peering Connection

In this step i'm going to create the VPC Peering connections so that there a connection between the two VPC's that enables to route traffic between them using they private IPv6 or IPv4 (in my case) addresses.

### - Update Route Tables

In this step I am going to set a way for traffic comig from VPC 1 to VPC 2 and an other way for traffic coming from VPC 2 to VPC 1

### - Launch EC2 Instances

In this step I launched two EC2 instance in each VPC's public subnet

---

## Multi-VPC Architecture

I started my project by launching 2 VPC's (with there one seperate IPV4 CIDR BLOCK) with one public subnet each.

The CIDR blocks for VPC's 1 and 2 have two different IPv4 CIDR blocks because they have to be unique so that they not overlaping and communicate and exchange data otherwise it can cause conflit and connectivity issues.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as recommanded because with EC2 Instance Connect manage the key pair connection is handled by AWS. When ethablishing a connection a one uses key pair is create with a expiration time

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_11111111)

---

---

## VPC Peering

A VPC peering connections is a networking connection that enable the communucation and allows exchange data between two defferent VPC (they must have 2 different IPv4 or IPv6 CIDR blocks). A VPC pering can be use to connect between VPC either if they are in the same region (in my case) in an other AWS account or in a different Regions.

A VPC peering connections helps the transfert of data directly between 2 or more VPC with private addresses witout the need of using a gateway or vpn conneciont or the public internet. It allows the transfert of data in an private ip address space.

The difference between a Requester and an Accepter in a peering connection is that the requester the Requester is the one sending the connections invatation in a peering connection and the Accepter is the VPC that receive the invitation, can either accepte it or decline it so the receive is the one finishing the connection

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_1cbb1b88)

---

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because they dont know to go to the VPC peering even though they know there's one

My VPCs' new routes have a destination of each other private IPv4 addresses and the routes' target was the VPC peering Connection. Meaning if one instaces want to communicate the other instances in a seperate VPC to flow the traffic to the VPC peering connection

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_4a9e8014)

---


### - Use EC2 Instance Connect

In this step I connecting my ec2 instance that I launch using 'EC2 Instance Connect' in AWS.

### - Connect to EC2 Instance 1

I connect to my ec2

### - Test VPC Peering

I'm testing connectivity between instance 1 to instance 2 using the ping command.


## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to connect to my ec2 instance because i dont have to manage the ssh key AWS does it for me.

I was stopped from using 'EC2 Instance Connect' as my EC2 instance didn't have a public address because by default 'EC2 Instance Connect' connect to the instance using the public internet. 

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static IPv4 address that AWS manage and is allocated to my AWS account so that it can have a public ip address.

Associating an Elastic IP address resolved the error because now AWS can connect to my ec2 instance because it have an ip addrress allocate to it by Elsatic Ip.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

To test VPC peering, I ran the command ping to check if the host (VPC 2s ec2) is up and reachable from its private ip

A successful ping test would validate my VPC peering connection because when pigning a host a requeste ping its send over the network and is the host is up and reachble an icmp echo reply is send back meaning its connected 

I had to update my second EC2 instance's security group because it didnt allow icmp traffic wich ping uses. I added a new rule that allows icmp ping request from VPC CIDR

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_7a29d352)

---

---

# VPC Monitoring with Flow Logs

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_3e1e79a1)

---

### - Set up Logs

Set up a way to track all inbound and outbound network traffic.Set up a space that stores all of these records.

### - Set IAM permissions for Logs

I am going to set up a IAM role policy to give permission to flow log to send data to cloudwatch

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_e7fa8775)

---

## Logs

Logs are files that keep track everything goig on in your systeme from login to errors. It's the go-to place to understand what's going on with your systems, troubleshoot problems, and keep an eye on who’s doing what.

Log groups are like a folder for related resources otherwise they all logs are mixed.

### I also set up a flow log for VPC 1

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_e8398869)

---

## IAM Policy and Roles

I created an IAM policy because by default flows logs do not have the permission  to write logs and send them to CloudWatch.

 I also created an IAM role because services like flow logs have to be associated with a role. It to give only VPC flows log those permission to record and upload logs

A custom trust policy is uses for designing who or what is allows acces to the IAM role

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_4334d777)

---

## In the second part of my project...

### - Ping testing and troubleshooting

I am going to generate network traffic by using the ping command by pigning the instance #2 from instance #1

### - Set up a peering connection

.....

### - Analyze flow logs

I'm going to track the data that have been collected on my VPCs

---

## Connectivity troubleshooting

A ping reponse mean that the host is up and reachable

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_99d4ba42)

I could receive ping replies if I ran the ping test using the other instance's public IP address, which means there communication between the 2 end host using the public internet

---

## Analyzing flow logs

Flow logs tell us about the source, destination, the amount of data transferred, whether the traffic was accepted or rejected.

For example, the flow log I've captured tells us the traffic from 147.185.133.33 to 10.1.11.171 was accepted by the security group and network ACL of my VPC

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_d116818e)

---

## Logs Insights

Logs Insights is a CloudWatch tool that analyzes your logs. Using queries to filter, process and combine data to help you troubleshoot problems or better understand your network traffic.

I ran the query "Return the top 10 byte transfers by source and destination IP addresses". This query analyzes the flow logs collected on EC2 instances and return the top 10 pair of ip addrresses based on the amount of data transfrered between them.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-monitoring_3e1e79a1)

---

---

## Access S3 from a VPC

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-s3_3e1e79a2)

---
### - Set up access keys

I'm going to give my ec2 instance access to my AWS environment but creating an Access key and configure it with 'aws configure'.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-s3_4334d777)

---

## Running CLI commands

AWS CLI is a command-line shell that let you run command that let you interact with you AWS ressources. I have access to AWS CLI because it's pre-installed on ec2 instances.

The first command I ran was 'aws s3 ls'. This command is used to list the s3 bucket in your AWS account.

The second command I ran was 'aws sts get-caller-identity'. This command is used to display credentials of the AWS Account.

The last command I ran was 'aws configure'. This command is used to set up and manage the configuration and credentials required to interact with AWS services.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-s3_e7fa8776)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured by entering my new Access key id with my secret access key using 'aws configure'.

Access keys are credentials used for your applications and other servers to uses your AWS services/resources.

The secret access key is like the password that pairs with your access key ID (username).

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use AWS Cloudshell, a browser-based CLI to run commands.

---

### - Set up an S3 bucket

Launch a bucket from Amazon S3

---

## Connecting to my S3 bucket

The first command I ran was 'aws s3 ls'. This command is used to list the s3 bucket in your AWS account.

When I ran the command 'aws s2 ls' again, the terminal responded by listing all the s3 bucket in my AWS account. This indicated that my ec2 instances is connected to my account.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-s3_4334d778)

---


Another CLI command I ran was 'aws s3 ls s3://bucket-name' which returned the files inside the s3 bucket.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-s3_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command 'sudo touch /tmp/test.txt'. This command creates a new file names test.txt in the tmp folder.

The second command I ran was 'aws s3 ls s3://bucket-name'. This command will upload the new file that i just created to my s3 bucket.

The third command I ran was'aws s3 ls s3://nextwork-vpc-project-yourname' wich validated that the file was succefully uploeaded.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-s3_3e1e79a2)

---

---


## VPC Endpoints

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_09bcaa8a)

---
### - Architecture set up

Create A VPC Endpoint and connecting it to my ec2 instance and my s3 bucket

a voir

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_4334d777)

---
### - Set up a Gateway

Set up a way for your VPC and S3 to communicate direclty.

### - Bucket policies

In this step i'm going to test my VPC endpoint to make sure taht my ec2 do not the public internet to get access to my s3 bucket by denying or blocking all access from the bucket through internet except by my VPC Endpoint.

### - Update route tables

I'm going to see if i can access my s3 bucket through me ec2 instance like my policy is supposed to do.

### - Validate endpoint conection

.....

---

## Setting up a Gateway

I set up an S3 Gateway, wich is a type of endpoint used specifically for Amazon S3 and DynamoDB

### What are endpoints?

An endpoint is a service that allows private connection between AWS services and my VPC.

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_09bcaa8a)

---

## Bucket policies

A bucket policy is a type of IAM policy designed for setting access permissions to an S3 bucket. 

My bucket policy will deny all access from the internet except from my vpc endpoint

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_7316a13d)

---

## Bucket policies

Right after saving my bucket policy, my S3 bucket page showed 'denied access' warnings. This was because my policy made my s3 bucket not accesible from the internet even from  AWS Management Console.

I also had to update my route table because the only ways to access my s3 bucket was by the internet not by my vpc endpoint

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_4ec7821f)

---

## Route table updates

To update my route table, I had to indicate that if my ec2 want to access my s3 bucket it had to go through my vpc endpoint instead.

After updating my public subnet's route table, my terminal could return me the files in my bucket

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_d116818e)

---

## Endpoint policies

An endpoint policy is rules to gives acces or denying access to my AWS services

I updated my endpoint's policy by the 'Effect' from allows to denied I could see the effect of this right away, because i couldn't access my s3 files from my ec2

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_3e1e79a3)

---

---
