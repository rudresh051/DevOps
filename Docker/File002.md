# commands

# 🐧 Linux + 🐳 Docker Flags Cheat Sheet

### 🔹 General Conventions

* `-a` → **all**
* `-l` → **latest / last / long format**
* `-i` → **interactive**
* `-t` → **terminal (tty)**
* `-v` → **version / verbose**
* `-h` → **help**

---

## 🐧 Linux Commands

| **Command** | **Short Flag** | **Long Flag**         | **Meaning**                       |
| ----------- | -------------- | --------------------- | --------------------------------- |
| `ls -a`     | `-a`           | `--all`               | Show all files (incl. hidden `.`) |
| `ls -l`     | `-l`           | `--format=long`       | Long listing format               |
| `ls -al`    | `-al`          | `--all --format=long` | Combine flags                     |
| `ps -a`     | `-a`           | `--all`               | Show all processes                |
| `ps -u`     | `-u`           | `--user`              | Show user processes               |
| `ps -aux`   | combo          | combo                 | Show everything                   |
| `rm -r`     | `-r`           | `--recursive`         | Delete recursively                |
| `cp -r`     | `-r`           | `--recursive`         | Copy folders recursively          |
| `cat -n`    | `-n`           | `--number`            | Show line numbers                 |
| `man -h`    | `-h`           | `--help`              | Help for man itself               |

---

## 🐳 Docker Commands

| **Command**                 | **Short Flag** | **Long Flag**         | **Meaning**                                           |
| --------------------------- | -------------- | --------------------- | ----------------------------------------------------- |
| `docker -v`                 | `-v`           | `--version`           | Show Docker version                                   |
| `docker ps -a`              | `-a`           | `--all`               | Show all containers (incl. stopped)                   |
| `docker ps -l`              | `-l`           | `--latest`            | Show last created container                           |
| `docker run -it ubuntu`     | `-it`          | `--interactive --tty` | Run container in interactive terminal                 |
| `docker exec -it <id> bash` | `-it`          | `--interactive --tty` | Run command inside running container                  |
| `docker logs -f <id>`       | `-f`           | `--follow`            | Stream container logs                                 |
| `docker build -t myapp .`   | `-t`           | `--tag`               | Tag image with a name                                 |
| `docker rmi -f <id>`        | `-f`           | `--force`             | Force remove image                                    |
| `docker system prune -a`    | `-a`           | `--all`               | Remove all unused data (images, containers, networks) |

---

## ⚡ Pro Tips

1. Short flags are just **shorthand** → `-a` == `--all`.
2. You can **combine short flags**:

   ```bash
   docker run -i -t ubuntu
   # same as
   docker run -it ubuntu
   ```
3. When confused → always use **long form** (`--version`, `--all`) because it’s self-explanatory.

---

✅ If you keep this table in mind, 70–80% of flags in Linux & Docker will start making sense.
👉 The rest you can always check with:

```bash
command --help
```

```bash
C:\Users\rudre>docker rm 30edd338d8aa
30edd338d8aa

C:\Users\rudre>docker rmi hello-world
Untagged: hello-world:latest
Deleted: sha256:54e66cc1dd1fcb1c3c58bd8017914dbed8701e2d8c74d9262e26bd9cc1642d31

C:\Users\rudre>
```

# Docker Image Layers


## 🐳 What are Docker Image Layers?

* A **Docker image** is not just one big file.
* It is made of **multiple layers**, stacked on top of each other.
* Each layer represents a **change (instruction)** in the Dockerfile.

👉 Jab tu ek Dockerfile banata hai, har line (FROM, COPY, RUN, etc.) ek **layer** banata hai.

---

## 📌 Example Dockerfile

```dockerfile
FROM ubuntu:20.04        # Base layer
RUN apt-get update       # New layer
RUN apt-get install -y python3 # Another layer
COPY app.py /app/        # Another layer
CMD ["python3", "/app/app.py"] # Final layer
```

### Layers here:

1. `FROM ubuntu:20.04` → Base image (big layer \~70 MB)
2. `RUN apt-get update` → 1 layer (small)
3. `RUN apt-get install -y python3` → 1 layer (say 50 MB)
4. `COPY app.py /app/` → 1 layer (few KB)
5. `CMD ...` → metadata layer

👉 All these together = final image.

---

## ⚡ Why Layers Are Powerful?

1. **Reusability (Caching)**

   * If you build the same Dockerfile again, unchanged layers are reused.
   * Example: If only `app.py` changes → Docker rebuilds only the `COPY` layer, not the whole image.

