<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-peering)

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

### This project took me...

About 2h

---

## In the first part of my project...

### Step 1 - Set up my VPC

I am going to create the 2 VPC using 'VPC and more' mode so it can be faster and clearer.

### Step 2 - Create a Peering Connection

In this step i'm going to create a Peering connections so that there a connection between the two VPC's that enables to route traffic between them using private IPv6 or IPv4 (in my case) addresses.

### Step 3 - Update Route Tables

In this step I am going to set a way for traffic comig from VPC 1 to VPC 2 and an other way for traffic coming from VPC 2 to VPC 1

### Step 4 - Launch EC2 Instances

in this step im going to set up two EC2 instance in each VPC's public subnet

---

## Multi-VPC Architecture

I started my project by launching 2 VPC's (with there one seperate IPV4 CIDR BLOCK) with one public subnet each 

The CIDR blocks for VPC's 1 and 2 have two different IPv4 CIDR blocks because they have to be unique so that they not overlaping and communicate and exchange data otherwise it can cause conflit and connectivity issues.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as recommanded because with EC2 Instance Connect manage the key pair connection is handled by AWS. When ethablishing a connection a one uses key pair is create with a expiration time

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_11111111)

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

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step i'm going to connect to my ec2 instance that I launch using 'EC2 Instance Connect'.

### Step 6 - Connect to EC2 Instance 1

Use EC2 Instance Connect to connect to Instance 1

### Step 7 - Test VPC Peering

I am going to test connectivity between instance 1 to instance 2 using the ping command

---

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to to my ec2 instance with the public internet without the need of managing the ssh key.

I was stopped from using EC2 Instance Connect as my EC2 instance didnt have a public address because by default EC2 Instance Connect connect to the instance using the public internet. 

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static IPv4 address that AWS manage and is allocated to my AWS account so that it can have a public ip address.

Associating an Elastic IP address resolved the error because now AWS can connect to my ec2 instance because it have an ip addrress allocate to it

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

To test VPC peering, I ran the command ping to check if the host (VPC 2s ec2) is up and reachable from its private ip

A successful ping test would validate my VPC peering connection because when pigning a host a requeste ping its send over the network and is the host is up and reachble an icmp echo reply is send back meaning its connected 

I had to update my second EC2 instance's security group because it didnt allow icmp traffic wich ping uses. I added a new rule that allows icmp ping request from VPC CIDR

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-peering_7a29d352)

---

---


<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Endpoints

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-endpoints)

**Author:** Alexandre St-fort  
**Email:** stforta1@gmail.com

---

## VPC Endpoints

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_09bcaa8a)

---

## Introducing Today's Project!

### What is Amazon VPC?

.....

### How I used Amazon VPC in this project

....

### One thing I didn't expect in this project was...

......

### This project took me...

.....

---

## In the first part of my project...

### Step 1 - Architecture set up

Create A VPC Endpoint and connecting it to my ec2 instance and my s3 bucket

### Step 2 - Connect to EC2 instance

.......

### Step 3 - Set up access keys

.........

### Step 4 - Interact with S3 bucket

.......

---

## Architecture set up

......

.....

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_4334d777)

---

## Access keys

### Credentials

.......

........

.........

### Best practice

........

---

## Connecting to my S3 bucket

.........

...........

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_4334d778)

---

## Connecting to my S3 bucket

.......

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_4334d779)

---

## Uploading objects to S3

........

............

..........

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-endpoints_3e1e79a2)

---

## In the second part of my project...

### Step 5 - Set up a Gateway

Set up a way for your VPC and S3 to communicate direclty.

### Step 6 - Bucket policies

In this step i'm going to test my VPC endpoint to make sure taht my ec2 do not the public internet to get access to my s3 bucket by denying or blocking all access from the bucket through internet except by my VPC Endpoint.

### Step 7 - Update route tables

I'm going to see if i can access my s3 bucket through me ec2 instance like my policy is supposed to do.

### Step 8 - Validate endpoint conection

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

