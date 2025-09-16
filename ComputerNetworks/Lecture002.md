# Classful Addressing

## 🌍 What is **Classful Addressing**?

Classful addressing was the **original IPv4 addressing system** (1981, RFC 791).
It divided the **32-bit IPv4 space** into **fixed blocks called “classes”** (A, B, C, D, E), based on the **leading bits** of the address.

### Classes:

* **Class A** → For very large networks (few networks, many hosts each)
* **Class B** → For medium-sized networks
* **Class C** → For small networks (many networks, few hosts each)
* **Class D** → Reserved for multicast
* **Class E** → Reserved for experimental

Each class had a **default subnet mask**:

* A → /8 (255.0.0.0)
* B → /16 (255.255.0.0)
* C → /24 (255.255.255.0)

---

## ❓ Why was Classful Addressing done?

At the time (early internet), the goals were **simplicity and manageability**:

1. **Easy to understand** → Just by looking at the **first few bits**, you know if it’s Class A, B, or C.
   Example:

   * `10.x.x.x` → Class B
   * `192.x.x.x` → Class C

2. **Simplified routing** → Routers could decide quickly based on class, without complex subnet lookups.

3. **Matching organization sizes** →

   * Big companies/government → Class A (millions of hosts)
   * Universities/medium ISPs → Class B (65k hosts)
   * Small companies → Class C (254 hosts)

---

## ⚠️ Problem with Classful Addressing

It **wasted a massive amount of IP space**:

* A company might get a whole **Class A (16M IPs)** even if they only needed 1000.
* Small companies often ran out of Class C networks.

By the 1990s, IPv4 was running out of space because of this waste.

---

## ✅ What replaced it?

* In **1993**, **Classless Inter-Domain Routing (CIDR)** was introduced.
* CIDR uses **variable-length subnet masks (VLSM)** — so instead of rigid “classes,” you can allocate **just enough addresses**.
  Example: Instead of giving Class B (65k) to a company, you can give them a **/20 block (4096 IPs)**.

---

👉 **In short:**
Classful addressing was the **first, simple way to divide IPv4 addresses**, but it was too rigid and wasteful. CIDR replaced it to allow finer control and prevent IPv4 exhaustion.


![alt text](image-8.png)
Note -
1. Number of IP Addresses present in class A = 2^31
2. Class B = 2^30
3. Class C = 2^29
4. Class D = 2^28
5. Class E = 2^28

![alt text](image-9.png)

![alt text](image-10.png)

## IP Address Representation
1. dot Binary

e.g. 11001000.11111100.00111111.11110111
convert in dotted decimal  
Weightage - 128,64, 32, 16,8,4,2,1  
200.252.63.247

2. convert in Hexadecimal 

C8:FC:3F:F7

Note - 
1. Whenever we have all zeros or all ones, either in the network ID or in the Host ID of any IP addresses. These IP addresses are reserved for some special purpose, so we cannot assign these IP addresses to computer.

