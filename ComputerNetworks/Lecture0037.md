# Computer Networks 37 | Medium Access Control Part 01 ( Pure Aloha)

## Topics
* Pure Aloha

## Multiple Access Protocols

Lets take a example

![alt text](image-641.png)

* Data link layer is divided in two - 
  * LLC(Logical Link Control)
    * Error Control
    * Flow control
  * MAC(Medium Access Control)
    * Access Control

![alt text](image-642.png)

## What is Media Access Protocol?
Let's understand this first - 

![alt text](image-643.png)

* Source and destination send data between each other which is dedicated in Point to point. No collision in if it is full duplex.
* Broadcast - We have common channels and many station are connected to it. It is also called shared channel. Basically they can access data.
  * Two stations data can collide at a given time t1 when A and B sends data
* **Access Control** basically means we have to access this link in sach a way there is no problem of collision. 
* We have different way to access such link.
* Solution - At a time only one station should data?
* What if we make slots of time - 10:05 to 10:10 only A will transfer , 10:10 to 10:15 only B will transfer

## Random Access Protocols
* Any station can send data at any time
* All stations have same power here.

1. In Random Access, No station is superior to another station and None is assigned control over another i.e. no station permits or stops other station to send data
2. Any station can send the data whenever it wants.
3. If more than one station tries to send then there is an access conflict collision and the Frames will be either destroyed or modified
4. To Avoid collision station must send data by executing a preocedure or condition defined by the protocol
5. There is not fixed order in which station send data so these are called Random Access Protocols
6. Each station competes for the channed hence these are also known as **Contention methods.**
