FROM alpine:latest

WORKDIR /usr/src/app

COPY webserver.go .

RUN apk update && apk upgrade
RUN apk add go git

RUN go get -u github.com/gin-gonic/gin

CMD go run webserver.go
