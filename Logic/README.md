# 🚀 Project Setup Guide

This guide walks you through setting up the environment, installing dependencies, configuring Redis, and running the app.

---

## 📦 Requirements

- Python 3.8+
- Redis
- Git
- Docker

---

## ✅ Installation Steps

### 1. 📅 Clone the Repository

```bash
git clone git@github.com:AleixCode/-B--WebApp-EdgeCompSim.git
cd -B--WebApp-EdgeCompSim
```

---

### 2. 🧠 Install and Start Redis

#### Install Redis

Follow the official guide for your system:
🔗 [https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/install-redis-on-linux/](https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/install-redis-on-linux/)

For Debian/Ubuntu:

```bash
sudo apt update
sudo apt install redis-server
```

#### Start Redis

```bash
sudo systemctl start redis-server
```

Check it's running:

```bash
redis-cli ping
# Output: PONG
```

---

### 3. 🐍 Set Up Python Environment

Navigate to the Logic directory:

```bash
cd Logic
```

Create a virtual environment and activate it:

```bash
python3 -m venv venv
source venv/bin/activate
```

Install Python dependencies:

```bash
pip install -r requirements.txt
```

---

### 4. 🐳 Build Docker

If your project includes Docker support, get into the folder app and run:

```bash
chmod +x ./build_docker.sh
./build_docker.sh
```

---

### 5. ▶️ Run the App

Without the virtual environment active, run:

```bash
chmod +x ./run.sh
./run.sh
```

Or

With the virtual environment active, run:

```bash
python3 run.py
```

---

## 🔁 Common Commands

- Stop Redis:

  ```bash
  sudo systemctl stop redis-server
  ```

- Deactivate virtual environment:

  ```bash
  deactivate
  ```

---

## 🔪 Troubleshooting

- **Redis not responding?**

  Restart it:

  ```bash
  sudo systemctl restart redis-server
  ```

  Or run manually:

  ```bash
  redis-server
  ```

- **Permission denied errors (Docker or files)?**

  Ensure you have correct permissions:

  ```bash
  sudo chown -R $(whoami) .
  ```

---

## 📌 Notes

- This project assumes Redis is running locally on default port `6379`.
