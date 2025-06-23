FROM python:3.11-slim

WORKDIR /app

# Copy requirements
COPY pyproject.toml uv.lock ./

# Install dependencies
RUN pip install flask

# Copy application code
COPY app.py .

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
    CMD wget --quiet --tries=1 --spider http://localhost:8002/ping || exit 1

# Run the application
CMD ["python", "app.py"] 