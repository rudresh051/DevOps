# Question 1
1. A software development company needs to provide a cost estimate for a Kubernetes cluster using the GCP pricing calculator for Kubernetes. The workload requires high IOPs(Input/output operations per second) and will be using disk snapshots. They start by entering the number of nodes, average hours, and average days.

What should they do next?
* Select Add GPUs. Add estimated cost for cluster management.
* Fill in local SSD. Fill in persistent disk storage and snapshot storage.
* Fill in local SSD. Add estimated cost for cluster management.
* Select Add GPUs. Fill in machine type

# Question 2

You want to verify the IAM users and roles assigned within a GCP project named exampro-project.

What should you do?
* Navigate to the project and then to the Roles section in the GCP Console. Review the roles and status.
* Navigate to the project and then to the IAM section in the GCP Console. Review the members and roles.
* Run gcloud iam roles list. Review the output section.
* Run gcloud iam service-accounts list. Review the output section.

Correct answer is 2nd

Ah, got it bro — this is a common confusion. Let me explain clearly.

---

### **Principal in GCP IAM**

A **principal** is basically **“who” you are granting access to**. It’s the identity that can perform actions in a project.

**Types of principals:**

1. **User account** → e.g., `john@example.com`
2. **Service account** → e.g., `my-app-sa@project.iam.gserviceaccount.com` (used by apps)
3. **Google group** → e.g., `dev-team@example.com`
4. **Domain** → e.g., `@example.com` (all users in the domain)
5. **AllAuthenticatedUsers / AllUsers** → everyone with Google account / public

---

### **IAM view options**

* **View by principal** → Shows **all roles assigned to a particular identity**.

  * Example: “What roles does `alice@example.com` have in this project?”

* **View by roles** → Shows **all users who have a particular role**.

  * Example: “Who has the role `Editor` in this project?”

---

✅ **Memory trick:**

* **Principal = who**
* **Role = what**

By command line - `gcloud projects get-iam-policy   confident-inn-466803-r1`