2. **Efficiency**

   * Common base layers (like `ubuntu:20.04`) are downloaded once → reused across many images.

3. **Portability**

   * Layers are stored as separate files (tar archives).
   * They can be shared and distributed efficiently.

---

## 🛠 How to See Layers?

Run:

```bash
docker history <image_name>
```

Example:

```bash
docker history ubuntu:20.04
```

👉 You’ll see a list of all layers with size and instruction.

---

## 🧠 Analogy

* **Image layers = Cake layers 🍰**
* Base = Sponge (FROM ubuntu)
* Cream layer = apt-get update
* Chocolate layer = apt-get install python
* Cherry on top = COPY app.py

👉 Together it’s one cake (final Docker image).
But if you only change the cherry, you don’t bake the whole cake again 😋

---

## ✅ In Short

* Docker image = **stack of read-only layers**
* Each instruction in Dockerfile = **1 layer**
* Layers make Docker:

  * Fast ⚡ (rebuild only changed layers)
  * Lightweight 💡 (reuse base layers)
  * Portable 🚚 (share common layers)

# Port Binding
## 🧠 Imagine This

* Tere laptop ek **building** hai 🏢
* Har app ek **flat** me reh raha hai (container).
* Har flat ka apna **flat door number** hai (container port).
* Lekin bahar se koi bhi seedha flat ka darwaza nahi khol sakta → sabko **building ka main gate** se hi aana padta hai (host port).

👉 **Port binding** = Building ka security guard bolta hai:
*"Agar koi visitor building ke gate no. 8080 pe aaye, toh usko flat no. 80 pe bhej do."*

---

## 🐳 Docker Angle

* Container ke andar app chal raha hai → listen kar raha hai **ek port pe**.

  * Example: Nginx listens on `80`.
* Agar tu chaahta hai woh **outside world se accessible ho**, toh tu us port ko host machine ke ek port se **bind** karega.

---

## 📌 Super Simple Example

```bash
docker run -d -p 8080:80 nginx
```

* Inside container: Nginx is running on port `80`.
* Outside world: You access port `8080` of your laptop.
* Docker does the **mapping (binding)**: 8080 (host) → 80 (container).
* Now open browser:

  ```
  http://localhost:8080
  ```

  👉 Boom! Nginx page visible.

---

## ⚡ Why This Matters

Without binding:

* App runs inside container but you **can’t reach it** from your laptop/browser.

With binding:

* You tell Docker *“take traffic from host port X and forward it to container port Y.”*

---

✅ In one line:
**Port binding = “connecting the outside world to the right door inside the container.”**


Arre wah bhai, tu ekdum **seedhi baat** pakad li 🔥 — yeh **port numbers** ka funda samajh le, toh networking ka half confusion khatam.

---

# Port number
## 🐧 What is a Port Number?

* A **port number** is just a **numeric identifier** for a “door” on a computer.
* Har service / app jo network pe baat karti hai, ek **unique port** use karti hai.

👉 Socha jaaye toh:

* IP address = **Building address** 🏢
* Port number = **Flat number inside that building** 🚪

---

## 📌 Range of Port Numbers

Port numbers are **16-bit unsigned integers** → so they go from:

```
0  to  65535
```

saare **natural numbers** hain is range ke andar 😄

---

## 🔹 Categories of Ports

1. **Well-Known Ports (0–1023)**
   Reserved for standard services:

   * `80` → HTTP
   * `443` → HTTPS
   * `22` → SSH
   * `25` → SMTP (email)
   * `3306` → MySQL

👉 Inko “system ports” bhi bolte hain.

---

2. **Registered Ports (1024–49151)**

   * Assigned to specific applications but not as common.
   * Example:

     * `3307` (alternate MySQL)
     * `8080` (alternate HTTP)

---

3. **Ephemeral / Dynamic Ports (49152–65535)**

   * Randomly chosen by the OS for temporary connections.
   * Example: Jab tu Chrome me `google.com` open karta hai → browser ek **random high port** use karega connection banane ke liye.

---

## ⚡ Example in Real Life

* Nginx (web server) listens on port **80** inside container.
* Tu bind karta hai host port `8080:80`.
* Client (browser) may open connection from its own **ephemeral port** (say 51523) → to your server’s `8080`.

So connection looks like:

```
Client_IP:51523  --->  Server_IP:8080
```

---

## ✅ In Short

* Port numbers = **0 to 65535**.
* Small ones (0–1023) = reserved for famous services.
* Middle ones (1024–49151) = registered for apps.
* High ones (49152–65535) = temporary, used by clients dynamically.


