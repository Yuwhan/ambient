FROM golang AS builder

WORKDIR /app
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM scratch

WORKDIR /
COPY .env .
COPY --from=builder /app/app .

CMD ["/app"]