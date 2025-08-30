# Organizing GCP Resources

## Resource Hierarchy in GCP
* Well defined hierarchy - 
  * Org > folder > project > resources
* Resources are created in projects
* A folder can contain multiple projects
* Organization can contain multiple projects

## Resource Hierarchy - Recommendations for Enterprises
* Create **separate projects for different environments**
  * Create isolation between for each department
* Create **separate folders for each department**
  * Isolate production applications of one department from another
  * We can create a shared folder for shared resources
* **One project per application per environment**
  * Let's consider two apps - A1 and A2
  * Let's assuem we need two environments "DEV" and "PROD"
  * In the ideal world you will create four projects A1-DEV, A1-PROD, A2-DEV, A2-PROD
    * Isolates environments from each other
    * DEV changes will not break PROD
    * Grant all developers complete access(create, delete, deploy) to DEV projects
    * Provide production access to operations teams only!

In free trial only Org and projects are available

![alt text](image-35.png)