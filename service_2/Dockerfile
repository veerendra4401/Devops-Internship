# Build stage
FROM python:3.11-slim as builder

WORKDIR /app

# Install uv
RUN pip install uv

# Copy dependency files
COPY requirements.txt pyproject.toml ./

# Create venv and install dependencies using uv
RUN uv venv
RUN . .venv/bin/activate && uv pip install -r requirements.txt

# Final stage
FROM python:3.11-slim

WORKDIR /app

# Copy virtual environment from builder
COPY --from=builder /app/.venv /app/.venv

# Copy application code
COPY app.py .

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
    CMD wget --quiet --tries=1 --spider http://localhost:8002/ping || exit 1

# Set PATH to use the venv
ENV PATH="/app/.venv/bin:$PATH"

# Run the application
CMD ["python", "app.py"] 