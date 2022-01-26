FROM ubuntu:bionic

ARG DOCKER_COMPOSE_VERSION

# https://docs.docker.com/compose/install/
RUN \
   apt-get -y update && \
   apt-get -y install ca-certificates curl docker.io python3.7 && \
   curl https://dl.google.com/dl/cloudsdk/release/google-cloud-sdk.tar.gz > /tmp/google-cloud-sdk.tar.gz && \
   mkdir -p /usr/local/gcloud && \
   tar -C /usr/local/gcloud -xvf /tmp/google-cloud-sdk.tar.gz && \
   /usr/local/gcloud/google-cloud-sdk/install.sh --quiet && \
   rm -rf /var/lib/apt/lists/* && \
   curl -L "https://github.com/docker/compose/releases/download/${DOCKER_COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
   chmod +x /usr/local/bin/docker-compose

ENV PATH $PATH:/usr/local/gcloud/google-cloud-sdk/bin

ENTRYPOINT ["/usr/local/bin/docker-compose"]
