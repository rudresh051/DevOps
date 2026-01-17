# Computer Network 03 | Transport Layer [ UDP and TCP ]

## Topics to be covered
1. Transport Layer Services
2. UDP
3. TCP
4. MSL

## Topic - Syllabus 
**Transport layer** - **flow control** and **congestion control**, UDP, TCP , **sockets**;

Tranport layer communication not possible without sockets  
Process read/write through sockets.

e.g. Consider the below diagram  

![alt text](image-59.png)

* Process P1 is initiating the communication. 
* Two hosts don't communicate. Two hosts process communicate through their sockets.
  * Analogy - Milkman keep the milk in the pot
  * Similary pot is a like buffer to keep the data
  * Analogy - Garbage box kept at a place outside and picked by the van
* Process P1 through sockets transfer the message through sockets to transport layer. And tranport layer encapsulates into segment. Tranport layer decides to make TCP segment or UDP segment. And network layer make IP datagram. 

## Transport Layer
1. Provide **logical communication** between **application processes**(Processes running on different machine)
2. Responsible for **process-to-process**(end-to-end) **communication**(connectivity)
   1. > It is called end-to-end because two process are run on two end machines
3. **Multiplexing** & **Demultiplexing**
   1. > It is a must functionality

![alt text](image-60.png)

option d(it is must categoy funcitonality)

## Two Transport layer Protocols
1. **UDP - User Datagram Protocol**
   1. > Uncontrolled and not structured transmission. It's free protocol
   2. > UDP is a basic protocol
2. **TCP - Transmission control protocol**
   1. > Controlled and structured fashion transmission
   2. > TCP = UDP + Extra services

Note - UDP provide faster communication

![alt text](image-61.png)

DHCP - Used for dynamic IP protocol

These do not use TCP/IP => [OSPF, ICMP, IGMP] gives packet directly to IP  

![alt text](image-62.png)

Telnet is remote login. These days we have better to login into servers.

option - c

![alt text](image-63.png)

![alt text](image-64.png)


