FROM alpine:3.13

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:8000
ENV REDIS_HOST=redis


RUN apk add --no-cache go && \
    go build && \
    go test ./... && \
    addgroup -S backend && adduser -S backend -G backend && \
    chown -R backend:backend /usr/src/app

USER backend

CMD ./server
