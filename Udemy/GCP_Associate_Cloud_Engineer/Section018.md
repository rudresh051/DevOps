# Choosing Database in Google Cloud Platform
|Database Type|GCP Services|Description|
|--|--|--|
|**Relational OLTP databases**|Cloud SQL, Cloud Spanner|Transactional usecases needing **predefined schema** and very **strong transactional** capabilities (Row storage) <br> **Cloud SQL:** MySQL, PostgreSQL, SQL server DBs <br> **Cloud Spanner:** Unlimited scale and 99.999% availabilityfor global applications with horizontal scaling|
|**Relational OLAP databases**|BigQuery|Columnar storage with predefined schema. Datawarehousing & BigData workloads|
|**NoSQL Databases**|Cloud Firestore(Datastore), Cloud BigTable|Apps needing **quickly evolving** structure (**schema-less**) <br> **Cloud Firestore** - Serverless transactional document DB supporting mobile & Web apps. Small to medium DBs (0-few TBs) <br> **Cloud BigTable** - Large databases(10TB-PBs). Streaming (IOT), analytical & operational workloads. NOT serverless.|
|**In memory databases/caches**|Cloud Memorystore|Applications needing **microsecond** responses|

## Databases - Scenarios
|Scenario|Solution|
|--|--|
|A start up with quickly evolving schema(table structure)|Cloud Datastore/firestore|
| Non relational db with less storage (10 GB)|Cloud Datastore|
|Transactional global database with predefined schema needing to process million of transactions per second|Cloud Spanner|
|Transactional local database processing thousands of transactions per second|Cloud SQL|
|Cache data (from database) for a web application|Memory Store|
| Database for analytics processing of petabytes of data|BigQuery|
|Database for storing huge volumes stream data from IOT devices|BigTable|
|Database for storing huge streams of time series data|BigTable|