# Docker Compose
Docker Compose is a **tool for defining and managing multi-container Docker applications**.

Instead of running multiple `docker run` commands manually, you describe all the services your application needs (databases, backend, frontend, cache, etc.) in a **single YAML file** (`docker-compose.yml`). Then, with just one command (`docker-compose up`), Docker Compose will start and connect all the containers for you.

---

### Key Points:

* **Configuration in YAML**: You define your services, networks, and volumes in `docker-compose.yml`.
* **Multi-container orchestration**: Useful for apps that need multiple services (e.g., a web server + database + cache).
* **Environment isolation**: Each Compose project runs in its own network, so services can talk to each other by name.
* **One-command deployment**: `docker-compose up` starts everything, `docker-compose down` stops and cleans up.

---

### Example

Here’s a simple `docker-compose.yml`:

```yaml
version: "3.8"

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
```

* Running `docker-compose up` will start **Nginx** (on port 8080) and **MySQL** (with password `example`).
* The `web` container can reach the database using the hostname `db`.

---

✅ In short: **Docker = container tool**
**Docker Compose = tool to manage multi-container applications easily.**

ठीक है 🙂
चलो इसे **simple रोज़मर्रा के example** से समझते हैं:

---

### Docker vs Docker Compose – Restaurant Analogy 🍽️

* **Docker (single container)** → मान लो तुमने सिर्फ़ *एक रसोईया* (cook) रखा है जो सिर्फ़ *चाय* बना सकता है।
  मतलब एक container = एक काम (जैसे web server, database, cache, etc.)

* **Docker Compose (multi-container management)** → अब imagine करो तुम्हारा restaurant है जहाँ सिर्फ़ चाय वाला cook काफी नहीं है।
  तुम्हें चाहिए:

  * चाय वाला cook ☕ (web server)
  * खाना बनाने वाला cook 🍲 (database)
  * मिठाई वाला cook 🍰 (cache)

  अब हर बार सबको अलग-अलग बुलाना, instructions देना, ये झंझट हो जाएगा।
  इसके बजाय तुमने एक **menu card (docker-compose.yml)** बना लिया जिसमें लिखा है:

  * कौन सा cook चाहिए
  * किसको कौन-सा सामान (volume) चाहिए
  * किसको कहाँ काम करना है (network)

  फिर तुम बस एक command बोलते हो:
  👉 `docker-compose up`
  और पूरा restaurant एक साथ चल पड़ता है — सब cooks अपनी-अपनी जगह काम करने लगते हैं।

---

### Bottom line:

* **Docker** = एक-एक container चलाने का तरीका।
* **Docker Compose** = एक command से *पूरा setup* (multi-container app) खड़ा करने का तरीका।



# Dockerizing our app

**Dockerizing an app** means:
👉 Taking your application (code + dependencies + environment setup) and packaging it into a **Docker container image** so it can run anywhere without worrying about the host system.

---

### Why "Dockerize"?

Normally, running an app requires:

* Correct version of programming language (Node, Java, Python, etc.)
* Installing libraries (npm install, pip install, maven, etc.)
* Configuring environment (ports, DB connection, OS dependencies)

On your laptop it works ✅, but on a server it might fail ❌ because the setup is different.

**When you dockerize your app:**

* You put all these things in a **Dockerfile**.
* Build a **Docker image** → a portable package.
* Run it as a container anywhere (Linux, Windows, Mac, Cloud, Kubernetes).

---

### Example: Dockerizing a Node.js App

Suppose you have an `app.js` that runs on Node.js.

👉 Create a `Dockerfile`:

```dockerfile
# Step 1: Use official Node.js image as base
FROM node:18

# Step 2: Set working directory inside container
WORKDIR /app

# Step 3: Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Step 4: Copy rest of the code
COPY . .

# Step 5: Expose port
EXPOSE 3000

# Step 6: Run the app
CMD ["node", "app.js"]
```

---

### Steps to Dockerize

1. Build image:

   ```bash
   docker build -t my-node-app .
   ```
2. Run container:

   ```bash
   docker run -p 3000:3000 my-node-app
   ```

Now your app is running inside a container 🎉.
You can send this image to anyone, or push it to Docker Hub, and it will run the same everywhere.

---

✅ **In short:**
*Dockerizing an app = packaging your app + dependencies into a Docker image → running it anywhere as a container.*

Writing a docker file - https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/

# Publishing Images on Docker hub

# Docker volumes


## 📦 What is a Docker Volume?

By default, any data written inside a container (e.g., files, DB data, logs) is **temporary**.
👉 If the container stops or is removed, the data is lost.

**Docker Volumes** solve this by providing:

* **Persistent storage** → data survives even if the container is deleted.
* **Sharing** → multiple containers can access the same volume.
* **Decoupling** → data is stored outside the container’s writable layer, making it safer and more portable.

Example:

```bash
docker run -v myvolume:/data mongo
```

Here, all content inside `/data` of the container will be stored in a named volume `myvolume`.

---

## 🍱 Analogy: Tiffin Box + Kitchen

* Think of a **container** like a lunchbox.
* If you put food directly into the lunchbox and the box breaks, the food is gone.
* Instead, if you **store food in the kitchen** and only serve it in the lunchbox, the food stays safe even if the lunchbox is replaced.

👉 In this analogy:

* **Container = Lunchbox**
* **Volume = Kitchen**
* **Data = Food**

So, containers can come and go, but the data is safely stored in the “kitchen” (volume).

---

### ⚡ In short:

**Docker Volumes are persistent storage areas where container data is safely kept outside the container’s lifecycle.**


