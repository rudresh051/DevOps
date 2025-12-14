# Computer Networks 04 | Introduction to Subnetting

> Question 6  
> ![alt text](image-44.png)
> Option C - IP address belongs to class B. See the table and limited broadcast address sabka same hota hai.

> Question 7  
> ![alt text](image-38.png)
> Refer Lecture 3 at 33:30 for concept
```
The source ID is invalid IP, because host ID is all 0 in the host octet. Then that IP address cannot be assigned to any computer
```

> Question 8  
> ![alt text](image-39.png)  

```
Explanation - 
We have source IP as - 23.0.0.97
And let's suppose we have destination IP as - 29.3.5.7

And If we reverse in above the SIP and DIP . i.e. Source IP is 29.3.5.7 and Destination IP as 23.0.0.97 then this will also work. so correct option is A

```


> Question 9  
> ![alt text](image-40.png)  

# Classful Addressing
1. Class A - 2^24 IP Addresses in one network
2. Class B - 2^16 IP Addresses in one network
3. Class C - 2^8 IP Addresses in one network



### 1. **Classful Addressing (Old Method)** and **Why Subnetting required**
> Example 1  
>> ![alt text](image-47.png)  

* IPv4 was originally divided into **fixed classes** (A, B, C, D, E).
* Example:

  * Class A → **/8** → 16,777,214 usable hosts
  * Class B → **/16** → 65,534 usable hosts
  * Class C → **/24** → 254 usable hosts

👉 Problem: **Wastage of IPs.**
If an organization needed only 500 IPs, they couldn’t fit in Class C (only 254 hosts), so they had to take a whole Class B (65k hosts). That meant \~64k addresses wasted.

---

### 2. **Subnetting**

* Introduced to **divide large blocks into smaller networks**.
* For example:

  * Instead of using the full **Class B (/16)** = 65k hosts, you could subnet it into smaller chunks, say /24 → 254 hosts each.
* Benefits:

  * **Less wastage** (right-size the subnet to the actual number of hosts).
  * **Better network management** (smaller broadcast domains).
  * **Improved security and routing**.

---

### 3. **CIDR (Classless Inter-Domain Routing)**

* Came **after subnetting** as a more flexible approach.
* CIDR allowed **ignoring the rigid classes** (A, B, C) and just using prefixes like /10, /13, /28, etc.
* This made **IP allocation more efficient** and slowed IPv4 exhaustion.

---

✅ So in order:
**Classful Addressing → Subnetting → CIDR**


> Example -2  
>> ![alt text](image-42.png)  

> Example - 3  
>> ![alt text](image-41.png)

# Subnetting
* Matlab kaafi IP address waste ho jaate the. Isiliye hum subnetting use kar rahe hain.
* Iske baad Subnetting bhi fail hoga. Phir subernetting uske baad hum class less me jaayenge.
* **The process of dividing a big network into many smaller pieces/subnet is nothing but a subnetting.**

![alt text](image-43.png)

**IMPORTANT Note** - **The process of Borrowing bits from Host ID to generate the subnet ID is also called as Subnetting**
* **No of bit borrowed depends on our requirement**
* Let's take an example


> Example 1  
> > ![alt text](image-48.png) 

```txt
I want to create 4 subnets(basically divide that class network in 4 pieces. so to divide how many bits I need to borrow? 2 bits - right? right. Because 2^2 will give 4 combination.)
So out of 8 bits, 2 bit taken borrowed from Host ID. So, first 2 bits will represent subnet ID and 6 bit will be left for Host ID . And with the 2 bit borrowed we will have 2^2 = 4 subnets. 
```

> First Subnet  
>> ![alt text](image-49.png)  
>> ![alt text](image-50.png)  
>> ![alt text](image-51.png)  
>> ![alt text](image-52.png)  
>> ![alt text](image-53.png)  

> Second subnet  
> > ![alt text](image-54.png)  

> 3rd subnet  
> > ![alt text](image-55.png)

> 4th Subnet  
> > ![alt text](image-56.png)  

> Shortcut  
> > ![alt text](image-57.png)  

where SID = Subnet ID and DBA = Directed Broadcast address

> > ![alt text](image-58.png)  

# Homework - Question 2
I want to create 8 subnets. how many bit I have to borrow? 3 bit. Because from 3 bits 8 combination is possible. (basically 8 groups can be made.)
e.g. 
000 => for 1st subnet first 3 bits will be fixed to 000 and remaining 5 bits will vary from all 0's to all 1's  
001 => for 2nd subnet first 3 bits will be fixed to 001 and remaining 5 bits will vary from all 0's to all 1's  
010 => for 3rd subnet first 3 bits will be fixed to 010 and remaining 5 bits will vary from all 0's to all 1's  
011  
100    
101  
110  
111  


![alt text](image-59.png)  
* 8 combination banane ke liye 3 bit chahiye minimum
* ![alt text](image-60.png)

# Question 3 - ISRO exam
* Last 2 bit is used. If we take last 2 bit borrow from host ID, then what is subnet ID and Direct broadcast ID?
* ![alt text](image-61.png)

> ![alt text](image-62.png)  
> ![alt text](image-63.png)  
> Isme IP address sequence me nahi hai. Practically aisa possible nhi hai.  
> ![alt text](image-64.png)


# Subnet Mask
* We saw Network mask. Now let's see subnet mask
* It is a 32 bit number used to indicate no. of bits borrowed from host-id and there positions based on the following rules
* Rule 1 - No of 1's in the subnet mask indicate NID + SID
* Rule 2 - No of 0's in the subnet mask indicate HID part.
* Subnet Mask ka concept kyun aaya? kyunki humne subnet me divide kiya isliye aaya

# Default subnet Mask

![alt text](image-65.png)

![alt text](image-66.png)

# Question 1
![alt text](image-67.png)

![alt text](image-68.png)

![alt text](image-69.png)

![alt text](image-70.png)

# Question 2
![alt text](image-71.png)

# Question 3
![alt text](image-72.png)

![alt text](image-73.png)

![alt text](image-74.png)

# Question 4
![alt text](image-75.png)

# Question 5
![alt text](image-76.png)

![alt text](image-77.png)

# Question 6
![alt text](image-78.png)

![alt text](image-79.png)

# Question 7
![alt text](image-80.png)

# Question 8
![alt text](image-81.png)

![alt text](image-82.png)
Answer - D

# Question 9
![alt text](image-83.png)

# Question 10
![alt text](image-84.png)

# Question 11
![alt text](image-85.png)