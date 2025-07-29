# Week 0 - Assignment 0

## Concepts

### Note1

| Feature           | Hub                                 | Bridge                                  | Switch                                     | Router                                       |
| :---------------- | :---------------------------------- | :-------------------------------------- | :----------------------------------------- | :------------------------------------------- |
| **OSI Layer** | Layer 1 (Physical)                  | Layer 2 (Data Link)                     | Layer 2 (Data Link) (some are Layer 3/Multi-layer) | Layer 3 (Network)                            |
| **Functionality** | Connects multiple devices within a LAN; broadcasts all incoming data to all ports. | Connects two LAN segments; filters traffic based on MAC addresses. | Connects multiple devices within a LAN; intelligently forwards data to specific destination based on MAC addresses. | Connects different networks (LANs, WANs); routes data based on IP addresses; performs inter-network communication. |
| **Data Forwarding** | Broadcasts data to all ports        | Forwards data to specific segment based on MAC address. | Unicasts data to the intended destination (after learning MAC addresses). | Routes data packets between different networks based on IP addresses. |
| **Addressing** | No addressing intelligence; operates on raw bits. | Uses MAC addresses for filtering and forwarding. | Uses MAC addresses for intelligent forwarding; maintains a MAC address table. | Uses IP addresses for routing; maintains a routing table. |
| **Logical Addressing System** | **Not Applicable:** Does not understand or use logical (IP) addresses. Operates purely on electrical signals. | **Not Applicable:** Does not understand or use logical (IP) addresses. Primarily uses MAC addresses. | **Not Applicable for Core Function:** Its primary function uses MAC addresses. **Applicable for Layer 3 Switches:** Layer 3 switches *can* use IP addresses for routing functions. | **Applicable:** Fundamentally relies on logical (IP) addresses to route traffic between different networks. |
| **Collision Domain** | Single collision domain for all ports. | Divides collision domains (each segment is a separate collision domain). | Each port is its own collision domain.      | Each port is its own collision domain and broadcast domain. |
| **Broadcast Domain** | Single broadcast domain for all ports. | Single broadcast domain (forwards broadcasts between connected segments). | Single broadcast domain (forwards broadcasts to all ports within its broadcast domain). | Divides broadcast domains (each network connected to a router port is a separate broadcast domain). |
| **Duplex Mode** | Half-duplex                         | Half-duplex                             | Full-duplex                                | Full-duplex                                  |
| **Intelligence** | "Dumb" device; no filtering or intelligence. | More intelligent than a hub; can filter traffic. | Intelligent device; learns MAC addresses; efficient forwarding. | Highly intelligent device; determines best path for data; connects dissimilar networks. |
| **Bandwidth** | Shared among all connected devices. | Shared within connected segments.       | Dedicated to each port.                    | Manages bandwidth across connected networks. |
| **Cost** | Lowest                              | Low                                     | Moderate                                   | Highest                                      |
| **Common Use** | Obsolete in modern networks; very basic small LANs (rarely used now). | Segmenting small LANs; connecting two similar LANs. | Modern LANs, enterprise networks, data centers. | Connecting LANs to WANs (e.g., Internet), connecting different subnets, network security. |

### Note 2

| Port Range          | Name (Common Alias)        | Description                                                  | Access/Usage                                          | Examples of Protocols/Services (Common)                  |
| :------------------ | :------------------------- | :----------------------------------------------------------- | :---------------------------------------------------- | :------------------------------------------------------- |
| **0 - 1023** | **Well-Known Ports** | These ports are reserved for common, widely used, and standardized network services. They are assigned by IANA. | Typically require **administrative/root privileges** to bind to or listen on, due to their critical nature. Used by servers to offer public services. | FTP, SSH, Telnet, SMTP, DNS, HTTP, POP3, IMAP, HTTPS, RDP |

-----

**Detailed Examples of Common Well-Known (System) Ports:**

