# Use official Golang image
FROM golang:1.22

# Set working directory inside container
WORKDIR /app

# Copy source code into container
COPY . .

# Build the Go app
RUN go build -o app .

# Expose port 5000
EXPOSE 5000

# Command to run the app
CMD ["./app"]

