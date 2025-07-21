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