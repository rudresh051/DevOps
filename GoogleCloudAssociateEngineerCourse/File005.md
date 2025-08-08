# Cloud IAM

## Principle of Least privilege
* A user, program, or process should have only the bare
minimum privileges necessary to perform its function
![alt text](image-64.png)

## Cloud Identity
**Cloud Identity** is an Identity as a Service (IDaaS) solution that centrally manages users and groups. This would be the sole system for authentication and that provides a single sign-on experience for all employees of an organization to be used for all your internal and external applications.

**Device management** - lets people in any organization access their work accounts from mobile devices while keeping the organization's data more secure.

**Security** - Helps by applying security best practices along with being able to deploy 2SV for the whole company along with enforcement controls and can also manage passwords to make sure they are meeting the enforced password requirements automatically.

**Single Sign-on** - With single sign-on (SSO), users can access many applications without having to enter their username and password for each application

**Reporting** - This covers audit logs for logins, groups, devices and even tokens. You are even able to export these logs to BigQuery for analysis. You can then create reports from these logs that cover security, applications and activity.

**Directory Management** - Provides profile information for users in your organization, email and group addresses, and shared external contacts in the Directory. Using Google Cloud Directory Sync (GCDS), you can synchronize the data in your Google Account with your Microsoft Active Directory or LDAP server. GCDS doesn't migrate any content (such as email messages, calendar events, or files) to your Google Account. You use GCDS to synchronize all your users, groups, and shared contacts to match the information in your LDAP server.

**Google Cloud Directory Sync** is a free Google-provided tool that implements the synchronization process and can be run either on Google Cloud or in your on-premises environment. Synchronization is one-way so that Active Directory remains the source of truth.

## Identity And Access Management(IAM)
### Policy Architecture
![alt text](image-70.png)

![alt text](image-65.png)

You manage access control by defining who (identity) has what access (role) for which resource. This also includes organizations, folders, and projects.

* A **policy** is a collection of bindings, audit configuration, and metadata.
  * A policy is attached to a resource and is used to enforce access control whenever that resource is accessed

* A **binding** specifies how access should be granted on resources. It binds one or more members with a single role and any context-specific conditions that change how and when the role is granted.

The **metadata** includes additional information about the policy, such as an etag and version to facilitate policy management.

The **AuditConfig** field specifies the configuration data for how access attempts should be audited.
### The Who
![alt text](image-66.png)
**Google Account** - Any email address that's associated with a Google Account, including gmail.com or other domains.

**Service Account** - An account for an application instead of an individual end user.

**Google Groups** - A named collection of Google Accounts and service accounts

**G Suite Domain** - Google Accounts that have been created in an organization's G Suite account

**Cloud Identity Domain** - Google Accounts in an organization that are not tied to any G Suite applications or features

**AllAuthenticatedUsers** - A special identifier that represents all service accounts and all users on the internet who have authenticated with a Google Account

**AllUsers** - A special identifier that represents anyone who is on the internet, including authenticated and unauthenticated users

### Roles -  
* This is a named **collection of permissions** that grant access to perform actions on Google Cloud resources.
* You **cannot grant** a permission to the user **directly**
* You **grant a role** to a user and a**ll the permissions that the role contains.**

![alt text](image-68.png)

**Permissions** - 
* Determines what **operations are allowed** on a resource
* Correspond one-to-one with **REST API** methods
* **Not granted** to users **directly**
* You grant roles which contain one or more permissions
* E.g., `compute.instances.list`

![alt text](image-67.png)

**Primitive** - Roles historically available in the Google Cloud
    * Owner
    * Editor
    * Viewer
    * Avoid using these roles if possible

**Predefined** - Finer-grained access control than the primitive roles

**Custom** - Tailor permissions to the needs of your organization

![alt text](image-69.png)

* Launch Stages
  * alpha - in testing
  * beta - tested and awaiting approval
  * ga - generally available 
### Conditions - 
* Further constraints binding
* Used to **define** and **enforce conditional, attribute-based access control** for Google Cloud resources.
* Conditions allow you to choose **granting resource access to identities only if configured conditions are met**
* When a condition exists, the access request is only granted if the condition expression = true

### Metadata
* etags - Concurrency control
* version - Specifies schema version


To help prevent a race condition when updating the policy, IAM supports concurrency control through the use of an etag field in the policy

### Audit Config
* Used to configure audit logging
* Determines which permission types are logged, and what identities, if any, are exempted from logging

* Resource Hierarchy

![alt text](image-71.png)

## Policies and Conditions

### Policy Statement
![alt text](image-79.png)

example of policy statement shown below in JSON format- 
![alt text](image-72.png)

YAML format -(Shorter and cleaner format)
![alt text](image-80.png)

