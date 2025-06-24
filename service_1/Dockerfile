FROM golang:1.24.3-alpine

WORKDIR /app

COPY main.go .
COPY go.mod .

RUN go build -o app .

EXPOSE 8001

CMD ["./app"]
