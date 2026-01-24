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