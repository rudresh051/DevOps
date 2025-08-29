# Networking

## Need for Google Cloud VPC

## Google Cloud VPC(Virtual Private Cloud)

## Need for VPC(Virtual Private Cloud) Subnets
* Different types of resources are created on cloud - databases, compute etc
* How do you **separate public resources from private resources** inside a VPC?
  * Create separate Subnets!
* (Additional Reason) - You want to distribute resources across multiple regions for high availability

## VPC Subnets
* (Solution)**Create different subnets** for public and private resources
  * Resources in a public subnet CAN be accessed from internet
  * Resources in a private subnet CANNOT be accessed from internet
  * But resources in public subnet can talk to resources in private subnet
* Each Subnet is crated in a region
* Example - VPC - demo-vpc => Subnets - region us-central1, europe-west1 or us-west1 or ..

## Creating VPCs and Subnets
* By default, every project has a default VPC
* You can create your own VPCs
* Options when you create a subnet
  * Enable **Private Google Access** - Allows VM's to connect to Google API's using private IP's
* Enable **FlowLogs** - To troubleshoot any VPC related network issues

## Step 03a - Understanding CIDR Blocks
* Resources in a network use continuous IP addresses to make routing easy
* How do you express a **range of addresses** that resources in a network can have?
  * CIDR block
* https://cidr.xyz/


