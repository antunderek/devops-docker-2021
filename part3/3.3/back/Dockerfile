FROM alpine:3.13

EXPOSE 8080

WORKDIR /usr/src/app

RUN apk update && apk add go

COPY . .

RUN go build
RUN go test ./...

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:8000
ENV REDIS_HOST=redis

RUN addgroup -S backend && adduser -S backend -G backend
RUN chown -R backend:backend /usr/src/app
USER backend

CMD ./server
