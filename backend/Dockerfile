# build stage
FROM golang:1.19-alpine3.16 AS builder
RUN mkdir /build
COPY . /build/.
WORKDIR /build
RUN go mod download && go mod verify
RUN CGO_ENABLED=0 GOOS=linux go build -a -o backend .

# final stage
FROM scratch
EXPOSE 9000
WORKDIR /app
COPY --from=builder /build/ .
ENTRYPOINT ["/app/backend"]
