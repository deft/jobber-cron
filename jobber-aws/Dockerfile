FROM blacklabelops/jobber
MAINTAINER Steffen Bleul <sbl@blacklabelops.com>

USER root

# install Amazon WS Cli
ENV AWS_ACCESS_KEY_ID=
ENV AWS_SECRET_ACCESS_KEY=
ENV AWS_DEFAULT_REGION=
ENV AWS_CLUSTER=
RUN apk add --update \
      gpgme \
      curl \
      py-pip && \
    pip install --upgrade pip && \
    pip install awscli && \
    curl -o /usr/local/bin/ecs-cli https://s3.amazonaws.com/amazon-ecs-cli/ecs-cli-linux-amd64-latest && \
    chmod +x /usr/local/bin/ecs-cli && \
    # Cleanup
    apk del \
      curl \
      py-pip && \
    rm -rf /var/cache/apk/* && rm -rf /tmp/* && rm -rf /var/log/*

COPY imagescripts /opt/cloud
ENTRYPOINT ["/opt/cloud/docker-entrypoint.sh"]
CMD ["jobberd"]
