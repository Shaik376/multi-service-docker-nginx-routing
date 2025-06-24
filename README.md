
# DevOps Project: Nginx Reverse Proxy with Dockerized Services

## 📑 Overview
This project sets up a simple microservices architecture using:
- **Service 1:** Golang HTTP server  
- **Service 2:** Python Flask API  
- **Nginx:** Reverse proxy routing requests to the two services  

Each service runs in its own Docker container, and Nginx routes incoming requests based on URL paths.

---

## 📦 Setup Instructions

1️⃣ **Clone this repository**
```bash
git clone <your-repo-url>
cd devops_project
````

2️⃣ **Build and start all containers**

```bash
sudo docker-compose up --build
```

3️⃣ **Check running containers**

```bash
docker ps
```

---

## 🌐 How Routing Works

| Route                                  | Routed To                                                   |
| :------------------------------------- | :---------------------------------------------------------- |
| `http://localhost:8080/service1/ping`  | Service 1 (Golang server at port 5000 inside its container) |
| `http://localhost:8080/service1/hello` | Service 1                                                   |
| `http://localhost:8080/service2/ping`  | Service 2 (Flask API at port 5001 inside its container)     |
| `http://localhost:8080/service2/hello` | Service 2                                                   |

**Nginx** listens on **port 8080** and forwards requests internally to the correct container and service port via Docker’s internal bridge network.

---

## 🎁 Bonus Features

✅ **Health Checks:**
Both services include Docker health checks via `/ping` endpoints.
Nginx waits for both services to report healthy before starting, using:

```yaml
depends_on:
  service1:
    condition: service_healthy
  service2:
    condition: service_healthy
```

✅ **Docker Logs Routing Visibility:**
Use this command to view Nginx request logs:

```bash
sudo docker logs nginx_reverse_proxy
```

You’ll see logs for each routed request, like:

```
GET /service1/ping HTTP/1.1" 200 -
```

---

## 📌 Tech Constraints

* ✅ Nginx runs inside a Docker container
* ✅ Uses Docker bridge networking (no host networking)

---

## 📋 To Stop Containers

```bash
sudo docker-compose down
```

---


