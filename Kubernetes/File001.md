# Kubernetes

## Borg
* Websites crash ho jaa raha tha
* Toh 2014 me inhone Borg start kiya 
* Later rename kubernetes kar diya

# Kubernetes
* Ye ek orchestration tool hai
* Isko K8S bhi bolte hain
* Kubernetes use kiyon karte hain?
* Pehle application monolithic hote hain(Mono means single)
* e.g. D-Mart
* Ek bade application ko chhote pieces me bana diya
* Why to study kubernetes?
  * **Microservice** ka use jyada ho raha hai
* CKA(Certified Kubernetes Administrator)

# Kubernetes Architecture

![alt text](image.png)
* **Node** = Server
  * 1 Node = 1 Server
  * Multi Node = Cluster
  * Master Node and Worker Node
  * Master Node - Ye worker node se kaam karwate hain
  * Worker node me docker ka container chal raha hota hai
* **Master node me kya hota hai?**
  * 1. **API Server** - API Server ka kaam kya hai? To communicate. It's a medium. If you want to talk to Kubernetes Cluster you need to talk through API server
  * 2. Requirement hai DevOps Engineer ki. Hire kaun karwata hai? HR
    * **Scheduler** - To schedule container or Pods.Aapke containers ko worker node par schedule karti hai
  * 3. 



## Scheduler
In **Kubernetes**, a **scheduler** is the control plane component responsible for deciding **which node a newly created pod should run on**.

👉 Think of it like this:

* You ask Kubernetes to create a **Pod** (your application container).
* That pod starts in a **"Pending"** state.
* The **Kube-scheduler** looks at all available nodes in the cluster and picks the most suitable one for your pod.
* Once scheduled, the **kubelet** on that node actually runs the pod.

---

### How does the scheduler decide?

It considers many factors:

1. **Resource requirements** (CPU, memory, etc.)
2. **Node constraints/affinity rules** (e.g., this pod should run only on nodes with GPUs).
3. **Taints and tolerations** (e.g., some nodes are reserved for special workloads).
4. **Pod affinity/anti-affinity** (e.g., keep pods together or spread them out).
5. **Load balancing** (distribute workloads across nodes fairly).

---

### Workflow in short:

1. User creates a Pod → Pod is "Pending".
2. Scheduler watches for "unscheduled" pods.
3. Scheduler picks the best node.
4. Pod gets bound to that node.
5. Kubelet on that node pulls the image and runs the container.

## Pod

### 🔹 Container (e.g., Docker container)

* Smallest unit of software packaging.
* Runs **one process/app** (e.g., Node.js app, MySQL DB).
* Self-contained with its own filesystem, libraries, and runtime.

Think of it like: **a single meal packed in a lunchbox**.

---

### 🔹 Pod

* A **wrapper around one or more containers**.
* Provides **shared network (same IP/port space)** and **shared storage (volumes)** to those containers.
* Containers inside a Pod are **always scheduled together** on the same Node.
* Usually → a Pod has **just one container** (most common case).
* Sometimes → a Pod has **multiple tightly-coupled containers** (like a main app + sidecar helper).

Think of it like: **a lunch tray** that can hold **one or multiple lunchboxes**, and all of them share the same table (network & storage).

---

### ✅ So:

* **Container** = the actual application.
* **Pod** = the Kubernetes unit that holds container(s).
* **Node** = the machine (VM/server) where Pods run.

---

📌 Example:

* You run a **Docker container** of Nginx → it’s just Nginx.
* You run an **Nginx Pod in Kubernetes** → it’s Nginx inside a Pod, managed by Kubernetes.
* If you need Nginx + a sidecar (say, a logging agent), **both containers go inside the same Pod**.


### ✅ Pod ≠ Docker Container

* A **Docker container** is just the application packaged with its dependencies.
* A **Pod** is a higher-level **Kubernetes abstraction** that manages **one or more containers together**, plus all the extra stuff they need to run smoothly inside a cluster.

---

### What extra things does a Pod have (beyond a container)?

1. **Networking** → Every Pod gets its own unique IP address in the cluster. All containers in that Pod share that IP.
2. **Storage** → Pods can define **volumes** (persistent or temporary) that containers share.
3. **Lifecycle & Restart Policies** → If a container inside a Pod crashes, Kubernetes can restart it.
4. **Metadata** → Labels, annotations, and configs so that other Kubernetes components (scheduler, controllers, services) can manage it.
5. **Multi-container support** → You can run a **main app container** + **sidecar containers** (for logging, proxy, monitoring) together.