* Using cloud shell
![alt text](image-73.png)

* Commands to use
  * `gcloud projects get-iam-policy <project-id>`
  * `gcloud resource-manager folders get-iam-policy <folder-id>`
  * `gcloud organizations get-iam-policy <organization-id>`

### 1. Policy versions
* Version 1, Version 2, Version 3

![alt text](image-74.png)

### 2. Policy Limitations

* 1 policy per resource (including organizations, folders, projects)  
* **1500 members or 250 Google groups per policy**  
* **Up to 7 minutes for policy changes to fully propagate across GCP**  
* Limit of **100** conditional role bindings **per policy**


### 3. Conditions - 
Condition attributes are either based on resource or based on details about the request (timestamp, originating/destination IP address)  
![alt text](image-81.png)

* **Time based conditions**

![alt text](image-82.png)

* **Resource based conditions**

![alt text](image-83.png)

### 4. Condition Limitations

* Limited to **specific services**  
* **Primitive roles are unsupported**  
* **Members cannot be allUsers or allAuthenticatedUsers**  
* Limit of **100** conditional role bindings **per policy**  
* **20** role bindings for **same role and same member**

![alt text](image-75.png)

* Time based conditions

![alt text](image-76.png)

* Resource based conditions

![alt text](image-77.png)

### 5. AuditConfig Logs 
* It specifies the audit configuration for a service. The configuration determines which permission types are logged and what identities if any are exempted from logging.


![alt text](image-78.png)

Specifies the audit configuration for a service. The configuration determines which permission types are logged, and what identities, if any, are exempted from logging. An AuditConfig must have one or more AuditLogConfigs.

## Cloud IAM - Follow along
* Labels - Labels are a key value pair that helps you organize and then filter your resources based on their roles.

* Good rule of thumb - Label all of your resources

* Settings - Google personnel take when they're accessing your content for troubleshooting

## Service Accounts
* A service account is a special kind of account used by an application or a virtual machine (VM) instance, not a person.
* An application uses the service account to authenticate between the application and GCP services so that the users aren't directly involved
* A special type of Google account intended to represent a non-human user that needs to authenticate and be authorized to access data in Google APIs.

### Service Account types
* Service accounts play a powerful part in google cloud and can allow a different approach for application interaction with the resources in Google cloud
* Service account is a special kind of account that is used by an application or a virtual machine instance and not a person.
* It is a special type of Google account intended to represent a non human user that needs to authenticate and be authorized to access data in Google APIs.
* Note - Service account is identified by its email address which is unique to the account.


* **User-managed**
  * User created 
  * You choose the name

* **Default**
  * Using some GCP services create user-managed service accounts
  * Automatically granted the Editor role for the project
  * When using certain GCP services, default service accounts are automatically created. These are user-managed service accounts.
  * These default service accounts are automatically granted the Editor role for the project
* **Google-managed**
  * Managed by Google, and they are used by Google services
  * Some are visible, some hidden
  * Name ends with "Service Agent" or "Service Account"

![alt text](image-84.png)


### Service Account Keys
* Google managed
  * **Key Management** - None, All handled by Google
* User managed
  * **Key Management** - Key storage, Key distribution, Key revocation, Key rotation, Protecting the keys from unauthorized users, Key recovery

### Service Account Permissions
![alt text](image-85.png)

### Use of Service Accounts
![alt text](image-87.png)

### Access scopes
![alt text](image-86.png)

* Service Account scopes are the legacy method of specifying permissions for your instance
* And they are used in substitution of IAM roles
* These are used specifically for default
* Or automatically created service accounts
* Based on enabled API's


### Best Practices

* **Audit service accounts and keys** using either
the serviceAccount.keys.list() method or the Logs Viewer page in the console.
* **Delete service account external keys** if you don't need them
* Grant the service account only the **minimum set of permissions** required to
achieve their goal
* **Create service accounts for each service** with only the permissions required
for that service
* Take advantage of the IAM service account API to **implement key rotation**

### Service Accounts - Follow Along

## Cloud Identity
**Cloud Identity** is an Identity as a Service (IDaaS) solution that centrally manages users and groups. This would be the sole system for authentication and that provides a single sign-on experience for all employees of an organization to be used for all your internal and external applications.

**Device management** - lets people in any organization access their work accounts from mobile devices while keeping the organization's data more secure.
![alt text](image-89.png)

**Security** - Helps by applying security best practices along with being able to deploy 2SV for the whole company along with enforcement controls and can also manage passwords to make sure they are meeting the enforced password requirements automatically.
![alt text](image-88.png)

**Single Sign-on** - With single sign-on (SSO), users can access many applications without having to enter their username and password for each application

