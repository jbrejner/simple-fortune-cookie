# build stage
FROM golang:1.19-alpine3.16 AS builder
RUN mkdir /build
COPY . /build/.
WORKDIR /build
RUN CGO_ENABLED=0 GOOS=linux go build -a -o frontend .

# final stage
FROM scratch
EXPOSE 8080
ENV BACKEND_DNS=localhost
ENV BACKEND_PORT=9000
WORKDIR /app
COPY --from=builder /build/ .
ENTRYPOINT ["/app/frontend"]