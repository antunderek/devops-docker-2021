FROM alpine:3.13

EXPOSE 8080

WORKDIR /usr/src/app

RUN apk update && apk add go

COPY . .

RUN go build
RUN go test ./...

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000

CMD ./server
