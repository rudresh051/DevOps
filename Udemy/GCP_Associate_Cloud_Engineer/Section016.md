# Object Storage in Google cloud
* Most popular, very flexible & inexpensive storage device
  * Serverless - Autoscaling and infinite scale
* Store large objects using a key-value approach
  * Treats entire objects as a unit(Partial updates not allowed)
    * Recommended when you operate on entire object most of the time
    * Access Control at Object level
  * Also called Object Storage
* Provides REST API to access and modify objects
* Store all file types
* Objects are stored in buckets
* Each object is identified by a unique key
* Max object size is 5 TB

## Cloud Storage - Uploading and Downloading Objects

|Option|Recommended for Scenarios|
|--|--|
|Simple Upload|Small files(that can be re uploaded in case of failures) + No object metadata|
|Multipart upload|Small files(that can be reuploaded in case of failures) + object metadata|
|Resumable upload|Larger files|
|Streaming upload|upload an object of unknown size|
|Parallel composite uploads|File divided upto 32 chunks|
|Simple download|Downloading objects to a destination|
|Streaming download|Downloading data to a process|
|Sliced object download|Slice and download large objects|

## Object Versioning
* Prevents accidental deletion & Provides history
  * Enabled at buket level
  * Live version
  * Older version
  * Reduce costs by deleting older

## Object Lifecycle Management
* Files are frequently accessed when they are created
* Identify objects using conditions based on - 
* Two kinds of actions
* Allowed Transitionsf