FROM golang:alpine AS builder

RUN apk update && apk add --no-cache git

WORKDIR $GOPATH/src/app
COPY src/hello.go $GOPATH/src/app

RUN go get -d -v \
	&& go build -o /go/bin/hello


FROM scratch

COPY --from=builder /go/bin/hello /app/hello

ENTRYPOINT ["/app/hello"]
