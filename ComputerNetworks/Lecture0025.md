# Computer Network 25 | UDP | CS & IT |

## Transport layer protocol

Transport layer can be connection oriented or connection less  

* Transport layer
  * TCP (Transmission Control Protocol)
    * connection oriented
  * UDP (User datagram protocol)
    * Connection less


> Important points
1. TCP is reliable process to process delivery of entire message
2. TCP is a connection oriented
3. TCP connection are full duplex and point to point.
4. TCP connection has 3 phases
   1. Connection establishment
   2. Data transfer
   3. Connection termination
5. Each TCP connection is associated with four window
6. TCP uses three way "Handshake" to establish TCP connection.
7. TCP is NOT useful for Broadcasting and Multicasting.
8. TCP Header size is 20 byte but if options are added it will become 60 byte.
9. TCP provide end-to-end error control and flow control
10. Data will be received at the destination in order.

## Out of order segment

TCP implements **today do not discard out of order segment**.They store them temporarily and flag them as out of order until the missing segment arrive.
Note, however, that out of order segment never delivered to process.
**TCP guarantee that data are delivered to the process In order**  

**NOTE** - 
Data may arrive out of order and be temporarily stored by receiving TCP, but TCP guarantee that No out of data delivered to the process

## UDP
1. UDP is message oriented connection less Datagram protocol.
2. It is unreliable tranport protocol
3. It does not provide flow control and error control & congestion control
4. It does not add anything to the services except process to process delivery of data.
5. Header is simple and fixed in size i.e. 8 byte

## => UDE Header

![alt text](image-689.png)






