FROM ubuntu:latest
USER root
RUN apt-get update && apt-get install -y 
RUN apt-get install wget -y
RUN wget "https://github.com/sigstore/cosign/releases/download/v1.6.0/cosign-linux-amd64"
RUN mv cosign-linux-amd64 /usr/local/bin/cosign
RUN chmod +x /usr/local/bin/cosign
COPY cosign.key /usr/local/bin/cosign.key
COPY cosign.pub /usr/local/bin/cosign.pub
RUN ls -last

