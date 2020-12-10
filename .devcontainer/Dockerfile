# There may be a newer version
FROM docker:19.03.14-dind-rootless
USER root

# Install your dependencies, this can be changed
RUN apk add --no-cache git bash curl sudo make py-pip

# azcli
RUN apk add --virtual=build gcc libffi-dev musl-dev openssl-dev python3-dev
RUN pip install azure-cli
RUN apk del --purge build

# kubectl 
RUN sudo az aks install-cli

# helm 2.14.2
RUN curl -OL https://get.helm.sh/helm-v2.14.2-linux-amd64.tar.gz
RUN tar xvf helm-v2.14.2-linux-amd64.tar.gz
RUN cp linux-amd64/helm /usr/local/bin/

# helm 3.4.2
#RUN curl -OL https://get.helm.sh/helm-v3.4.2-linux-amd64.tar.gz
#RUN tar xvf helm-v3.4.2-linux-amd64.tar.gz
#RUN cp linux-amd64/helm /usr/local/bin/

# Set the user back to the rootless user
USER rootless

# Setup docker
ENV DOCKER_HOST=unix:///var/run/user/1000/docker.sock

