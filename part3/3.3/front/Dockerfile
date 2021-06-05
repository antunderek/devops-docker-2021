FROM ubuntu:xenial

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN apt update && apt install curl -y

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash
RUN apt install -y nodejs

RUN npm install

ENV REACT_APP_BACKEND_URL=http://localhost:8000/api

RUN npm run build

RUN npm install -g serve

RUN useradd -m frontend
RUN chown -R frontend:frontend /usr/src/app
USER frontend

CMD ["serve", "-s", "-l", "5000", "build"]
