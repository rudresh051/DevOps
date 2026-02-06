# Exploring API Management - Apigee, Endpoints, API Gateway

* **Most applications today are built around REST API**
  * Resources(/todos,/todos/{id},etc.)
* **Managment of REST API is not easy -** 
  * You've to take care of authentication and authorization
  * You've to be able to set limits (rate limiting, quotas) for your API consumers
  * You've to take care fof mplementing multiple versins of your API
  * You would want to implement monitoring, caching and lot of other features...


* **Apigee API Management** - Comprehensive API management platform
  * Deployment options : Cloud, on-premises or hybrid
  * Manage Complete API life cycle
  * Powerful Features
    * On-boarding partners and developers
    * Supports complex integrations(REST, gRPC, Non-gRPC-REST, integrate with GCP, on-premises or hybrid apps)
* **Cloud Endpoints** - Basic API Management for Google Cloud Backneds
  * Little complicated to setup - You need to build a container and deploy to Cloud Run
  * Supports REST API and gRPC
* **API gateway-** Newer, Simpler API Management for Google Cloud backends
  * Similar to setup
  * Suppots REST API and gRPC