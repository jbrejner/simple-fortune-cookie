# build stage
FROM golang:1.18

WORKDIR /usr/src/app

COPY . .

RUN go build -v -o /usr/local/bin/frontend ./...
EXPOSE 8080
ENV BACKEND_DNS=localhost
ENV BACKEND_PORT=9000

CMD ["frontend"]

# # final stage
# FROM scratch
# WORKDIR /app
# COPY --from=builder /src/goapp /app/
# ENTRYPOINT ["/app/goapp"]