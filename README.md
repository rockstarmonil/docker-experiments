# 🐳 Docker - Beginner to Advanced Guide

Welcome to the Docker README guide. This document is designed to help you understand what Docker is, why it is used, how it works, and a detailed explanation of all major Docker concepts from beginner to advanced levels.

---

## 📌 What is Docker?

**Docker** is an open-source platform that allows developers to automate the deployment, scaling, and management of applications in lightweight, portable containers.

A **Docker container** packages your application along with all its dependencies (like libraries, binaries, and configurations) to ensure it runs consistently across different environments.

---

## 🎯 Use Cases of Docker

- 🚀 **Simplified Application Deployment**
- 🧪 **Isolated Development Environments**
- 🔄 **CI/CD Pipelines (Automation)**
- ☁️ **Cloud-Native Application Development**
- 🧳 **Microservices Architecture**
- 🧪 **Testing Across Multiple Environments**
- 📦 **Environment Replication for Debugging**

---

## 🆚 Containerization vs Virtualization

| Feature              | Virtualization                          | Containerization                          |
|----------------------|------------------------------------------|-------------------------------------------|
| Architecture         | Hypervisor-based                         | Docker Engine-based                        |
| Size                 | GBs (heavy VMs)                          | MBs (lightweight containers)               |
| Startup Time         | Minutes                                  | Seconds                                    |
| OS                   | Full Guest OS per VM                     | Shares Host OS Kernel                      |
| Performance          | Slower due to full OS overhead           | Faster due to less overhead                |
| Resource Isolation   | High (uses entire hardware stack)        | Moderate (uses namespaces and cgroups)     |
| Portability          | Medium                                   | High                                       |

---

## 🧩 Docker Topics (Step-by-Step)

---

### 1. 🔧 Docker Installation

- [Install Docker on Linux/macOS/Windows](https://docs.docker.com/get-docker/)
- Verify installation:  
  ```bash
  docker --version


### 2. 🚀 Basic Docker Commands

* `docker pull <image>` – Pull image from Docker Hub
* `docker run <image>` – Run a container
* `docker ps` – List running containers
* `docker images` – List downloaded images
* `docker stop <container_id>` – Stop container
* `docker rm <container_id>` – Remove container
* `docker rmi <image_id>` – Remove image

---

### 3. 📦 Dockerfile (Create Custom Images)

A **Dockerfile** defines how to build an image step by step.

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

Build and run:

```bash
docker build -t my-python-app .
docker run -p 5000:5000 my-python-app
```

---

### 4. 🗂 Docker Volumes (Persistent Data)

Docker volumes allow data to persist even if the container is deleted.

* Create a volume:

  ```bash
  docker volume create mydata
  ```
* Bind it to a container:

  ```bash
  docker run -v mydata:/data ubuntu
  ```

---

### 5. 🌐 Docker Networks

#### Types of Docker Networks:

| Network Type | Description                            |
| ------------ | -------------------------------------- |
| **bridge**   | Default for single host communication  |
| **host**     | Uses host network stack (no isolation) |
| **none**     | No networking (isolated container)     |
| **overlay**  | Multi-host communication (Swarm)       |
| **macvlan**  | Assign MAC address directly            |

#### Create and use network:

```bash
docker network create my-bridge
docker run -d --name web --network my-bridge nginx
```

---

### 6. 🔗 Bind Mount vs Volume

| Feature          | Bind Mount             | Docker Volume             |
| ---------------- | ---------------------- | ------------------------- |
| Storage Location | Any path on host       | Managed by Docker         |
| Performance      | Slower for large files | Optimized                 |
| Backup/Easier    | Manual                 | Yes (via `docker volume`) |

**Example Bind Mount:**

```bash
docker run -v $(pwd)/data:/app/data my-app
```

---

### 7. 🧰 Docker Compose

Docker Compose allows you to define multi-container apps in a YAML file.

**docker-compose.yml:**

```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
  redis:
    image: redis
```

Commands:

```bash
docker-compose up --build
docker-compose down
```

---

### 8. 🛠 Docker Exec

Execute commands in a running container:

```bash
docker exec -it <container_id> bash
```

---

### 9. 📋 Docker Logs

View logs from a running container:

```bash
docker logs <container_id>
```

---

### 10. 📦 Docker Image Management

* Save image:

  ```bash
  docker save myapp > myapp.tar
  ```
* Load image:

  ```bash
  docker load < myapp.tar
  ```

---

### 11. 🚨 Docker Security Practices

* Use minimal base images (e.g., `alpine`)
* Keep images updated
* Don’t run containers as root
* Scan images for vulnerabilities (e.g., Docker Scout, Trivy)

---

### 12. 🔄 Docker Registry

Push and pull images to Docker Hub:

```bash
docker tag myapp username/myapp
docker push username/myapp
```

Private registry (optional):

```bash
docker run -d -p 5000:5000 --name registry registry:2
```

---

### 13. 🕸 Docker Swarm (Intro to Orchestration)

* Cluster your Docker hosts
* Deploy services with `docker service` command
* Not as widely used now (Kubernetes is preferred)

---

## ✅ Summary

Docker simplifies software development and deployment by offering lightweight containers with built-in networking, volume management, and orchestration. It's essential for microservices, CI/CD, and modern DevOps workflows.

---
