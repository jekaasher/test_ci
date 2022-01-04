# syntax=docker/dockerfile:1
FROM golang:1.16-alpine AS builder
WORKDIR /app
COPY app/go.mod    ./
COPY app/go.sum    ./
RUN go mod download
COPY app/*.go ./
RUN go build -o main

FROM alpine:latest  
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /app/main ./
CMD ["./dev"]  