| Port Number | Protocol/Service | Description                                                | Common Use Case                                            |
| :---------- | :--------------- | :--------------------------------------------------------- | :--------------------------------------------------------- |
| **20** | FTP (Data)       | File Transfer Protocol - Used for data transfer.           | Transferring files between a client and a server.          |
| **21** | FTP (Control)    | File Transfer Protocol - Used for control commands.        | Initiating and managing file transfers.                    |
| **22** | SSH              | Secure Shell - Secure remote command-line access.          | Securely accessing remote servers, file transfers (SFTP).  |
| **23** | Telnet           | Telecommunication Network - Unencrypted remote command-line access. | Historically used for remote access; largely replaced by SSH due to security. |
| **25** | SMTP             | Simple Mail Transfer Protocol - Sending email.             | Mail servers communicating to send emails.                 |
| **53** | DNS              | Domain Name System - Translates domain names to IP addresses. | Resolving website names (e.g., https://www.google.com/search?q=google.com) to IP addresses. |
| **67** | DHCP (Server)    | Dynamic Host Configuration Protocol - Assigns IP addresses to clients. | A server providing IP configurations to network devices.    |
| **68** | DHCP (Client)    | Dynamic Host Configuration Protocol - Client requests IP.  | A device requesting an IP address from a DHCP server.      |
| **69** | TFTP             | Trivial File Transfer Protocol - Simple file transfer.     | Booting diskless workstations, transferring configuration files. |
| **80** | HTTP             | Hypertext Transfer Protocol - Unencrypted web traffic.     | Accessing websites (e.g., Browse a non-secure site).     |
| **110** | POP3             | Post Office Protocol version 3 - Retrieving email from a server. | Downloading emails from a mail server to a local client.    |
| **123** | NTP              | Network Time Protocol - Synchronizing computer clocks.     | Ensuring accurate time across networks and devices.        |
| **137** | NetBIOS (NS)     | NetBIOS Name Service - Name resolution for NetBIOS.        | Used for name resolution in older Windows networks.        |
| **138** | NetBIOS (DGM)    | NetBIOS Datagram Service - Datagram distribution.          | Used for datagram communication in older Windows networks. |
| **139** | NetBIOS (SSN)    | NetBIOS Session Service - Session-based communication.     | Used for session communication in older Windows networks (e.g., file sharing). |
| **143** | IMAP             | Internet Message Access Protocol - Managing email on a server. | Accessing and managing emails directly on the mail server.  |
| **161** | SNMP             | Simple Network Management Protocol - Network device management. | Monitoring and managing network devices (routers, switches). |
| **162** | SNMP Trap        | SNMP Traps - Alerts from network devices.                  | Devices sending alerts to a management station.            |
| **389** | LDAP             | Lightweight Directory Access Protocol - Directory services. | Accessing and managing user accounts, network resources in directories (e.g., Active Directory). |
| **443** | HTTPS            | Hypertext Transfer Protocol Secure - Encrypted web traffic. | Securely accessing websites (e.g., online banking, shopping). |
| **445** | SMB/CIFS         | Server Message Block / Common Internet File System - File sharing, printer sharing. | Windows file and printer sharing.                          |
| **3389** | RDP              | Remote Desktop Protocol - Remote desktop access.           | Accessing and controlling a Windows computer remotely.     |


### Note 3

The concept of IP address classes (Class A, B, C, D, E) is part of a historical addressing scheme for IPv4, known as **Classful Addressing**. While it was fundamental to the internet's early design, it has largely been superseded by **Classless Inter-Domain Routing (CIDR)** due to the inefficiencies and limitations of classful addressing, especially concerning the exhaustion of IPv4 addresses.

However, understanding IP address classes is still important for historical context, for older networks that might still use this system, and as a foundational concept in networking education.

Here are the different types of IPv4 address classes:

### IPv4 Address Classes (Classful Addressing)

IPv4 addresses are 32-bit numbers, typically represented in dotted-decimal notation (e.g., 192.168.1.1). These addresses are divided into two main parts: a **Network ID** (NetID) and a **Host ID** (HostID). The class of an IP address is determined by the value of its **first octet** (the first 8 bits).

| Class | First Octet Range (Decimal) | Leading Bits (Binary) | Default Subnet Mask | Network Bits (N) | Host Bits (H) | Number of Networks (approx.) | Number of Hosts per Network (approx.) | Purpose / Use Cases                                             |
| :---- | :-------------------------- | :-------------------- | :------------------ | :--------------- | :-------------- | :--------------------------- | :------------------------------------ | :-------------------------------------------------------------- |
| **A** | 1 - 126                     | `0`xxxxxxx            | 255.0.0.0           | 8                | 24              | 126                          | 16,777,214                    | Large organizations with many hosts.                                    |
| **B** | 128 - 191                   | `10`xxxxxx            | 255.255.0.0         | 16               | 16              | 16,384                       | 65,534                        | Medium to large organizations, universities.                             |
| **C** | 192 - 223                   | `110`xxxxx            | 255.255.255.0       | 24               | 8               | 2,097,152                    | 254                           | Small local area networks (LANs) with few hosts.                      |
| **D** | 224 - 239                   | `1110`xxxx            | Not Defined         | Not Applicable   | Not Applicable  | Not Applicable               | Not Applicable                | Reserved for **Multicast** communication (one-to-many communication, e.g., video conferencing). |
| **E** | 240 - 255                   | `1111`xxxx            | Not Defined         | Not Applicable   | Not Applicable  | Not Applicable               | Not Applicable                | Reserved for **Experimental** purposes and future use. Not used on the public internet. |

---

### Key Points about IP Address Classes:

* **Network ID vs. Host ID:**
    * The **Network ID** identifies the specific network to which a host belongs. All devices on the same network must have the same Network ID.
    * The **Host ID** uniquely identifies a specific device (host) within that network.
* **Default Subnet Mask:** Each class (A, B, C) has a predefined "default subnet mask" that implicitly defines the boundary between the network and host portions of the address.
* **Limitations of Classful Addressing:**
    * **Inefficient Address Utilization:** Classful addressing led to significant wastage of IP addresses. For example, a Class B network, if assigned to an organization that only needed a few thousand hosts, would still consume over 65,000 host addresses, with tens of thousands going unused.
    * **Rigid Network Sizes:** The fixed sizes of Network and Host IDs (8/24, 16/16, 24/8 bits) often didn't match the actual needs of organizations, leading to either too many unused addresses or a shortage of addresses for larger networks.
    * **Routing Table Bloat:** The large number of independent classful networks resulted in very large routing tables on Internet routers.

### Transition to CIDR

Due to these limitations, the internet community moved away from classful addressing in the early 1990s and adopted **Classless Inter-Domain Routing (CIDR)**.

* **CIDR (Classless Inter-Domain Routing):** Instead of fixed classes, CIDR uses a variable-length subnet mask (VLM) denoted by a `/` (slash) followed by the number of bits in the network portion (e.g., `192.168.1.0/24`). This allows for much more flexible and efficient allocation of IP address blocks, regardless of the traditional class boundaries.
* **No Implicit Classes:** With CIDR, the concept of "classes" A, B, and C is largely irrelevant for routing decisions. The subnet mask explicitly defines the network portion.

While CIDR is the standard today, understanding classful IP addressing provides valuable context for how network addressing evolved and the challenges it aimed to solve.


The key to figuring this out is to **look only at the first octet (the first number) of the IP address** and compare it to the ranges defined for each class.

Let's break down how to determine the class for any given IPv4 address using the first octet:

**Recall the First Octet Ranges for Each Class:**

* **Class A:** First octet is between **1 and 126**
* **Class B:** First octet is between **128 and 191**
* **Class C:** First octet is between **192 and 223**
* **Class D:** First octet is between **224 and 239** (Multicast)
* **Class E:** First octet is between **240 and 255** (Experimental/Reserved)

**Important Note:** The numbers 0, 127, and 255 have special meanings and are not typically part of the assignable ranges for standard network IDs.
* **0.0.0.0:** Default route or a non-specific address.
* **127.0.0.1 (and the entire 127.0.0.0/8 range):** Reserved for the **loopback address** (used for testing network interfaces on the local machine).
* **255.255.255.255:** Broadcast address.

---

**Let's try some examples. Tell me an IP address, and I'll tell you its class and why.**

**Example 1:**
IP Address: `10.50.12.3`

* **First Octet:** `10`
* **Check Range:** `10` falls between `1` and `126`.
* **Conclusion:** This is a **Class A** IP address.

**Example 2:**
IP Address: `172.20.1.50`

* **First Octet:** `172`
* **Check Range:** `172` falls between `128` and `191`.
* **Conclusion:** This is a **Class B** IP address.

**Example 3:**
IP Address: `192.168.0.100`

* **First Octet:** `192`
* **Check Range:** `192` falls between `192` and `223`.
* **Conclusion:** This is a **Class C** IP address.

**Example 4:**
IP Address: `230.1.2.3`

* **First Octet:** `230`
* **Check Range:** `230` falls between `224` and `239`.
* **Conclusion:** This is a **Class D** (Multicast) IP address.

**Example 5:**
IP Address: `250.250.250.250`

* **First Octet:** `250`
* **Check Range:** `250` falls between `240` and `255`.
* **Conclusion:** This is a **Class E** (Experimental/Reserved) IP address.

---

**To help you, focus on these steps:**

1.  **Identify the first number** in the IP address (before the first dot).
2.  **Compare that number** to the range for Class A, then Class B, then Class C, and so on.
3.  **The first range it fits into** determines its class.
