FROM golang:1.16 as builder

WORKDIR /app

COPY go.mod .
COPY go.sum .

RUN go mod graph | awk '{if ($1 !~ "@") print $2}' | xargs go get
#RUN go mod download

COPY *.go .

RUN CGO_ENABLED=0 GOOS=linux go build -v -o /app/main .

FROM gcr.io/distroless/static

COPY --from=builder /app/main /

EXPOSE 8080

CMD ["/main"]
