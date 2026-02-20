# Microsoft Fabric 🧵

# Spark Engineering Excellence Workshop ⚡

## Attendee Prerequisites Guide ✅

Welcome! We’re excited to have you join the workshop. To get the most out of our hands-on session, please complete the prerequisites below **before** the workshop starts. 🙌

This guide is organized into two parts:

1. 🐳 **Set up your local Spark environment** using **Docker + WSL**
2. 🧠 **Build (or refresh) foundational Spark knowledge**

⏱️ **Estimated setup time:** 30–60 minutes

---

## 1) Local Spark Environment (Docker + WSL) 💻🐳

One of the highlights of this workshop is running Spark code locally inside a Docker container in Lab 4, similar to how engineering teams develop and test pipelines before deploying to production. 🚀

### Why run Spark locally first? 🤔

- ⚡ Validate your code logic before submitting to Fabric (fast feedback, no cluster spin-up time)
- 🔁 Mirror a practical inner-loop workflow used by many engineering teams
- 🧱 Build confidence with containerized Spark environments used across the industry
- 🛠️ Catch configuration and dependency issues early in a safe, local sandbox

---

### 1.1 Install WSL (Windows Subsystem for Linux) 🐧🪟

WSL lets you run a Linux environment natively on Windows—a key dependency for running Docker Desktop smoothly with WSL 2.

#### Step 1 — Enable WSL 2 ✅

Open **PowerShell as Administrator** and run:

```powershell
wsl --install
```

#### Step 2 — Set WSL 2 as default ⚙️

```powershell
wsl --set-default-version 2
```

#### Step 3 — Restart your machine 🔄

A restart is required to complete the WSL installation.

#### Step 4 — Verify installation 🔍

Open PowerShell and confirm WSL is running:

```powershell
wsl --list --verbose
```

📚 **Full guide:**
- Microsoft WSL Documentation: https://learn.microsoft.com/windows/wsl/install

---

### 1.2 Install Docker Desktop 🐳

Docker Desktop is what we’ll use to spin up a containerized PySpark environment locally.

#### Step 1 — Download Docker Desktop ⬇️

Download the installer from the official Docker website:
- https://www.docker.com/products/docker-desktop/

#### Step 2 — Install Docker Desktop 🧩

Run the installer. During setup, ensure **“Use WSL 2 instead of Hyper-V”** is checked ✅

#### Step 3 — Start Docker Desktop ▶️

Launch Docker Desktop and wait for it to show a green **“Engine running”** status 🟢

#### Step 4 — Verify installation 🧪

Open a terminal (**WSL** or **PowerShell**) and run:

```bash
docker --version
```

Then run a quick test container:

```bash
docker run --rm hello-world
```

If you see “Hello from Docker!” — you’re in great shape. 🎉

---

### 1.3 Verify Your Spark Container Works (Smoke Test) 🔥✅

This smoke test confirms your environment is ready for the workshop.

#### Step 1 — Pull the Docker image 📦 (Raki to update)

_(Add the exact commands for stup)_

#### Step 2 — Confirm Spark runs and prints a version 🧾

In the shell, run PySpark.

✅ **You’re all set if…**

- 🐳 `docker --version` returns a version number (e.g., Docker version 26.x.x)
- ✅ `docker run --rm hello-world` prints “Hello from Docker!”
- ⚡ `spark.version` prints a Spark version (e.g., 3.5.x)
- 🧘 No errors appear during container startup

---

## 2) Spark Knowledge Prerequisites 🧠⚡

This workshop assumes basic familiarity with Apache Spark concepts. You don’t need to be an expert but having a solid foundation on Spark is important to get more value from the advanced Fabric Spark content. 💪

### Core concepts to review 📚

- 🧾 DataFrames and Spark SQL basics
- 🔄 Transformations vs. actions
- 💤 Lazy evaluation
- 🧩 Partitions and shuffles (why they happen)
- 🔗 Joins (broadcast vs. shuffle), groupBy, aggregations
- 🧊 Caching/persisting
- 🔄 Spark Structured Streaming

### Video learning 🎥

Spark Learning Series:
https://learning.oreilly.com/videos/apache-spark-3/9781803241555/9781803241555-video2_2/

Spark Streaming Execution Model: 
https://www.youtube.com/watch?v=zx5H82fmUPU&list=PLgPb8HXOGtsQeiFz1y9dcLuXjRh8teQtw&index=21

---

## Pre-Workshop Checklist 📝✅

Complete this checklist before the workshop day. Bring your laptop with all items below ready to go. 🔌💻

- [ ] 🐧 WSL 2 is installed and running on my machine
- [ ] 🐳 Docker Desktop is installed and shows “Engine running” status 🟢
- [ ] ✅ `docker run --rm hello-world` ran successfully
- [ ] 📦 I pulled the Spark Docker image 
- [ ] 📚 I’ve reviewed core Spark concepts
