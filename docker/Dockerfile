FROM ubuntu:18.04

RUN sed -i 's/http:\/\/archive.ubuntu.com\/ubuntu\//http:\/\/mirror.math.princeton.edu\/pub\/ubuntu\//' /etc/apt/sources.list
RUN apt-get update
RUN apt-get -y install curl
RUN apt-get -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"
RUN apt-get -y install docker-ce

CMD nohup dockerd && \
    docker import /exec/piston.tar && \
    sleep infinity
