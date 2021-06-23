FROM golang:1.16 as builder

WORKDIR /app

COPY go.mod .
COPY go.sum .

RUN go mod download

COPY *.go .

RUN CGO_ENABLED=0 GOOS=linux go build -v -o /main .

FROM gcr.io/distroless/static

COPY --from=builder /main .

EXPOSE 8080

CMD ["/main"]
