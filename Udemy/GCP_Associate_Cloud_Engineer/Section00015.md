# Block and File Storage in GCP
# Storage
## Storage Types - Block Storage and File Storage
* What is the type of storage of your hard disk?
  * Block storage
* You've created a file share to share a set of files with your colleagues in a
enterprise. What type of storage are you using?
    * File Storage
### Block Storage
* Use case - Harddisks attached to your computers
* Typically, ONE Block storage can be connected to one virtual server



### File Storage
* Media workflows need huge shared
storage for supporting processes like
video editing
* Enterprise users need a quick way to
share files in a secure and organized
way
* These file shares are shared by several
virtual servers

## Persistent Disks vs Local SSDs

|Feature|Persistent Disks|Local SSDs|
|--|--|--|
|Attachment to VM instance|As a network drive|Physicallly attached|
|Lifycycle|Separate from VM instance|Tied with VM instance|
|I/O Speed|Lower(network latency)|10-100X of PDs|
|Snapshots(backups)|Supported|Not Supported|
|Use case|Permanent storage|Ephemeral storage|

## Persistent Disks(pd) - Standard vs Balanced vs SSD
|Feature|Standard|Balanced|SSD|
|--|--|--|--|
|Underlying Storage|Hard Disk Drive|Solid State Drive|Solid State Drive|
|Referred to as|pd-standard|pd-balanced|pd-ssd|
|Performance - Sequential IOPS(Big Data/Batch)|Good|Good|Very Good|
|Performance - Random IOPS(Transactional Apps)|Bad|Good|Very Good|
|Cost|Cheapest|In Between|Expensive|
|Use cases|Big Data(cost efficient)|Balance between cost and performance|High Performance|

## Taking Snapshots for Persistent Disks

## Persistent Disks - Snapshots - Recommendations