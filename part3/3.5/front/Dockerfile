FROM alpine:3.13

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

ENV REACT_APP_BACKEND_URL=http://localhost:8000/api

RUN apk add --no-cache nodejs npm && \
    npm install && \
    npm run build && \
    npm install -g serve && \
    addgroup -S frontend && adduser -S frontend -G frontend && \
    chown -R frontend:frontend /usr/src/app

USER frontend

CMD ["serve", "-s", "-l", "5000", "build"]
