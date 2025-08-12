AWS Cloud Networking Project
A project to create a private network on Amazon Web Services (AWS) using a VPC and connecting it to another VPC with VPC Peering.

🚀 What It Is
This project sets up a cloud network with two separate virtual private clouds (VPCs). Think of a VPC as your own private network in the cloud. The project then uses VPC Peering to connect these two private networks together.

This allows resources in one network to talk to resources in the other network, but without being exposed to the public internet.

✨ Key Parts
VPC: Your own private and isolated network in the cloud. We'll set up two of these.

VPC Peering: A connection between the two VPCs that lets them communicate privately.

🛠️ How to Use It
Create your two VPCs.

Create a peering connection between the two VPCs.

Accept the peering connection.

Update the route tables for each VPC so they know how to send traffic to the other VPC.

🧹 Cleanup
To avoid extra charges, remember to delete the peering connection and then delete both VPCs when you're done.
