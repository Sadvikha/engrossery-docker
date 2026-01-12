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
├── grocery-frontend/Dockerfile
├── grocery-backend/Dockerfile
└── docker-compose.yml



### Why separate Dockerfiles?
- Each service has **independent dependencies**
- Enables **layer caching**
- Allows **individual image builds**
- Follows Docker best practices

---

## 🚀 Running Everything (One Command)

```bash
docker compose up

Run in background:

docker compose up -d


This command:

Pulls images (if not present)

Builds images (if configured)

Creates containers

Starts networking automatically
