# Docker Lab: Flask Application in a Container

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)

## 📋 Overview

This project demonstrates how to containerize a simple Flask web application using Docker. The application runs in an isolated container environment and can be easily deployed anywhere Docker is supported.

## 🚀 Features

- **Lightweight Python Flask Application** - Simple web server returning "Hello from Docker!"
- **Docker Containerization** - Application packaged with all dependencies
- **Port Mapping** - Accessible on localhost:5000
- **Optimized Image** - Uses `python:3.9-slim` for minimal image size

## 📁 Project Structure

```
docker-lab/
├── app.py              # Flask application
├── Dockerfile          # Docker build instructions
├── .dockerignore       # Files to exclude from Docker image
├── image/              # Screenshots and documentation images
│   ├── docker-build.png
│   ├── docker-run.png
│   └── flask-app-browser.png
└── README.md           # This file
```

## 🛠️ Prerequisites

- Docker Desktop or Docker Engine installed
- Basic knowledge of command line
- Git (for cloning the repository)

## 📦 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/valensniyonkuru/docker-lab.git
cd docker-lab
```

### 2. Build the Docker Image

```bash
docker build -t flask-app .
```

**Build Output:**

![Docker Build](image/docker-build.png)

### 3. Run the Container

```bash
docker run -d -p 5000:5000 flask-app
```

**Container Running:**

![Docker Run](image/docker-run.png)

### 4. Access the Application

Open your browser and navigate to:

```
http://localhost:5000
```

**Application Output:**

![Flask App](image/flask-app-browser.png)

## 📝 File Descriptions

### app.py

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return 'Hello from Docker!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

### Dockerfile

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install flask
EXPOSE 5000
CMD ["python", "app.py"]
```

## 🎯 Docker Commands Reference

### View Running Containers

```bash
docker ps
```

### View All Containers (including stopped)

```bash
docker ps -a
```

### View Container Logs

```bash
docker logs <container-id>
```

### Stop the Container

```bash
docker stop <container-id>
```

### Remove the Container

```bash
docker rm <container-id>
```

### View Docker Images

```bash
docker images
```

### Remove the Image

```bash
docker rmi flask-app
```

## 🔧 Troubleshooting

**Port already in use?**

```bash
# Use a different port
docker run -d -p 8080:5000 flask-app
# Access at http://localhost:8080
```

**Container not starting?**

```bash
# Check container logs
docker logs <container-id>
```

## 📚 What You'll Learn

- ✅ Creating a Dockerfile
- ✅ Building Docker images
- ✅ Running containers with port mapping
- ✅ Using `.dockerignore` for optimization
- ✅ Managing containers and images
- ✅ Best practices for Python containerization

## 🎓 Key Concepts

- **Base Image**: `python:3.9-slim` - A minimal Python image
- **Working Directory**: `/app` - Where the application code lives
- **Port Exposure**: `5000` - Application port
- **Detached Mode**: `-d` flag runs container in background
- **Port Mapping**: `-p 5000:5000` maps host port to container port

## 🌟 Next Steps

- Add a `requirements.txt` for better dependency management
- Implement multi-stage builds for even smaller images
- Add environment variables for configuration
- Set up Docker Compose for multi-container applications
- Push image to Docker Hub

## 👤 Author

**Valens Niyonkuru**

- GitHub: [@valensniyonkuru](https://github.com/valensniyonkuru)

## 📄 License

This project is open source and available for educational purposes.

---

**⭐ If you found this helpful, please give it a star!**
