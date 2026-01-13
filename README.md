# 🐳 Docker Setup - Engrossery

This repository demonstrates **Dockerizing a multi-service application** using:

- Docker images
- Docker containers
- Docker Compose
- Docker Hub

The goal is to provide a **single-command setup** for any new developer.

---

## 🧱 Docker Components Used

### Docker Images
- `sadvikham/engrossery-frontend:latest`
- `sadvikham/engrossery-backend:latest`
- `mongo:7` (official image)

> Docker Hub stores **images only**, not containers.

---

### Docker Containers
Containers are **runtime instances** created from images.

| Container | Source Image |
|---------|-------------|
| engrossery-frontend | engrossery-frontend |
| engrossery-backend | engrossery-backend |
| engrossery-mongo | mongo:7 |

Each time an image is run, **a new container is created**.

---

## 🧩 Docker Compose Role

`docker-compose.yml` is responsible for:

- Starting **multiple containers together**
- Creating a **shared network**
- Managing **environment variables**
- Controlling **port mappings**
- Ensuring **correct startup order**

Compose **does not store containers or images** — it only **orchestrates them**.

---

## 📁 Docker Files Structure

engrossery-docker
- ├── grocery-frontend/Dockerfile
- ├── grocery-backend/Dockerfile
- └── docker-compose.yml



### Why separate Dockerfiles?
- Each service has **independent dependencies**
- Enables **layer caching**
- Allows **individual image builds**
- Follows Docker best practices

---

## 🚀 Running Everything (One Command)

```bash
docker compose up
```

### Run in background:
```bash
docker compose up -d
```
### This command:

- Pulls images (if not present)

- Builds images (if configured)

- Creates containers

- Starts networking automatically


## Running the Project

There are two ways to run the Engrossery project, depending on what you need:

### Purpose 1: Quick Run / Demo / Read-Only Mode  
(For testing, stakeholders, or anyone who just wants to see the app working without editing code)

This uses **pre-built images** from Docker Hub - fastest startup, no build required, and **guaranteed consistency** (no "it doesn't work on my system" issues).

```bash
# 1. Clone the repo (only docker-compose.yml is needed)
git clone https://github.com/sadvikha/Engrossery_.git
cd Engrossery_

# 2. Pull the pre-built images
docker pull sadvikham/engrossery-frontend:latest
docker pull sadvikham/engrossery-backend:latest

# 3. Start the app (fast!)
docker compose up -d

# 4. Check status (optional)
docker compose ps

# 5. Open in browser
# Frontend: http://localhost:5173
# Backend (test): http://localhost:5000

# Stop when done
docker compose down
```
Best for: Quick verification, demos, or non-developers.
Limitation: You cannot edit code - it's a frozen snapshot.

### Purpose 2: Development / Editing / Contributing Mode
(For developers who need to edit code, add features, fix bugs)
This builds everything from source code - allows full editing while still ensuring perfect environment consistency across machines.

```bash
# 1. Clone the full repo
git clone https://github.com/sadvikha/Engrossery_.git
cd Engrossery_

# 2. Open in VS Code (recommended)
code .

# 3. Edit code (frontend/src/, backend/src/, etc.) → save files

# 4. Rebuild images from your changes + restart
docker compose up --build -d

# 5. Test in browser (repeat edit → rebuild as needed)
# Frontend: http://localhost:5173

# 6. When ready, commit & push
git add .
git commit -m "Added new cart feature"
git push origin main

# Stop when done
docker compose down
```
Best for: Developers, contributors, feature work.
Why Docker helps here: Every build uses the exact same Node version, dependencies, and setup - no compatibility problems ever.
