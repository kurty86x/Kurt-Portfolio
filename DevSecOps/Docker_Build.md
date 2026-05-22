# 📝 Overview
This project demonstrates how I used Docker to containerize a simple web application and run it in a controlled, repeatable environment. 

The goal was to learn how images, containers, Dockerfiles, and multi‑container setups work — all foundational DevSecOps skills.

--- 

### 🎯 Objectives
- Build a Docker image from a Dockerfile
- Run containers locally
- Use docker-compose for multi‑service apps
- Manage environment variables and ports
- Apply basic container security practices

---

### 🏗️ Lab Environment
- Docker Engine installed on Linux/Windows
- Docker Compose v2
- Simple web app (Python Flask, Node.js, or static HTML)
- Terminal access

---

### 📁 Project Structure
```
docker-deployment/
│── app/
│     └── app.py (or index.html)
│── Dockerfile
│── docker-compose.yml
└── docs/
```
---

## 🐳 Building the Docker Image

### Dockerfile

```
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
```

### Build the image
```
Command:
docker build -t myapp:1.0
```

### Verify the image
```
docker images
```

## ▶️ Running the Container
```
Command:
docker run -d -p 5000:5000 --name myapp-container myapp:1.0
```

### Check logs
```
Command:
docker logs myapp-container
```

### Stop the container
```
Command:
docker stop myapp-container
```

---

## 🧩 Multi‑Container Setup (docker‑compose)

docker-compose.yml
```
version: "3.9"

services:
  web:
    image: myapp:1.0
    ports:
      - "5000:5000"
    environment:
      - APP_ENV=production
    restart: always
```

### Start the stack
```
Command:
docker compose up -d
```

### Stop the stack
```
Command:
docker compose down
```

---

## 🔐 Basic Container Security Practices
- Used official base images (python:3.10-slim)
- Avoided running as root
- Exposed only required ports
- Used .dockerignore to avoid leaking secrets
- Kept environment variables minimal

---

## 🧪 Validation Checklist
- App loads in browser at http://localhost:5000
- Container restarts automatically if stopped
- Logs show no errors
- Image size is reasonable
- No sensitive files included in the image

---

## 🛠️ Troubleshooting
- **Port already in use**
  ```
  Command:
  sudo lsof -i :5000
  ```
- **Container exits immediately**  
  Check logs:
  ```
  Command:
  docker logs myapp-container
  ```
- **Image too large** 

  Switch to a slimmer base image like alpine (if compatible).

---

## 📘 What I Learned
- How to build and run Docker containers
- How Dockerfiles define application environments
- How to use docker‑compose for multi‑service apps
- How containerization improves consistency and portability
- How to apply basic container security practices