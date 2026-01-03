# Computer Network 02 : Application Layer [ DNS, HTTP, Email ] | CS & IT |

# Topics to be covered
1. Application Layer Protocols
2. DNS
3. HTTP => V. Imp
4. Email => SMTP

## Topic - Two Process Communication
Two paradigm -   
1. Client-Server
   1. e.g. Web browsing, Email, Internet chat, Online live classes
2. Peer to peer
   1. e.g. BitTorrent, VoIP(Voice over IP) - 4G(Internet based voice call)
   2. e.g. Skype call
   3. Server can record the call if it want

## Topic - Client-Server Paradigm
* Server -  
  * **Always on** host
  * **Permanent IP Address**
  * Mostly in data centers
* Client - 
  * Communicate(contact) with **server**
  * May have **dynamic IP address**
  * Clients do not communicate directly with each other
    * They have to communicate via a server(Client-Server Architecture)
    * In peer to peer architecture Client can directly communicate.

* Server - Here server serve data. In restaurant waiter serves food
* Example - 
  * **Web browsing**
    * Client - **Web browser**
    * Server - **Web Server**
  * **Email**- 
    * Client - **User Agent**
    * Server - **Mail Server**

**Client-server is nothing but communication. Client process communicates with Server process**

## Topic - Peer - Peer Architecture
* **No always on** server
* Arbitrary **end systems** directly communicate
* **Complex management**(Peers can change IP address)
  * Clients share each other IPs to each other
* e.g. **P2P file sharing**(BitTorrent), Voice over IP(VoIP)
  * Whatsapp privacy feature for IP address 

Q. How two process client-server communicate? - Watch all 18 lectures :) to understand it completely

## Question 
![alt text](image-15.png)

Correct option - d - Ping
Ping is a utility, to check connectivity between either client-client or client-server

