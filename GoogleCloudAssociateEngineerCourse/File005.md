# Cloud IAM

## Identity And Access Management(IAM)
You manage access control by defining who (identity) has what access (role) for which resource. This also includes organizations, folders, and projects.

A **policy** is a collection of bindings, audit configuration, and metadata.

A **binding** specifies how access should be granted on resources. It binds one or more members with a single role and any context-specific conditions that change how and when the role is granted.

The **metadata** includes additional information about the policy, such as an etag and version to facilitate policy management.

The **AuditConfig** field specifies the configuration data for how access attempts should be audited.

**Google Account** - Any email address that's associated with a Google Account, including gmail.com or other domains.

**Service Account** - An account for an application instead of an individual end user.

**Google Groups** - A named collection of Google Accounts and service accounts

**G Suite Domain** - Google Accounts that have been created in an organization's G Suite account

**Cloud Identity Domain** - Google Accounts in an organization that are not tied to any G Suite applications or features

**AllAuthenticatedUsers** - A special identifier that represents all service accounts and all users on the internet who have authenticated with a Google Account

**AllUsers** - A special identifier that represents anyone who is on the internet, including authenticated and unauthenticated users

**Roles** -  
* This is a named collection of permissions that grant access to perform actions on Google Cloud resources.
* You cannot grant a permission to the user directly
* You grant a role to a user and all the permissions that the role contains.

**Permissions** - 
* Determines what operations are allowed on a resource
* Correspond one-to-one with REST API methods
* Not granted to users directly
* E.g., compute.instances.list

**Primitive** - Roles historically available in the Google Cloud
    * Owner
    * Editor
    * Viewer
    * Avoid using these roles if possible

**Predefined** - Finer-grained access control than the primitive roles

**Custom** - Tailor permissions to the needs of your organization

**Conditions** - 
* Used to define and enforce conditional, attribute-based access control for Google Cloud resources.
* Conditions allow you to choose granting resource access to identities only if configured conditions are met
* When a condition exists, the access request is only granted if the condition expression = true

**Metadata**  
To help prevent a race condition when updating the policy, IAM supports concurrency control through the use of an etag field in the policy

**Audit Config**  
* Determines which permission types are logged, and what identities, if any, are exempted from logging

## Policies and Conditions
**Policy Limitations**  

1 policy per resource (including organizations, folders, projects)  
1500 members or 250 Google groups per policy  
Up to 7 minutes for policy changes to fully propagate across GCP  
Limit of 100 conditional role bindings per policy
Conditions - Condition attributes are either based on resource or based on details about the request (timestamp, originating/destination IP address)  

**Condition Limitations**

Limited to specific services  
Primitive roles are unsupported  
Members cannot be allUsers or allAuthenticatedUsers  
Limit of 100 conditional role bindings per policy  
20 role bindings for same role and same member  

**AuditConfig Logs**  

Specifies the audit configuration for a service. The configuration determines which permission types are logged, and what identities, if any, are exempted from logging. An AuditConfig must have one or more AuditLogConfigs.


## ✅ **Cloud IAM Best Practices**

### 🔒 1. **Principle of Least Privilege (PoLP)**

* **Grant only the minimum permissions** required to perform a task.
* Avoid using broad roles like `Editor` or `Owner` unless absolutely necessary.
* Instead, use **predefined roles** or create **custom roles** for precision.

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

---

### 🧾 8. **Enable and Monitor Audit Logs**

* Enable **Cloud Audit Logs** (Admin Activity logs are always on).
* Monitor logs for **suspicious activity**, such as unexpected permission grants or denied requests.

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

---

## **Use Organization Policy Constraints**

* Use **Org Policies** to:

  * Restrict where resources can be created (e.g., specific regions)
  * Enforce SSL
  * Prevent external service account keys


