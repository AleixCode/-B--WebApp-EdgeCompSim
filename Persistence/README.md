# 📁 Project Persistence Setup Guide

This guide covers setting up MongoDB persistence for the project using Docker containers.

---

## 📦 Requirements

- Docker Engine installed
- Git

---

## ✅ Setup Steps

### 1. 📂 Clone the Repository (if needed)

```bash
git clone git@github.com:AleixCode/-B--WebApp-EdgeCompSim.git
cd -B--WebApp-EdgeCompSim
```

---

### 2. 🏗️ Build and Run the MongoDB Container

Use the `run.sh` script to build the Docker image and start your MongoDB container for the first time.

```bash
./run.sh
```

**Script contents (`run.sh`):**

```bash
#!/bin/bash

# Build Docker image for MongoDB
sudo docker build -t my-mongodb .

# Run container mapping host port 27016 to MongoDB's default 27017
docker run -d \
  -p 27016:27017 \
  --name mongodb_container \
  my-mongodb
```

> 💡 Ensure `run.sh` is executable:
>
> ```bash
> chmod +x run.sh
> ```

---

### 3. ▶️ Start the MongoDB Container

After the initial run, you can start the existing container any time with:

```bash
./start.sh
```

**Script contents (`start.sh`):**

```bash
#!/bin/bash

docker start mongodb_container
```

> 💡 Make sure `start.sh` is executable:
>
> ```bash
> chmod +x start.sh
> ```

---

### 4. ⏹️ Stop the MongoDB Container

To stop the running container:

```bash
./stop.sh
```

**Script contents (`stop.sh`):**

```bash
#!/bin/bash

docker stop mongodb_container
```

> 💡 Make sure `stop.sh` is executable:
>
> ```bash
> chmod +x stop.sh
> ```

---

## 🔁 Common Docker Commands

- **List containers:**

  ```bash
  docker ps -a
  ```

- **Remove container:**

  ```bash
  docker rm mongodb_container
  ```

- **Remove image:**

  ```bash
  docker rmi my-mongodb
  ```

---

## 🔪 Troubleshooting

- **Permission denied when building image?**

  - Ensure you have Docker permissions. On Linux, you might need `sudo` or add your user to the `docker` group.

- **Port conflicts on `27016`?**

  - Change the host port mapping in `run.sh`, e.g., `-p 28016:27017`.

- **Container logs:**

  ```bash
  docker logs mongodb_container
  ```

---

## 📌 Notes

- MongoDB data inside the container is ephemeral unless you mount a volume.
- To persist data across container restarts and rebuilds, consider adding a volume:

  ```dockerfile
  docker run -d -p 27016:27017 \
    -v mongodb_data:/data/db \
    --name mongodb_container \
    my-mongodb
  ```
