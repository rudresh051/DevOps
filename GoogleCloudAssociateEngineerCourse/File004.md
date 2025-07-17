# Account Setup

## Resource Hierarchy

In Google Cloud Platform (GCP), the resource hierarchy helps organize and manage GCP resources (like VMs, buckets, etc.) systematically, especially in large organizations. It allows setting permissions (IAM) and policies at different levels.

1. Organization (optional, for large companies)
   ↓
2. Folders (optional, used to group projects/departments)
   ↓
3. Projects (mandatory, main container for resources)
   ↓
4. Resources (e.g., Compute VMs, Cloud Storage, Cloud SQL, etc.)

1. Service-level resources
   1. Compute Instance VM's
   2. Cloud Storage buckets
   3. Cloud SQL databases

2. Account-level resources
   1. Organization
   2. Folders
   3. Projects

* Configure and grant access to the various resources
* Resource Hierarchy Structure
* Resources are organized hierarchically using a parent/child relationship
* Designed to map organizational structure to Google Cloud
* Better management of permissions and access control
* Policies controlled by IAM
* Access control policies and configuration settings on a parent resource are inherited by the child
* Each child object has exactly one parent.