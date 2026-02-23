# Computer Networks 23 | Congestion Control in TCP

* This topic is very important for GATE
* We will study this in depth

## Window size or Advertising window(16 bit)
* Used for flow control
* TCP is a full duplex connection
  * For understanding we are using half duplex connection

![alt text](image-668.png)


* Sender will not send data more than the capacity of receivers advertised window

## TCP Congestion control

![alt text](image-669.png)

**MSS - Maximum segement size** is 1 KB of the network

Receiver can receive 1024 segments  
So sender will send 1024 segment in the network.  

Router has buffer space. If router doesn't have space it will discard.
So no acknowledgement will NOT be sent by receiver. 

Sender will again send after time-out timer. And more Retransmission means more traffic.

And a situation may come whole network will collapse.

Sender doesn't know why packets are discarded because they both agreed upon receiving 1024 segments.

So before 1980's topic congestion control wasn't present.

Sender was confused why no acknowledgement

**After research, it was concluded network was discarding the packet** and not the receiver.
It was found by Scientist - 1980's  

**Now look in Network capacity also.**

At present - **Window sender size**  

**Ws = min{Network capacity, Receiver Capacity}**

but how sender will know network capacity? It knows receiver's capcity by advertised window send by reciever. 


There is not any general forumula for network capacity as it is dynamic.

**Ws = min{Wc, Wr}**  

So we have a concept of **congestion window for the network**  

## TCP Congestion Control

**An Internet** is a combination of networks and connecting devices (e.g., routers). A packet from a sender may pass through several routers before reaching its final destination. A router has a buffer that stores the incoming packets, processes them, and forwards them.   
If a router the receives packets faster than it can process, congestion might occur and some packets could be dropped.   
When a packet does not reach the destination, no acknowledgement is sent for it.   
The sender has no choice but to retransmit the lost packet.   
This may create more congestion and more dropping of packets, whic means more retransmission and more congestion.  
A point may be reached in which the whole system collapses and no more data can be sent. **TCP therefore needs to find some way to avoid this situation**

## Congestion Window

In TCP, **the sender's window size** is determined not only by the
receiver but also by congestion in the network.  
The sender has two pieces of information: the receiver-advertised
window size and the congestion window size.   The actual size of the
window is the minimum of these two.  


**Actual window size = minimum (receiver window size, congestion window size)**

**Ws = min{Wc, Wr}**  

Initially I will take Wc = 1

पहले मैं एक पैकेट सेंड करूँगा ।

so Ws = min{1, 1024}  

so Ws = 1  

मतलब नेटवर्क की कैपेसीटी 1 पैकेट को होल्ड करने की है ।

next time , Wc = 2  

and if acknowlegement comes, Ws = 2

again this time I will double Wc = 4  

if acknowlegement comes, again it will double to 8. Exponentially increase करेंगे ।    

![alt text](image-670.png)

और ये कहाँ तक चलेगा । ये चलेगा Threshold तक  

**Threshold is half of receivers capacity** = 512 capacity  

**After threshold it will be additive.****  

Wc = 1,2,4,8, 16, 32, 64, 128, 512, 513, 514, 515, 516, ... 1024, 1024, 1024 ...  

It won't go beyond 1024 as receiver's capacity is 1024.

Analogy -  

![alt text](image-671.png)











