# Decoupling Applications with Pub/Sub

## Need for Asynchronous Communication
* Why do we need asynchronous communication?


## Synchronous Communication
![alt text](image-33.png)
* Applications on your web server make synchronous calls to the logging service
* What if your logging service goes doen?
  * Will your applications go down too?
* What if all of sudden, there is high load and there are lot of logs coming in?
  * Log Service is not able to handle the load and goes down very often
## Asynchronous Communication
![alt text](image-34.png)
* Create a topic and have your applications put log messages on the topic
* Logging service picks them up for processing when ready
* Advantages - 
  * Decoupling: Publisher (Apps) don't care about who is listening
  * Availability: Publisher (Apps) up even if a subscriber (Logging Service) is down
  * Scalability: Scale consumer instances (Logging Service) under high load
  * Durability: Message is not lost even if subscriber (Logging Service) is down

## Pub/Sub
* Reliable,scalable, fully-managed 

## Commands
```txt
gcloud config set project glowing-furnace-304608
gcloud pubsub topics create topic-from-gcloud
gcloud pubsub subscriptions create subscription-gcloud-1 --topic=topic-from-gcloud
gcloud pubsub subscriptions create subscription-gcloud-2 --topic=topic-from-gcloud
gcloud pubsub subscriptions pull subscription-gcloud-2
gcloud pubsub subscriptions pull subscription-gcloud-1
gcloud pubsub topics publish topic-from-gcloud --message="My First Message"
gcloud pubsub topics publish topic-from-gcloud --message="My Second Message"
gcloud pubsub topics publish topic-from-gcloud --message="My Third Message"
gcloud pubsub subscriptions pull subscription-gcloud-1 --auto-ack
gcloud pubsub subscriptions pull subscription-gcloud-2 --auto-ack
gcloud pubsub topics list
gcloud pubsub topics delete topic-from-gcloud
gcloud pubsub topics list-subscriptions my-first-topic
```