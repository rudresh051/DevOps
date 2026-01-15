# Computer Networks 18 | Selective Repeat Protocol 

## Selective Repeat ARQ

* In GB-N , the efficiency was less. If a packet was lost , then again full window we had to send.  
* Here if a packet is lost in a window, then sender will select that packet and again send that packet.


## Selective Repeat/Selective Reject ARQ(Automatic repeat request)
1. In **SR Protocol** **window sender size** is equal to **window receiver size.**
   1. > Ws = Wr
   2. > GBN we had Ws = N and Wr = 1
2. SR Protocol uses **independent acknowledgement**, and **acknowledgement number** defines **number of error free packet received.**
   1. > GBN used cumulative acknowledgement
   2. > Stop and wait used independent protocol
   3. > In cumulative ack, if GBN-3, Ack would have been four i.e. next expcted packet or frame.
3. **SR receiver** can **receive out of order packet** but **packets are delivered to upper layer in order**
   1. > GB-N never recive out of order packet and there packet was discarded
   2. > At data link layer out of order but at network layer it will be send in order
4. In SR protocol **searching and sorting logic** is required. **Searching is done by sender** and **sorting is done by receiver.**
   1. > Receive can get packets out of order but then it will sort it and then send to network layer in order
5. **Timer is maintained** **for each and every frame in the window at sender size**
   1. > GBN, Timer was maintained for first frame only. only for first packet
   2. > Here 3 packet is lost, then only 3rd packet will be retransmit. If Acknowledgement doesn't come retransmit will be done

Let's take an example to understand -  

![alt text](image-496.png)

![alt text](image-497.png)

Diagram explanation -   

Note -  
1. For **1st out of order** delivery or if packet received is corrupted then **NAK(negative acknowledgement)** for respective packet is sent by receiver to sender.
2. When sender **receive NAK 3** then it will **search in the window for packet 3** & immediately packet 3 is retransmitted even though its **timer is not expired**

## Relationship between window size & sequence number
* Minimum how many sequence required to achieve 100% efficiency
* Very important to understand with diagram

![alt text](image-498.png)

In the above we have problem of duplicate packet, as according to this is also proved

![alt text](image-502.png)

Note -   
1. Duplicate packet problem can be solved by increasing the sequence No. or decreasing the sender window size
2. Duplicate packet problem can be solved by using the following formula

Ws + Wr <= A.S.N(available sequence number)  

![alt text](image-499.png)

![alt text](image-500.png)


![alt text](image-501.png)

So hence we can put a general formula - 

![alt text](image-503.png)

![alt text](image-504.png)

![alt text](image-505.png)

## Efficiency

efficiency = usefultime/total time

In question window size will be given of the frame

![alt text](image-506.png)

## Throughput

Throughput = efficiency * Bandwidth

or  

![alt text](image-507.png)

## Summary - Comparison between stop & wait, GB-N , and SR
 
![alt text](image-508.png)

![alt text](image-509.png)

## Problem solving on SR Protocol

## Question 1
![alt text](image-510.png)

B will be the correct answer

## Question 2
![alt text](image-511.png)

![alt text](image-512.png)

## Question 3

![alt text](image-513.png)

![alt text](image-514.png)

In above question N is the maximum sequence number NOT total sequence number

## Question 4
![alt text](image-515.png)

![alt text](image-516.png)

## Question 5
![alt text](image-517.png)

![alt text](image-518.png)

![alt text](image-519.png)

## Question 6
HW  

![alt text](image-520.png)

## Question 7
![alt text](image-521.png)

![alt text](image-522.png)

![alt text](image-523.png)

![alt text](image-524.png)

## Question 8

![alt text](image-525.png)

![alt text](image-527.png)

![alt text](image-526.png)

![alt text](image-528.png)

## Question 9

![alt text](image-529.png)

above is HW

## Question 10

![alt text](image-530.png)

![alt text](image-531.png)

Take N greater so N = 51

## Question 11

![alt text](image-532.png)

![alt text](image-533.png)

![alt text](image-534.png)

## Question 12
![alt text](image-535.png)






 
