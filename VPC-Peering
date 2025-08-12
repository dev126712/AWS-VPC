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
