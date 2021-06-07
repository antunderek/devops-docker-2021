FROM alpine:3.13 as build-stage
WORKDIR /usr/src/app
COPY . .
RUN apk update && apk add --no-cache go && \
    CGO_ENABLED=0 go build -ldflags '-extldflags "-static"' -tags timetzdata && \
    go test ./... && \
    addgroup -S backend && adduser -S backend -G backend && \
    chown -R backend:backend /usr/src/app


FROM scratch
EXPOSE 8080
ENV REDIS_HOST=redis
ENV REQUEST_ORIGIN=http://localhost:8000
COPY --from=build-stage /usr/src/app/server /server
COPY --from=build-stage /etc/passwd /etc/passwd
COPY --from=build-stage /etc/group /etc/group
USER backend
CMD ["/server"]