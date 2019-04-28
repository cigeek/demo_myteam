FROM golang as builder
#Default GOPATH --> /go/src
WORKDIR /go/src/mypackage/myapp/
COPY . .
RUN go get . && CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -ldflags '-w' -o web .
FROM scratch
COPY --from=builder /go/src/mypackage/myapp/web /app/
COPY --from=builder /go/src/mypackage/myapp/index.html /app/
WORKDIR /app
CMD ["./web"]
