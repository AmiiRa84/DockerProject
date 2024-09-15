# Stage 1: Build Stage
# Use the official Golang 1.18 image based on Alpine Linux for a small image size
FROM golang:1.18-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the Go module files to the container
# These files are used for downloading the dependencies
COPY go.mod go.sum ./

# Download the Go module dependencies
RUN go mod download

# Copy the rest of the application source code to the container
COPY . ./

# Build the Go application and output the binary as "main"
RUN go build -o main .

# Stage 2: Runtime Stage
# Use the official Alpine image for a minimal runtime environment
FROM alpine:latest

# Set the working directory inside the container
WORKDIR /app

# Copy the compiled binary from the build stage to the runtime stage
COPY --from=builder /app/main /app/main

# Expose port 8000 to the outside world
EXPOSE 8000

# Define the default command to run the application when the container starts
CMD ["./main"]
