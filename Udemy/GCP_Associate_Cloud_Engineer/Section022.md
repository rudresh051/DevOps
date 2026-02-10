# Cloud Operations

## Cloud Monitoring
* To operate cloud applications effectively, you should know - 
  * Is my application healthy?
  * are the users experiencing any issues?
  * Does my database has enough space?
  * are my servers running in an optimum capacity?
* Cloud Monitoring - Tools to monitor your infrastructure
  * Measures key aspects of services(Metrics)
  * Create visualizations(Graphs and Dashboard)
  * Cofigure Alerts(when metrics are NOT healthy)

## Cloud Montitoring - Workspace
* You can use cloud monitoring to monitor one or more GCP projects and one or more AWS accounts
* How do you group all the information from multiple GCP projects or AWS accounts?
* **Create a Workspace**
* Workspaces are needed to organize monitoring information
  * A workspaces allows you to see monitoring information from multiple projects
  * Step 1 - Create workspace in a specific project(Host Project)
  * Step 2 - Add other GCP projects(or AWS accounts) to the workspace

## Cloud Logging
* Real time log management and analysis tool
* Allows to store, search, analyze and alert on massive volume of data

## Cloud Logging - Collection
## Cloud Logging - Audit and Security Logs
## Cloud Logging - Audit Logs
* Which service?
  * protoPayload.serviceName
* Which operation?
  * protoPayload.methodName
* What resource is audited?
  * resource.Type
* Who is making the call?
  * authenticationInfo.principalEmail

## Cloud Audit Logs

|Feature|Admin Activity Logs|Data Acess Logs|System Even Logs|Policy Denied Logs|
|--|--|--|--|--|
|Logs for|||||
|Default Enabled|||||
|VM Examples|||||
|Cloud Storage|||||
|Recommended|||||

## Cloud Logging - Controlling & Routing
* How do you manage your logs?
* Two types of Logs buckets - 
  * _Required
  * _Default

## Cloud Logging - Export - Use Cases
* Use Case 1  - Troubleshoot using VM logs
* Use Case 2 - Export VM logs to BigQuery for querying using SQL like queries
* Use Case 3 - You want to retain audit logs for external auditors at minimum cost


<hr><hr><hr>

## GCP Network Tier

* **Premium Service Tier**

Traffic travels through the Google's high quality global backbone, entering and exiting at Google edge peering points closest to the user.  
For example: Consider an application is running on a virtual machine (VM) instance deployed in
the us-centrall (iowa) region. A user located in Mumbai, India, attempts to access the
application. Once the user's request reaches their Internet service provider, it is routed to the
closest Google edge peering point. From there, the request travels through Google Cloud's
reliable global backbone network to reach the destination in the us-centrall region (located in
Iowa). Similarly, the response from the application also returns through Google's backbone
network.

* **Standard Service Tier**

Traffic enters and exits the Google network at a peering point closest to the Cloud region it's
destined for or originated in.  

For example: Consider an application is running on a virtual machine (VM) instance deployed in
the us-centrall (iowa) region. A user located in Mumbai, India, attempts to access the
application. Once the user's request reaches their Internet service provider, the traffic is routed
through the internet towards the peering point closest to the cloud region at the destination
(iowa). From there, the request reach the destination in the us-centrall region (located in Iowa).
Similarly, the response from the application also returns through the internet and NOT through
the Google's backbone network

### GCP Network Tier: Premium vs Standard

| Aspect                  | **Premium Tier**                          | **Standard Tier**                            |
| ----------------------- | ----------------------------------------- | -------------------------------------------- |
| Network used            | Google’s **global private backbone**      | Public internet + regional Google network    |
| Traffic routing         | Enters Google network **closest to user** | Enters Google network **near the VM region** |
| Latency                 | **Lower**                                 | Higher                                       |
| Performance consistency | **Very high & predictable**               | Variable                                     |
| Global load balancing   | ✅ Yes                                     | ❌ No                                         |
| SLA                     | **Higher SLA**                            | Lower SLA                                    |
| DDoS protection         | **Advanced (global)**                     | Basic                                        |
| Availability            | Global                                    | Regional                                     |
| Cost                    | **More expensive**                        | **Cheaper**                                  |
| Default tier            | ✅ Yes (default)                           | ❌ No                                         |


* Simple mental model 🧠

**Premium** → Google’s private highway, globally  
**Standard** → Public roads + some Google highways  

![alt text](image-168.png)


* The number of hops is more in standard service tier network when compared to google premium-network
* Hop counts are the intermediate devices

![alt text](image-169.png)

## GCP Network Intelligence Services - Hands-on 

* **Network Topology**
  * It shows the project network over the GCP network

![alt text](image-173.png)


* **Connectivity Test**

![alt text](image-170.png)

* **Performance Dashboard**

![alt text](image-171.png)

* **Firewall Insights**
  * Details about firewall rules

* **Network Analyzer**
  * How many VPC, GKE, Hybrid connectivity are present

![alt text](image-172.png)

## Logging & Monitoring

* > If you click on logs it will automatically redirect to the Logs explorer with a query written
* Logs Explorer

![alt text](image-174.png)

We can filter the logs using **resouce filter**. The query will be automatically applied

![alt text](image-175.png)

Logs can filtered based on severity

![alt text](image-176.png)