**Reporting** - This covers audit logs for logins, groups, devices and even tokens. You are even able to export these logs to BigQuery for analysis. You can then create reports from these logs that cover security, applications and activity.

**Directory Management** - Provides profile information for users in your organization, email and group addresses, and shared external contacts in the Directory. Using Google Cloud Directory Sync (GCDS), you can synchronize the data in your Google Account with your Microsoft Active Directory or LDAP server. GCDS doesn't migrate any content (such as email messages, calendar events, or files) to your Google Account. You use GCDS to synchronize all your users, groups, and shared contacts to match the information in your LDAP server.
![alt text](image-90.png)

**Google Cloud Directory Sync** is a free Google-provided tool that implements the synchronization process and can be run either on Google Cloud or in your on-premises environment. Synchronization is one-way so that Active Directory remains the source of truth.
![alt text](image-91.png)



## ✅ **Cloud IAM Best Practices**

### 🔒 1. **Principle of Least Privilege (PoLP)**

* **Grant only the minimum permissions** required to perform a task.
* Avoid using broad roles like `Editor` or `Owner` unless absolutely necessary.
* Instead, use **predefined roles** or create **custom roles** for precision.
* Child resources cannot restrict access granted on it's parent
* Restrict who can create and manage service accounts
* Be cautious with owner roles

---

### 🧑‍🤝‍🧑 2. **Use Groups Instead of Individuals**

* Assign IAM roles to **Google Groups** (e.g., `devs@yourdomain.com`) instead of individual users.
* Easier to manage permissions as people join/leave the team.

---

### 🧱 3. **Use Folders and Projects for Structure**

* Organize resources into **folders and projects**.
* Apply IAM policies at folder or organization level when roles apply broadly.
* Projects can inherit permissions from folders and the organization.

---

### 🧪 4. **Audit Permissions Regularly**

* Use **Cloud Asset Inventory** or **Policy Analyzer** to view who has access to what.
* Review and **remove unused roles or accounts**.
* Use the **Recommender** service to get IAM role reduction suggestions.

---

### 🧑‍💻 5. **Avoid Granting Roles to All Users**

* Do **not use `allUsers` or `allAuthenticatedUsers`** unless your resource is truly public.
* For example, `Storage Object Viewer` to `allUsers` will expose a bucket to the internet.

---

### 🔐 6. **Enable Two-Factor Authentication (2FA)**

* Enforce **multi-factor authentication (MFA)** for all accounts, especially those with admin privileges.
* Use **Google Workspace or Identity Platform** policies for enforcement.

---

### 🧰 7. **Use Service Accounts Correctly**

* Give **each application/service a unique service account**.
* **Do not use user accounts** for automation.
* Apply minimal permissions to service accounts and **use Workload Identity Federation** if you want to avoid long-lived keys.
* When using service accounts, treat each app as a separate trust boundary
* **Do not delete service accounts** that are in use by running services
* Rotate user managed service account keys
* Name service account keys to reflect use and permissions
* Restrict service account access
* Don't check in service account keys into source code
---

### 🧾 8. **Enable and Monitor Audit Logs**

* Enable **Cloud Audit Logs** (Admin Activity logs are always on).
* Monitor logs for **suspicious activity**, such as unexpected permission grants or denied requests.
* Use Cloud Audit Logs to regularly audit IAM policy changes
* Audit who can edit IAM policies on projects
* Export audit logs to Cloud Storage for long-term retention
* Regularly audit service account key access
* Restrict log access with logging roles
---

### 📦 9. **Use Custom Roles Carefully**

* Use **predefined roles** when possible — they're well-tested.
* Create **custom roles** if you need a precise set of permissions not available in predefined roles.
* Keep custom roles documented and version-controlled.

---

### 🚨 10. **Set Up Alerts for Critical Changes**

* Use **Cloud Monitoring and Logging** to:

  * Alert on changes to IAM policies
  * Alert on use of high-risk permissions (like `resourcemanager.projects.delete`)


### 11. Resource Hierarchy
* Mirror your Google Cloud resource hierarchy structure to your organization structure
* Use projects to group resources that share the same trust boundary
* Set policies at the organization level and at the project level rather than at the
resource level
* Use the security principle of least privilege to grant IAM roles
* Grant roles for users or groups at the folder level instead of setting it at the
project level, if spanning across multiple projects

### 12. Policy Management
* To grant access to all projects in your Organization, use an organization-level
policy
* Grant roles to a Google group instead of individual users where possible
* When granting multiple roles to a particular task, create a Google group
instead

---

## **Use Organization Policy Constraints**

* Use **Org Policies** to:

  * Restrict where resources can be created (e.g., specific regions)
  * Enforce SSL
  * Prevent external service account keys


