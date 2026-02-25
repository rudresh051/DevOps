# Building Loosely Coupled Applications with Cloud Pub Sub

## Need for Asynchronous Communication

* Create a topic and have your applications put log messages on the topic
* Logging service picks them up for processing when ready
* Advantages - 
  * Decoupling - Publisher(Apps) don't care about who is listening
  * Availability
  * Scalability
  * Durability

## Pub/Sub

* **Usecases** - Event ingestion and delivery for streaming analytics pipelines
* Supports push and pull message deliveries