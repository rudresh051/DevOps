# Computer Network 26 | TCP Vs UDP | CS & IT

## => Need of UDP
### Why UDP?
1. The application that required one request one reply. TCP is not suitable hence we use UDP
   * Analogy - Asking a time from someone. no need to connection
   * e.g. DNS is one request one reply. 
   * e.g. BOOT & DHCP. This is my mac address, give tell me my IP address
2. Application that required **constant dataflow** TCP is not suitable hence we use UDP.
3. Application that required **multimedia data transfer** can not use TCP hence we use UDP.
   * e.g. watching video on YouTube. In HD video is TCP
4. Application that required **fastness** and then reliability TCP is not suitable, hence we use UDP.
   * If fastness is your first concern.
5. UDP used for management process such as SNMP(simple network management protocol)
6. UDP is used for some **route updating protocol** such as RIP(routing information protocol)
7. For **broadcasting & multicasting application** TCP is not suitable hence we use UDP 
8. UDP is normally used for **interactive real time applications**
9. UDP is suitable for a process with **internal flow error control mechanisms**. For example, the Trivial File Transfer protocol(TFTP) process include flow and error control. It can easily use UDP

## => TCP vs UDP

|TCP|UDP|
|--|--|
|Dynamic Header(20-60 byte)|Fixed Header(8 byte)|
|End to end Flow control|No flow control|
|Error control(checksum mandatory)|No error control(Checksum is optional)|
|Connection-oriented|Connectionless|
|Reliability in delivery of msg|No reliable|
|Sequence Number|No sequence number|
|Ack no.|No ack no.|
|Overhead is high(20-60B)|overhead is less(8 Byte)|
|Keep track of order(sequence)|No order|
|Protocols - HTTP, FTP, SMTP, POP|Protocols - DNS, SNMP, TFTP, NFS, RIP, BOOTP, DHCP, All real time and multimedia protocols|

Note -  Client server application such as DNS uses the services of UDP because a client need to send a short request to server and to receive a quick response from it. The request and response can each fit in one user datagram. Since only one message is exchanged in each direction.

Note - 
A client-server application such as SMTP, which is used in electronic mail, cannot use the services of UDP because a user might send a long e-mail message, which
could include multimedia (images, audio, or video). If the application uses UDP
and the message does not fit in one user datagram, the message must be split by
the application into different user datagrams. Here the connectionless service
may create problems. The user datagrams may arrive and be delivered to the
receiver application out of order. The receiver application may not be able to 
reorder the pieces.