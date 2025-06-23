# 🌟Nginx Reverse Proxy Internship

A modern, production-ready microservices demo showcasing Nginx reverse proxy with Go and Python services.

## ✨ Key Features

- 🔄 **Smart Routing**: Nginx routes requests based on service paths
- 🔒 **Secure**: Internal services protected, only Nginx exposed
- 📊 **Monitored**: Health checks and detailed logging
- 🚀 **Scalable**: Easy horizontal scaling with Docker Compose

## 🏗️ Architecture

```
                    ┌─────────────┐
                    │             │
 Internet ─────────▶│    Nginx    │
                    │             │
                    └──────┬──────┘
                           │
                ┌─────────┴──────────┐
                │                    │
         ┌──────┴─────┐      ┌──────┴─────┐
         │            │      │            │
         │ Go Service │      │   Python   │
         │            │      │  Service   │
         └────────────┘      └────────────┘
```

## 🚀 Quick Start

1. **Clone & Build**
   ```bash
   git clone https://github.com/veerendra4401/Devops-Internship.git
   cd Devops-Internship
   docker-compose up --build
   ```

2. **Test Services**
   ```bash
   # Service 1 (Go)
   curl http://localhost:8080/service1/hello
   
   # Service 2 (Python)
   curl http://localhost:8080/service2/hello
   
   # Health Check
   curl http://localhost:8080/health
   ```

## 📡 Service Details

### Routing
- `/service1/*` → Go Service (Port 8001)
- `/service2/*` → Python Service (Port 8002)
- `/health` → Nginx Health Status

### Available Endpoints

| Service | Endpoint | Description |
|---------|----------|-------------|
| Service 1 | `/hello` | Returns greeting |
| Service 1 | `/ping` | Health check |
| Service 2 | `/hello` | Returns greeting |
| Service 2 | `/ping` | Health check |
| Nginx | `/health` | System health |

## 🛠️ Technical Features

### 1. Advanced Health Monitoring
- Health check endpoints on all services
- Docker container health checks
- Nginx status monitoring

### 2. Enhanced Logging
```nginx
# Custom log format with timestamps and request details
log_format custom '$time_local - $request_uri - $status';
```

### 3. Security
- Services run on internal network
- Only port 8080 exposed
- Secure service isolation

### 4. Docker Configuration
- Optimized Dockerfiles
- Bridge networking
- Easy scaling support

## 📁 Project Structure
```
.
├── docker-compose.yml    # Main configuration
├── nginx/               # Nginx reverse proxy
│   ├── nginx.conf      # Routing config
│   └── Dockerfile      # Nginx setup
├── service_1/          # Go service
│   ├── main.go        # Service code
│   └── Dockerfile     # Go setup
└── service_2/         # Python service
    ├── app.py        # Flask code
    └── Dockerfile    # Python setup
```

## 🔍 Monitoring & Logs

View service logs:
```bash
# All services
docker-compose logs -f

# Specific service
docker-compose logs -f nginx
```

## 🌐 Scaling

Scale any service:
```bash
# Run 3 instances of service1
docker-compose up --scale service1=3
```

---


