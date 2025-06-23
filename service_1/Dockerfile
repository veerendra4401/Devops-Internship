FROM golang:1.21-alpine

WORKDIR /app

# Copy Go module files
COPY go.mod .
COPY main.go .

# Build the application
RUN go build -o main .

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
    CMD wget --quiet --tries=1 --spider http://localhost:8001/ping || exit 1

# Run the application
CMD ["./main"] 