---

### 🔹 So you can say:

👉 A **Pod is like a smart wrapper around one or more containers**, giving Kubernetes the power to schedule, network, scale, and manage them.

---

⚡ Quick analogy:

* **Docker container** = a single car 🚗
* **Pod** = a garage 🚘🏠 (can have one car, or a car + bike + tools) with electricity, address, and rules.
* **Node** = the whole parking lot (server) where many garages (pods) exist.

# etcd

### 🔹 What is **etcd**?

* **etcd** (pronounced *“et-cee-dee”*) is a **distributed key–value store**.
* It’s used by Kubernetes to store **all its cluster data**.
* Written in **Go**, it’s fast, reliable, and fault-tolerant.

👉 In simple words: etcd is like **Kubernetes’ database / brain**.

---

### 🔹 What does it store?

Everything about the cluster, for example:

* Cluster state (which nodes exist, are healthy, etc.)
* Pod definitions, ConfigMaps, Secrets
* Deployments, ReplicaSets, Services
* Any changes you apply with `kubectl apply`

Basically, when you run:

```bash
kubectl get pods
```

The info you’re retrieving ultimately comes from **etcd**.

---

### 🔹 Why “etcd” the name?

* **etcd = /etc + d**

  * `/etc` → traditional folder in Linux/Unix for system configuration.
  * `d` → stands for “distributed.”
* So, etcd = **distributed system configuration store**.

---

### 🔹 Properties of etcd

* **Consistent & Reliable** → uses the **Raft consensus algorithm** to agree on data across nodes.
* **Highly available** → usually runs as a cluster of 3, 5, or more nodes.
* **Key-Value store** → like a dictionary, where:

  ```
  /registry/pods/default/myapp  →  {pod details JSON}
  ```

---

### 🔹 Why Kubernetes needs etcd?

Kubernetes is a **distributed system** → many controllers, schedulers, API servers.
They all need a **single source of truth**.
That source is **etcd**.

Without etcd, Kubernetes wouldn’t “remember” the desired state of the cluster.

---

✅ **In short:**

* etcd = **Kubernetes’ database**
* Stores **all cluster state & configs**
* Highly available, distributed, consistent

---

⚡ Fun fact: If etcd crashes and you don’t have a backup, your cluster basically “forgets” everything.

# Controller Manager


## 🔹 What is the Controller Manager?

* In Kubernetes, a **controller** is a control loop that watches the cluster state and tries to make the **actual state** match the **desired state**.
* The **kube-controller-manager** is a **control plane component** that runs many such controllers as background processes.

👉 In simple words:
**Controller Manager = the automation engine that keeps the cluster running as you declared.**

---

## 🔹 Example (to make it clear)

Suppose you say:

```yaml
replicas: 3
```

in a Deployment.

* Desired state = 3 pods.
* Actual state (right now) = only 2 pods running.
* The **ReplicaSet controller** (running inside Controller Manager) notices the mismatch → creates 1 more pod.

This “check and fix” happens continuously.

---

## 🔹 Types of Controllers in kube-controller-manager

Some important ones are:

1. **Node Controller**

   * Detects if a node goes down and handles pod rescheduling.

2. **Replication Controller**

   * Ensures the correct number of pod replicas are always running.

3. **Endpoints Controller**

   * Maintains the list of endpoints (pods) that a Service should route to.

4. **Namespace Controller**

   * Cleans up resources when a namespace is deleted.

5. **ServiceAccount & Token Controllers**

   * Manage default accounts and access tokens for pods.

*(There are more, but these are the big ones.)*

---

## 🔹 Why is it important?

Without the **controller manager**, Kubernetes would not self-heal.

* If a pod crashes, no one would recreate it.
* If a node fails, no one would move workloads elsewhere.
* If a service changes, no one would update endpoints.

Basically, Kubernetes would lose its **autopilot**.

---

✅ **In short:**

* **Controller Manager** = a daemon that runs multiple controllers.
* Each controller constantly watches the cluster state and fixes mismatches.
* It’s what makes Kubernetes clusters **self-healing and automated**.













