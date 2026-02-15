# Google Cloud Architecture for CDL

## => Architecture - Loose Coupling with Pub/Sub

![alt text](image-58.png)

* Whenever you want to decouple a publisher from a subscriber, consider Pub/Sub
* Pub/Sub is used in - 
  * Microservices Architecture
  * iOT Architectures
  * Streaming Architectures

## => Data Formats
* **Three Data Formats**
* **Structured** - Tables, Rows and Columns(**Relational database**)
  * Example - Order Information, Product Inventory, etc
    * Google Cloud Services - 
        * Cloud SQL(Regional Tranactional)
        * Cloud Spanner(Global Unlimited Scale Tranactional)
        * BigQuery(Data warehousing and ML using SQL)

![alt text](image-59.png)

* **Semi-Structured** - Flexible Schema
  * Key-Value, Document(**JSON**) - Social Media Profile Information
    * Google Cloud Services - CloudFirestore/Datastore

![alt text](image-60.png)

* **Unstructured** - Video, Audio, Image, Text, Binary files
  * Example - Product images, Product videos
    * Google Cloud Services - Cloud Storage

* (**NEW) BigQuery** can also store **Semi Structured data**
  * **BigQuery ML can be used to do ML using Unstructured data**(images,videos) stored in Cloud Storage

## Cloud Dataproc 