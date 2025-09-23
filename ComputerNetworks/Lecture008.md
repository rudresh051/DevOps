# Classless Addressing

Classless addressing in computer networks is a way of assigning **IP addresses without being restricted to the traditional classful system (Class A, B, C, D, E)**.

In the older **classful addressing** system:

* IP addresses were divided into fixed classes (A, B, C).
* Each class had a fixed size network portion and host portion.
* Example:

  * Class A → 8 bits network + 24 bits host (supports \~16 million hosts per network).
  * Class B → 16 bits network + 16 bits host.
  * Class C → 24 bits network + 8 bits host.

The problem:

* **Wastage of IP addresses** — e.g., an organization needing 2000 IPs could not use Class C (too small, 254 hosts) and had to take Class B (65,534 hosts), wasting most of them.

---

### **Classless Addressing (CIDR – Classless Inter-Domain Routing)**

* Introduced in **1993** to replace classful addressing.
* Uses the format:

  ```
  IP_address / prefix_length
  ```

  where `prefix_length` = number of bits in the **network ID**.
* Example:

  * `192.168.10.0/20` → first 20 bits are the network, remaining 12 bits are for hosts.

This gives flexibility:

* Networks can be **divided into variable-length subnets** (VLSM – Variable Length Subnet Masking).
* IP space can be allocated more efficiently, reducing wastage.

---

✅ **Benefits of Classless Addressing:**

1. Efficient utilization of IP addresses.
2. Supports subnetting and supernetting.
3. Makes routing tables smaller and faster.

---

⚡ Example:

* Organization needs \~2000 IPs.
* With classless addressing, they can be assigned `172.16.0.0/21` → which provides 2048 IPs.
* No need to waste an entire Class B block.


