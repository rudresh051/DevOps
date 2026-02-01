# Load Balancing in Google Cloud Platform

## Cloud Load Balancing
* Distributes user traffic across instances of an application in single region or multiple regions
* **Fully distributed, software defined** managed service
* Important Features - 
  * Health check - Route to healthy instances
    * Recover from failures
  * Auto Scaling
  * Global load balancing with single anycast IP
    * Also supports internal load balancing
* **Enables**
  * High Availability
  * Auto Scaling
  * Resiliency

![alt text](image-108.png)

above is high level view of cloud load balancer

## Understanding HTTP, HTTPS, UDP and TCP Protocols
* Computers use protocols to communicate
* Multiple layers and multiple protocols
* **Network Layer** - Transfer bits and bytes
* **Transport Layer** - Are the bits and bytes tranferred properly
* **Application Layer** - Make REST API calls and Send Emails
* (Remember) Each layer makes use of the layers beneath it
* (Remember) Most applications talk at application layer. But some applications talk at network layer directly(High Performance)

![alt text](image-109.png)

* **Network Layer**
  * IP(Internet Protocol) - Tranfer bytes. Unreliable
* **Transport Layer**
  * TCP(Transmission control) - Reliability > Performance
  * TLS(Transport Layer Security) - Secure TCP
  * UDP(User Datagram Protocol) - Performance > Reliability
* **Application Layer**
  * HTTP(Hypertext Transfer Protocol) - Stateless Request Response Cycle
  * HTTPS - Secure HTTP
    * It secure HTTP communication by having certificates. It uses certificates which are installed on the servers to ensure communication between two system is secure.
  * SMTP - Email Transfer Protocol
  * and a lot of others

![alt text](image-110.png)

What's happening under the hood will help in understanding what's happening what we are going to talk in the next steps.

## Creating a Load Balancer in GCP - Demo | Hands-on



## Load Balancer Scenarios

![alt text](image-16.png)