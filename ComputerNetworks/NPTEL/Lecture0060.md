# Lecture 60 : Network Security-III[TCP/IPSecurity]

> Today we will talk about TCP/IP security

## Common Structure of security Protocols

![alt text](image-49.png)

## IPSecurity(IPSec)

![alt text](image-50.png)

## IPSec - Transport mode and Tunnel Modes

![alt text](image-51.png)

### Transport mode

![alt text](image-52.png)

### Tunel mode

![alt text](image-53.png)

## IPSec services

![alt text](image-54.png)

## Transport Layer Security - SSL/TLS

![alt text](image-55.png)

### Four SSL Protocols

![alt text](image-56.png)

## Application Layer Security - PGP

![alt text](image-57.png)

### PGP : E-mail message is authenticated and encrypted

![alt text](image-58.png)

## Firewall

![alt text](image-59.png)

* Firewalls are effective to
  - protect local systems;
  - protect network-based security threats;
  - provide secured and controlled access to Internet;
  - provide restricted and controlled access from the Internet to local servers.

## Types of Firewalls

1. Packet filters
2. Application-level gateways/ Proxy Firewall
3. Circuit-level gateways

### Packet Filtering Firewall

![alt text](image-60.png)

![alt text](image-61.png)

- Applies a set of rules to each incoming IP packet and then
forwards or discards the packet.
  - Typically based on IP addresses and port numbers.
- Filter packets going in both directions.
- The packet filter is typically set up as a list of rules based on
matches to fields in the IP or TCP header.
- Two default policies (discard or forward).

- Advantages:
  - Simplicity
  - Transparency to users
  - High speed
- Disadvantages:
  - Difficulty of setting up packet filter rules
  - Lack of authentication

## Application-Level Gateway

![alt text](image-62.png)

![alt text](image-63.png)

![alt text](image-64.png)

![alt text](image-65.png)

## Circuit-Level gateway

![alt text](image-66.png)

![alt text](image-67.png)

![alt text](image-68.png)

## Firewall Configurations
- In addition to the use of simple configuration of a single
system (single packet filtering router or single gateway),
more complex configurations are possible
- Three common configurations are in popular use.

### Screened Host Firewall(Single-homed host)

![alt text](image-69.png)

![alt text](image-70.png)

### Screened Host Firewall(dual-homed host)

![alt text](image-71.png)

- The packet-filtering router is not completely compromised.
- Traffic between the Internet and other hosts on the private network has to flow through the bastion host.

### Screened Subnet Firewall

![alt text](image-72.png)

## Perimeter Defense and Firewall - Typical Scenario

![alt text](image-73.png)