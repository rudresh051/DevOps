# Google Cloud Platform - Other Important Services


## GCP - Armor
* GCP Armor is Google Cloud Platform's **comprhensive security offering** designed to protect against-based assets and workloads from various cyber threats. It provides a multi-layered security approach to safeguard data, applications, and infrastructure hosted on Google Cloud.
* It is **Cloud Network service** that provides defense against the security threats like application attacks and Distributed Denial-of-service(DDOS) and offers a rich set of defined Web Application Firewall(WAF) rules. 

* Security Policy
  * It allows users to **define and enforce customized security rules** to protect web applications and services hosted on Google Cloud. These policies are primarilty focused on protecting against **Layer 7** (applicaion layer) attacks , such as HTTP floods, SQL injection, and cross-site scripting (XSS) attacks.
  * A security policy in Google Cloud Armor is **a set of rules that define how traffic is allowed or denied** to rech your web applications. These rules are based on various criteria, including IP addresses, HTTP headers, URL paths, and other attributes of incoming requests
    * > Firewall mainly works at Layer 3 and Layer 4
  * **Layer 7 Protection** - 
    * Google Cloud Armor focuses on **providing Layer 7 protection**, which means it can inspect and filter traffic based on application-layer attributes, such as HTTP headers and payload contents. This allows for more granular control and targeted protection against sophisticated application-level attacks.
  * **Rule-Based Configuration**
    * Security policies in Google Cloud Armor are configured using rules that specify conditions and actions to be taken for matching traffic. Users can create rules to allow, deny, or modify based on specific criteria, such as IP addresses, geolocation, user agents, or request methods.
  * **IP-based Access Control** -
    * Users can define IP-based allowlists and denylists to control access to web applications. This feature helps mitigate malicious traffic originating from known bad actors or unauthorized sources. 
  * **URL Map Integration** -
    * Google Cloud Armor Security Policies can be integrated with **URL maps**, which allows users to apply security policies to specific backend services or URL paths within their Google Cloud Load Balancer configuration 
  * **WAF Capabilites** -
    * While not as feature-rich as standalone Web Application Firewall(WAF) solutions, Google Cloud Armor **offers basic WAF capabilities** to protect against common web application attacks, such as SQL injection, cross-site scripting(XSS), and remote file inclusion(RFI)
  * **Logging and Monitoring**
    * Google Cloud Armor Security Policies **integrate with Google Cloud Monitoring and Cloud Logging**, allowing users to monitor policy enforcement, analyse traffic patterns, and investigate security incidents through logs and metrics