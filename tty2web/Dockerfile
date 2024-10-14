# Build stage
FROM golang:1.23.2-alpine AS builder

WORKDIR /app

RUN apk add --no-cache git make

RUN git clone https://github.com/kost/tty2web .

RUN make tools 

RUN make tty2web

# Final stage
FROM alpine:3.17

WORKDIR /app

COPY --from=builder /app/tty2web /app/tty2web

EXPOSE 8080

ENTRYPOINT ["/app/tty2web"]
