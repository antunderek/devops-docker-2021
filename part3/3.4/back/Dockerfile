FROM ubuntu:18.04

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

ENV PATH="${PATH}:/usr/local/go/bin"
ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:8000
ENV REDIS_HOST=redis


RUN apt update && apt install -y curl && \
    curl -O https://storage.googleapis.com/golang/go1.16.5.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go1.16.5.linux-amd64.tar.gz && \
    rm go1.16.5.linux-amd64.tar.gz && \
    apt install -y gcc && \
    go build && \
    go test ./... && \
    apt purge -y gcc && \
    useradd -m backend && \
    chown -R backend:backend /usr/src/app

USER backend

CMD ./server
