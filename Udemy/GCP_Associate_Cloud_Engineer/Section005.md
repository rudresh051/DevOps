# Section 5: Google Compute - Optimizing Costs and Performance in GCP

## Sustained Use Discounts

* These are automatically applied when you use instanes created by GKE or VMs usage

![alt text](image-129.png)

* Note above does not apply to VMs created using App engine and dataflow


## Committed use discounts
* It needs commitment from you if you think you need specific resources for some fixed time like 1 year

![alt text](image-130.png)

* Note above does not apply to VMs created using App engine and dataflow

![alt text](image-131.png)

## Preemptible VM
* Use it when
  *  your applications are **fault tolerant**
  *  you are very **cost sensitive**
  *  your workload is **NOT immediate**
  *  Example - Non immediate batch processing jobs

![alt text](image-132.png)

Under Machine Configuration >> Advanced Configurations

![alt text](image-133.png)

Update - Only change is now it **doesn't have maximum runtime**. Previously it was only for 24 hours.

![alt text](image-134.png)

## Understanding Billing for Google Compute Engine
![alt text](image-135.png)

Navigate to the following

![alt text](image-136.png)

* Billing Export

![alt text](image-137.png)

you can send your billing data to BigQuery Dataset

## Achieving High Availability with Live Migration and Automatic Restart
* How do you keep your VM instances running when a host system needs to be updated(a software or a hardware update needs to be performed)?
  * > You don't wnat your application to go down when you want to upgrade your software or hardware
* **Live Migration**
  * Your running instances is migrated to another host in the same zone
  * Does not change any attributes or properties of the VM
  * SUPPORTED for instances with local SSDs
  * NOT SUPPORTED for GPUs and preemptible instance
* Important Configuration - **Availability Policy**
  * **On host maintenance** - What should happen during periodic infrastructure maintenance?
    * Migrate(default) - Migrate VM instance to other hardware
    * Terminate - Stop the VM instance
  * **Automatic restart** - Restart VM instances if they are terminated due to non-user-initiated reasons(maintenance event, hardware failure etc.)

![alt text](image-138.png)

**Basically set the "On host maintenance" to Migrate**

## Exploring GPUs(Graphic Processing Unit) in Google Compute Engine

![alt text](image-139.png)

**Note** - On host maintenance, you need to terminate the VM instance

> GPUs can't be added to VMs while in the free trial programme. To enable adding GPUs to VMs, upgrade to a paid Cloud Billing Account.

## Quick Review

![alt text](image-140.png)

* Important - You must stop the VM instance to edit it's machine type.
  * Don't get confused with live migration. Here machine type is not changed. This is done by google to maintain the host.
  * But when we do, we need to stop the VM

Note - 
* Instances are zonal(in a specific zone NOT region)
  * Instance templates global(unless you use zonal resources in your templates)
  * Custom Images(to reduce launch time of VM) are global - You can provide access to other project if needed
* **Automatic Basic Monitoring** is enabled

## Sole-tenant nodes
* when you want more security, compliance
  
![alt text](image-141.png)

## Virtual Machine manager
* Basically to manage Virtual Machine
![alt text](image-142.png)

## Scenarios - Virtual Machine

![alt text](image-143.png)

## Quick Review

![alt text](image-144.png)

![alt text](image-145.png)




