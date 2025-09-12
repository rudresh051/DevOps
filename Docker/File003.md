# Developing with Docker
GitHub Link - https://github.com/shradha-khapra/docker-testapp
1. create a docker network
2. Setting up mongo & mongo express

# Docker network

## 🐳 What is a Docker Network?

* By default, every container runs in **isolation**.
* If multiple containers need to talk to each other (e.g., app container ↔ database container), they need to be on the same **Docker network**.
* A Docker network is a **virtual network layer** that enables communication between containers.

👉 Think of a Docker network like a **private Wi-Fi router** just for your containers.

---

## 📌 Types of Docker Networks

### 1. **Bridge (default)**

* The default network for standalone containers.
* Example:

  ```bash
  docker network create mynet
  docker run -d --name mydb --network mynet mongo
  docker run -it --name myapp --network mynet ubuntu bash
  ```

  Now inside `myapp`, you can `ping mydb` — they communicate by container name.

---

### 2. **Host**

* The container shares the host’s network stack.
* Meaning → container = same IP as host, no extra isolation.
* Example:

  ```bash
  docker run --network host nginx
  ```

  Nginx will run directly on the host’s network, without needing port mapping.

---

### 3. **None**

* The container gets **no network** at all.
* Fully isolated, can’t talk to outside or other containers.

---

### 4. **Overlay** (Advanced, for Swarm/Kubernetes)

* Creates a virtual network **across multiple Docker hosts**.
* Containers on different machines can talk as if they are on the same network.

---

## ⚡ Why Docker Networks Are Useful

1. **Service Communication**

   * App container ↔ Database container
   * Frontend ↔ Backend

2. **DNS Resolution**

   * Containers on the same network can use **names** instead of IPs.

3. **Isolation & Security**

   * You can create separate networks for separate applications.

---

## 🛠 Common Commands

```bash
docker network ls            # list all networks
docker network inspect mynet # view network details
docker network create mynet  # create a custom network
docker run --network=mynet ... # attach container to a network
```

---

## 🧠 Analogy

* **Bridge network** → Like rooms inside a house connected with internal Wi-Fi (containers talk by name).
* **Host network** → A room directly connected to the outside internet, skipping Wi-Fi.
* **None** → A room with no Wi-Fi at all.

---

✅ In short:
**A Docker network is a virtual network that handles container-to-container communication, DNS resolution, and isolation.**

