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

## Firewall Rules
* Configure Firewall Rules to control traffic going in or out of the network
  * Stateful
  * Each firewall rule has priority(0-65535) assigned to it
  * 0 has highest priorty. 65535 has least priority
  * Default implied rule with lowest priority(65535)
    * Allow all egress
    * Deny all ingress
    * Default rules can't be deleted
    * You can override default rules by defining new rules with priority(0-65534)
    * Default VPC has 4-additional rules with priority 65534
      * Allow incoming traffic from VM instances in same network(default-allow-internal)
      * Allow incoming TCP traffic on port22(SSH) default-allow-ssh

## Firewall Rules - Ingress and Egress Rules
* Ingress Rules - Incoming traffic from outside to GCP targets
* Egress Rules - Outgoing traffic to destination from GCP targets
* Along with each rule, you can also define:
  * Priority - Lower the number, higher the priority
  * Action on match - Allow or Deny traffic
  * Protocol - ex. TCP or Deny traffic
  * Port - which port?
  * Enforcement status - Enable or Disable the rule

## Shard VPC
* Scenario - Your organization has multiple projects. You want resources in different projects to talk to each other?
  * How to allow resources in different projects to talk with internal IPs securely and efficiently?
* Enter **Shared VPC(virtual private cloud)**
  * Created at organization or shared folder level (Access Needed - Shared VPC Admin)
  * Allows VPC network to be shared between projects in same organization
  * Shared VPC contains one host project and multiple service projects
    * Host Project - Contains VPC network
    * Servie Projects - Attached to host projects
* Helps you achieve **separation of concerns**
  * Network administrators responsible for Host projects and Resources users use Service Project

## VPC Peering
* Scenario - How to connect VPC networks across different organizations?
* Enter **VPC Peering**


# Hybrid Cloud
## 1. Cloud VPN
* Cloud VPN - Connect on-premise network to the GCP network
  * Implemented using **IPSec VPN Tunnel**
  * Traffic through internet(public)
  * Traffic encrypted using **Internet Key Exchange** protocol
* Two types of Cloud VPN Solutions
  * HA VPN
  * Classic VPN

## 2. Cloud Interconnect
* High speed physical connection between on-premise and VPC networks
  * Highly available and high throughput
  * Two types of connections possible
    * Dedicated interconnect
    * Partner interconnect
* Data exchange happens through a private network
* (Feature) Supported Google API's and services can be privately accessed from on-premise
* Use only for high bandwidth needs - 
  * For low bandwidth. Cloud VPN is recommended

## Direct Peering
* Connect customer network to google network using network peering
* Not a GCP service
* Not recommended


