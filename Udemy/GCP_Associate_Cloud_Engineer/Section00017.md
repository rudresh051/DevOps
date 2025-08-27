# Authentication and Authorization in Google Cloud with Cloud IAM

## Typical identity management in the cloud
* Authentication(is it the right user?) and
* Authorization
* Identities can be
  * A GCP User
* Provides very granular control
  * Limit a single user
    * to perform single action
    * on a specific cloud resource
    * from a specific IP address
    * during a specific time window

## Cloud IAM Example

## Commands
```txt
gcloud compute project-info describe
gcloud auth list
gcloud projects get-iam-policy glowing-furnace-304608
gcloud projects add-iam-policy-binding glowing-furnace-304608 --member=user:in28minutes@gmail.com --role=roles/storage.objectAdmin
gcloud projects remove-iam-policy-binding glowing-furnace-304608 --member=user:in28minutes@gmail.com --role=roles/storage.objectAdmin
gcloud iam roles describe roles/storage.objectAdmin
gcloud iam roles copy --source=roles/storage.objectAdmin --destination=my.custom.role --dest-project=glowing-furnace-304608
```

* IAM policy is a list of bindings - at project level

## Service Accounts

