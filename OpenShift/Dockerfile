FROM ubuntu:18.04


RUN apt-get update
RUN apt-get install -y wget
RUN apt-get install -y curl
RUN curl -L https://github.com/docker/machine/releases/download/v0.16.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine && \
    chmod +x /tmp/docker-machine && \
    sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
RUN wget https://github.com/openshift/origin/releases/download/v3.9.0/openshift-origin-client-tools-v3.9.0-191fece-linux-64bit.tar.gz
RUN tar -zvxf openshift-origin-client-tools-v3.9.0-191fece-linux-64bit.tar.gz
RUN docker info
RUN docker run hello-world
RUN su - \
cat << EOF > /etc/docker/daemon.json \
{ \
    "insecure-registries" : [ "172.30.0.0/16" ] \
} \
EOF
RUN service docker restart
WORKDIR openshift-origin-client-tools-v3.9.0-191fece-linux-64bit
RUN ls -l && pwd
RUN oc cluster up

