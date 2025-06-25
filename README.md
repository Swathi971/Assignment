# Nginx Reverse Proxy with Docker Compose
## Project Overview
This project sets up two backend services using Docker, and an Nginx reverse proxy to route requests based on URL path. The entire system is orchestrated using Docker Compose.
---
## Setup Instructions
1. **Clone the repository**:
```commandline
git clone https://github.com/your-username/Nginx-Reverse-Proxy-Docker.git
cd Nginx-Reverse-Proxy-Docker
```
2. **Build and start all containers**:
```commandline
docker-compose up --build
```
3. **Access the services**:
* Service 1: http://localhost:8080/service1/ping
* Service 2: http://localhost:8080/service2/ping
---
## How Routing Works
Nginx listens on port 8080 and routes requests as follows:
* Requests to /service1/* are forwarded to Service 1 running on port 8001
* Requests to /service2/* are forwarded to Service 2 running on port 8002
This is handled by nginx.conf:
```commandline
location /service1/ {
    proxy_pass http://service_1:8001/;
}

location /service2/ {
    proxy_pass http://service_2:8002/;
}
```
---
## Health Checks
Docker Compose includes health checks for both services:
```commandline
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost:8001/ping"]
```
##### Output
```commandline
{"service": "service1"}
```
````
{"service": "service2"}
````