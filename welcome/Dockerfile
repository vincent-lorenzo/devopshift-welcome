FROM ubuntu:20.04 as builder 

ENV TZ=Asia/Jerusalem
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Combine update and install, and remove specific version tags to avoid "Not Found" errors
RUN apt-get update && apt-get install -qy \
    git \
    openjdk-8-jdk \
    iputils-ping \
    patchelf \
    default-jdk \
    plantuml \
    doxygen \
    graphviz \
    xsltproc \
    python3-pip \
    curl \
    vim \
    cifs-utils \
    nfs-common \
    && apt-get -qy autoremove && rm -rf /var/lib/apt/lists/*

RUN pip3 install requests==2.22.0 && \
    pip3 install Atlassian-python-API && \
    git config --global http.sslVerify false

RUN mkdir -p /home/ciuser/sdk && \
    mkdir -p /home/ciuser/.jfrog && \
    mkdir -p /home/ciuser/.ssh