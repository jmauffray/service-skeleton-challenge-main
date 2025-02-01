FROM golang:1.22-alpine AS builder

ARG PORT

WORKDIR /app

COPY . .

RUN go build

FROM debian

COPY --from=builder /app/bin/go-service /go-service

ENV PORT=8080
EXPOSE $PORT

CMD ["/go-service"]
