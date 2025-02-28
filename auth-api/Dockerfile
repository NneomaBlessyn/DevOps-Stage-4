# Build Stage
FROM golang:1.21-alpine AS builder

WORKDIR /app

# Copy and download dependencies separately to leverage Docker layer caching
COPY go.mod go.sum ./
RUN go mod download

# Copy the source code
COPY . .

# Build the application statically
RUN CGO_ENABLED=0 GOOS=linux go build -o auth-api .

# Final Stage
FROM alpine:latest

# Install CA certificates and clean up unnecessary cache
RUN apk add --no-cache ca-certificates

WORKDIR /root/

# Copy the built binary
COPY --from=builder /app/auth-api .

# Expose port
EXPOSE 8081

# Run the application
ENTRYPOINT ["./auth-api"]
