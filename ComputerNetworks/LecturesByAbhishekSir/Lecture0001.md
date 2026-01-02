# Computer Network 01 : OSI and TCP/IP Model In One Shot

## Topic - Reference
* Request for Comments(RFC) by Internet Engineering Task Force(IETF)

## Topics to be covered
1. Circuit and Packet Switching
2. TCP/IP Model
3. OSI Model

## Topic : Syllabus
1. Concept of layering - OSI and TCP/IP Protocol Stacks
2. Basics of packet, circuit and virtual circuit switching

## Topic : Switching
* Process to **move data(or packets)** towards destination over the network
* Types of switching techniques - 
  * Circuit Switching
  * Packet Switching

## Topic : Circuit Switching
* **Establishes dedicated circuit** between **sender** and **receiver**, before transmission[over the links of the network]
* Example : Telephone Networks
  * PSTN - Public Switched Telephone network
* Advantage - 
  * **No any congestion occur**, during **data transfer**[**Congestion** may occur during **circuit establishment**]

"All lines of this route are currently busy"

* Disadvantage
  * **Inefficient utilization** of **network resources**
  * **Expensive**
  * e.g. Analogy - A single person drives a whole car for travelling to work  

So to make efficient use of resource we came up with Packet Switching

## Topic - Packet Switching
* No any **established required** between **sender** and **receiver**
* **Store** and **forward** **network**
* Example - **Internet** is a **packet-switched network**

Packet switching analogy - Unreserved coach of train  

* Advantage - 
  * **Efficient utilization** of **network resources**[Lead to **better utilization** of **bandwidth resource**]
  * Inexpensive
* Disadvantage - 
  * **Congestion** may occur **during routing**

* **Packet-switched** network
  * (analogy like road construction before driving a car)
* **TCP/IP** Model (first this one was created by DARPA as we might think OSI model would have created first)
  * It's a model which tells how the communication will happen in the packet-switched network

## Topic - TCP/IP Model
* Internet Protocol Stack[Suite]
* Conceptual Model
* Layered Architecture

OSI is a superset. How the things will operate, design is given in TCP/IP Model. 

* It's a 4-Layer Model
  * Link Layer => Internet Layer => Transport Layer => Application layer
* In Some books 5-Layer is mentioned
  * Physical Layer => Link Layer => Internet Layer => Transport Layer => Application layer
  * Don't go into debate
  * IBM, Xerox, Digital Equipment corporation all started making their own model
  * Then came ISO-OSI org

## Topic - ISO - OSI Model (International Standard Organization)
* Open System Interconnection
* Conceptual Model
* Datagram Network (they renamed it)
  * Packet-switched network
* Seven layer architecture
  * Layer 7 - Application Layer(Host layer)
  * Layer 6 - Presentation Layer(Host layer)
  * Layer 5 - Session Layer(Host layer)
  * Layer 4 - Transport Layer(Host layer)
  * Layer 3 - Network Layer(Media Layer)
  * Layer 2 - Data Link Layer(Media Layer)
  * Layer 1 - Physical Layer(Media Layer)

## Topic - Application Layer
* Network application program(network)
  * e.g. Browser
* Process - Program in execution

## Topic - Port Number
* **Port Number**(16-bit) - Identifier, 2 byte
* Used to Identify a **network process** in a machine
  * Process involved in **Network Communication**
* **Port Number** assigned/managed by **OS**
  * Different with process id(pid)
* Port Number should be unique within a machine
  * two network process running in same host, can not have same port no. at a time
* **Port Number** should be **unique within a machine**
  * **two network process** running in **same host**, **can not have same port no.** at a time
* Analogy - Everyone needs aadhar card. But if someone needs to foreign you need visa. Similarly the Process will be given port number those who require network communication

## Topic - Two Process Communication
* Communication Credentials
  * Source Port No. - 16-Bit
  * Source IPv4 Address - 32-Bit
  * Destination IPv4 Address - 32-Bit
  * Destination Port No. - 16-Bit
    * Destination process will be identified with Port number P2 which is 16 bit
    * But how P2 will know who is sending data ?
      * It will identify by source IP address and it's process running on P1
* Local Port No.

## Topic - Protocol
* **Set of Rules**
* **Define**, **how data is exchanged** between **network processes**

## Application Layer Protocols (GATE Syllabus)
1. DNS - Domain Name System
2. HTTP - Hyper Text Transfer Protocol
3. SMTP - Simple Mail Transfer Protocol
4. FTP - File Transfer Protocol

why so many protocol? 
Analogy - To create PAN card we require different form, similarly for driving licence, voter id, aadhar card. So to deal with different servers we require procedure
* Client(browser) changes it's protocols according to it's needs

## Topic - Protocol Data Unit
* **Protocol Data Unit(PDU)**
  * **Basic Unit exchange**
  * Between **same protocols** of **different machine**
  * If server require SMTP we need to use SMTP, same with other protocols according to our need

* In **"Internet Protocol Suite"(TCP/IP Model)**
  * Application Layer PDU - "**Message**"
* In "**OSI Model**"
  * Application Layer PDU - "**Data**" or "**Message**". Analogy - It's like nickname just to call in general name

So, therefore  
Note - Two **Network processes**, belongs to **different hosts** communicate over network, by exchanging "**messages**"

## Topic - Transport Layer
Two Transport Layer Protocols -  
1. UDP - User Datagram Protocol
   1. Basic Protocol
2. TCP - Transmission Control Protocol
   1. UDP + Extra Services

Analogy - needle and sword

