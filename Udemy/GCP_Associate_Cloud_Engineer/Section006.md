# Section 6: Getting started with Instance Groups in Google Cloud

* How do you create a group of VM instances?
  * Instance Group - Group of VM instances managed as a single entity
    * Manage group of similar VMs having similar lifecycle as ONE UNIT
* Two Types of Instance Groups:
  * Managed : Identical VMs created using a template:
 Features: Auto scaling, auto healing and managed releases
   * Unmanaged : Different configuration for VMs in same group:
     * Does NOT offer auto scaling, auto healing & other services
     * NOT Recommended unless you need different kinds of VMs
 * Location can be Zonal or Regional
   * Regional gives you higher availability (RECOMMENDED)