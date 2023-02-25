FROM jenkins/jenkins:2.375.3
USER root
RUN apt-get update && apt-get install -y lsb-release
COPY cosign-linux-amd64 cosign
USER root
RUN chmod +x cosign


