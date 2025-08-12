<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Alexandre St-fort  
**Email:** stforta1@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

### What is Amazon VPC?

A Amazon VPC its a private network (by default) inside your AWS account and is crucial to have when running ec2 instances. Its useful to keep some of the application running in private not in the public and otherwise

### How I used Amazon VPC in this project

I use AWS VPC today to set 2 vpc connected to an internetgateway so it can access the internet using the cloud shell and aws console

### One thing I didn't expect in this project was...

I didnt expect to be so fast setting up a vpc and an internet gateway from the AWS CloudShell with a few command

### This project took me...

i have spent 1 hours on this project

---

## Virtual Private Clouds (VPCs)

VPC are a group of device in the cloud connected together in private not accessible by the public with rules and policie

There was already a default VPC in my account ever since my AWS account was created. This is because some reseources in AWS cant be accisible whitout PVC like ec2 instance and connect resources together.

To set up my VPC, I had to define an IPv4 CIDR block, which is a way to define the number of adress avaible int the network PVC

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-vpc_2facf927)

---

## Subnets

Subnets are section in my private network that share the same policies and rules. Some subnets might be public and some private. There are already subnets existing in my account, one for every  Availability Zones

Once I created my subnet, I enabled auto-assign public IPV4 address This setting makes sure when i create a ec2 instance an ip address is assign within that subnet so that we dont have do to it manually 

The difference between public and private subnets are public can access the internet by examble an frontend web app. For a subnet to be considered public, it has to be connected to a internetgateway (router) like a door to the public internet

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-vpc_157c4219)

---

## Internet gateways

An internet gateways is what connect an public subnet to the public internet its like a bridge between the public internet and my PVC

Attaching an internet gateway to a VPC means allowing the connection to the public internet. If I missed this step the cant communicate to the outside world

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

CloudShell is AWS shell to run code and CLI is the interface to write and manage everything

To set up a VPC or a subnet, you can use the command " aws ec2 create-subnet --vpc-id [VPC-ID] "
 Make sure to avoid errors by includingthe cidr-block " aws ec2 create-subnet --vpc-id [VPC-ID]
--cidr-block X.X.X.X/X "

Compared to using the AWS Console, an advantage of using commands is that you can create a vpc and an internet gateway way faster with a few command An advantage of using the Console is it take less time Overall, I preferred using the cloudshell shell

![Image](http://learn.nextwork.org/thrilled_silver_playful_raspberry/uploads/aws-networks-vpc_9b2465411)

---

---
