# Microsoft Fabric

# Spark Engineering Excellence Workshop

## Attendee Prerequisites Guide

Welcome! To make the most of our hands-on workshop, please complete the following prerequisites before the session.

This guide is organized into two sections:

1. Setting up your local Spark environment using **Docker + WSL**
2. Building foundational **Spark knowledge**

**Estimated setup time:** 30–60 minutes

---

## 1) Local Spark Environment (Docker + WSL)

One of the highlights of this workshop is the opportunity to run Spark code locally inside a Docker container—similar to how engineering teams develop and test pipelines before deploying to production.

### Why run Spark locally first?

- Validate your code logic before submitting to Fabric (fast feedback, no cluster spin-up time)
- Mirror a practical inner-loop workflow used by many engineering teams
- Build confidence with containerized Spark environments used across the industry
- Catch configuration and dependency issues early in a safe, local sandbox

---

### 1.1 Install WSL (Windows Subsystem for Linux)

WSL allows you to run a Linux environment natively on Windows—a key dependency for running Docker Desktop smoothly with WSL 2.

#### Step 1 — Enable WSL 2

Open **PowerShell as Administrator** and run:

```powershell
wsl --install
```

#### Step 2 — Set WSL 2 as default

```powershell
wsl --set-default-version 2
```

#### Step 3 — Restart your machine

A restart is required to complete WSL installation.

#### Step 4 — Verify installation

Open PowerShell and confirm WSL is running:

```powershell
wsl --list --verbose
```

**Full guide:**

- Microsoft WSL Documentation: https://learn.microsoft.com/windows/wsl/install

---

### 1.2 Install Docker Desktop

Docker Desktop is what we’ll use to spin up a containerized PySpark environment locally.

#### Step 1 — Download Docker Desktop

Download the installer from the official Docker website:

- https://www.docker.com/products/docker-desktop/

#### Step 2 — Install Docker Desktop

Run the installer. During setup, ensure **“Use WSL 2 instead of Hyper-V”** is checked.

#### Step 3 — Start Docker Desktop

Launch Docker Desktop and wait for it to show a green **“Engine running”** status.

#### Step 4 — Verify installation

Open a terminal (**WSL** or **PowerShell**) and run:

```bash
docker --version
```

Then run a quick test container:

```bash
docker run --rm hello-world
```

---

### 1.3 Verify Your Spark Container Works (Smoke Test)

This smoke test confirms your environment is ready for the workshop.

> Tip: The commands below are easiest to run from a **WSL terminal** (Ubuntu, etc.), especially if you want to mount local files into the container.

#### Step 1 — Pull the PySpark Docker image

```bash
docker pull jupyter/pyspark-notebook
```

#### Step 2 — Start the container (Jupyter + Spark)

From a WSL terminal, run:

```bash
docker run --rm -it \
  -p 8888:8888 \
  -v "$(pwd)":/home/jovyan/work \
  jupyter/pyspark-notebook
```

What this does:

- Exposes Jupyter on `http://localhost:8888`
- Mounts your current folder into the container at `/home/jovyan/work`

#### Step 3 — Open Jupyter

- Open the URL shown in the terminal output (typically `http://localhost:8888/?token=...`), or
- Open `http://localhost:8888` and paste the token printed in the container logs.

#### Step 4 — Confirm Spark runs and prints a version

In a new notebook cell, run one of the following:

Option A (often available by default in this image):

```python
spark.version
```

Option B (explicitly create/get a Spark session):

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.getOrCreate()
print(spark.version)
```

✅ You’re all set if…

- `docker --version` returns a version number (e.g., Docker version 26.x.x)
- `docker run --rm hello-world` prints “Hello from Docker!”
- `spark.version` prints a Spark version (e.g., 3.5.x)
- No errors appear during container startup

---

## 2) Spark Knowledge Prerequisites

This workshop assumes basic familiarity with Apache Spark concepts. You don’t need to be an expert, but having a solid foundation will help you get more value from the advanced Fabric-specific content.

### Core concepts to review

- DataFrames and Spark SQL basics
- Transformations vs. actions
- Lazy evaluation
- Partitions and shuffles (why they happen)
- Joins (broadcast vs. shuffle), groupBy, aggregations
- Caching/persisting

### Free online learning resources

- Apache Spark Documentation (start here): https://spark.apache.org/docs/latest/
- Spark SQL, DataFrames and Datasets Guide: https://spark.apache.org/docs/latest/sql-programming-guide.html
- RDD Programming Guide (optional background): https://spark.apache.org/docs/latest/rdd-programming-guide.html

### Video learning (choose any)

- Search YouTube for: “Apache Spark DataFrames transformations actions lazy evaluation”
- Search YouTube for: “Spark shuffle partitioning joins broadcast join”

### Good blogs / reading prompts

If you prefer reading, search for these topics:

- “Spark shuffle explained”
- “Spark AQE adaptive query execution”
- “Spark partitioning best practices”
- “Spark skew handling salting broadcast join”

---

## Pre-Workshop Checklist

Complete this checklist before the workshop day. Bring your laptop with all items below ready to go.

- [ ] WSL 2 is installed and running on my machine
- [ ] Docker Desktop is installed and shows “Engine running” status
- [ ] `docker run --rm hello-world` ran successfully
- [ ] I pulled the PySpark Docker image (`jupyter/pyspark-notebook`)
- [ ] I ran a test Spark session in Jupyter and it printed a Spark version
- [ ] I’ve reviewed core Spark concepts (transformations, actions, DataFrames)
- [ ] My laptop is charged and I have my charger with me

---

## Questions or Issues?

If you run into any issues setting up your environment, reach out to the workshop team before the session—we’re here to help.

We look forward to seeing you there!