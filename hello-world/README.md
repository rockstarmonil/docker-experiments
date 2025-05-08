
# 🐳 Hello World Docker Container

This is a minimal Docker project that prints `Hello, World!` using the Alpine Linux base image. It’s great for testing your Docker setup or understanding the basics of Dockerfiles.


## 📁 Files

- `Dockerfile` — Defines the image and startup behavior
- `README.md` — Project documentation


## 🧱 Dockerfile Content

```Dockerfile
FROM alpine:latest
CMD ["echo", "Hello, World!"]


🚀 How to Use

 1. Clone the Repository (if on GitHub)

git clone https://github.com/rockstarmonil/docker-experiments.git
cd docker-experiments/hello-world


2. Build the Docker Image

docker build -t hello-world .


3. Run the Container

docker run hello-world


✅ Output

Hello, World!


📦 Base Image

This container uses the `alpine:latest` image — a tiny, fast, and secure Linux distribution (\~5MB).
