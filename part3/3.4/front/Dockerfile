FROM ubuntu:18.04

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

ENV REACT_APP_BACKEND_URL=http://localhost:8000/api

RUN apt update && apt install curl -y && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash && \
    apt purge -y --auto-remove curl && \
    apt install -y nodejs && \
    npm install && \
    npm run build && \
    npm install -g serve && \
    useradd -m frontend && \
    chown -R frontend:frontend /usr/src/app &&\
    rm -rf /var/lib/apt/lists/* 

USER frontend

CMD ["serve", "-s", "-l", "5000", "build"]
