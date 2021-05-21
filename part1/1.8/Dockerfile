FROM ubuntu:18.04

WORKDIR /home/

COPY script.sh .

RUN apt update && apt install curl -y
RUN chmod +x script.sh

CMD ./script.sh
