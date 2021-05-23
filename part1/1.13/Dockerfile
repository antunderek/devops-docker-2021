FROM alpine:3.13

EXPOSE 8080

WORKDIR /usr/src/app

RUN apk update && apk add go

COPY . .

RUN go build
RUN go test ./...

CMD ./server
