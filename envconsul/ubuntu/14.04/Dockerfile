FROM ubuntu:14.04

MAINTAINER Vincenzo FERME <info@vincenzoferme.it>

ENV ENVCONSUL_VERSION v0.6.0
ENV ENVCONSUL_VERSION_NUMBER 0.6.0

RUN \
  apt-get update && \
  apt-get install -y wget net-tools netcat && \
  wget -q --no-check-certificate -O /tmp/consul.tar.gz https://github.com/hashicorp/envconsul/releases/download/${ENVCONSUL_VERSION}/envconsul_${ENVCONSUL_VERSION_NUMBER}_linux_amd64.zip && \
  tar -xzvf /tmp/consul.tar.gz -C /usr/bin/ --strip-components=1 && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* *.gz
  
ENV ENVCONSUL_CONFIG /etc
  
COPY ./config/envconsul-config.hcl ${ENVCONSUL_CONFIG}/envconsul-config.hcl
COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
