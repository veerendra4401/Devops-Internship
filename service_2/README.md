# Python Service (Service 2)

A Flask microservice using modern Python tooling with uv.

## Features

- Fast dependency management with uv
- Multi-stage Docker build for smaller images
- Pinned dependencies for reproducibility
- Health check endpoint

## Development

### Local Setup with uv

1. Install uv:
   ```bash
   pip install uv
   ```

2. Create virtual environment:
   ```bash
   uv venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   uv pip install -r requirements.txt
   ```

4. Run the service:
   ```bash
   python app.py
   ```

### Docker Build

```bash
docker build -t service2 .
docker run -p 8002:8002 service2
```

## Why uv?

- 🚀 10-100x faster than pip
- 📦 Better dependency resolution
- 🔒 Reproducible builds
- 🛠️ Modern Python tooling
- 💾 Smaller image size with multi-stage builds

## API Endpoints

- `GET /hello` - Returns greeting message
- `GET /ping` - Health check endpoint

## Configuration

- Port: 8002
- Python version: 3.11
- Dependencies: See requirements.txt

### 📘 Service 2 – Python Flask API

This is a lightweight HTTP service written in Python using Flask. It exposes two simple endpoints and is designed to be used behind a reverse proxy like Nginx.

---

### 🔧 Endpoints

| Method | Path     | Description      | Response Example                      |
| ------ | -------- | ---------------- | ------------------------------------- |
| GET    | `/ping`  | Health check     | `{"status": "ok", "service": "2"}`    |
| GET    | `/hello` | Greeting message | `{"message": "Hello from Service 2"}` |

---

### 🚀 Running Locally

#### Prerequisites

* uv - https://docs.astral.sh/uv/getting-started/installation/

#### Run with Python:

```bash
uv run app.py
```

This will start the server on port `8002`.

---


Then visit:

* [http://localhost:8002/ping](http://localhost:8002/ping)
* [http://localhost:8002/hello](http://localhost:8002/hello)

---

### 📂 Project Structure

```
service2/
├── Dockerfile
├── app.py
└── README.md
```

# Update all dependencies
uv pip compile service_2/requirements.txt

# Show installed packages
uv pip list

# Install a specific package
uv pip install flask==3.0.0
