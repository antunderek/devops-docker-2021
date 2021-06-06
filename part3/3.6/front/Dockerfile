FROM alpine:3.13 as build-stage

WORKDIR /usr/src/app

COPY . .

ENV REACT_APP_BACKEND_URL=http://localhost:8000/api

RUN apk add --no-cache nodejs npm && \
    npm install && \
    npm run build


FROM nginx:stable-alpine
EXPOSE 80
COPY --from=build-stage /usr/src/app/build /usr/share/nginx/html