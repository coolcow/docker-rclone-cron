FROM ghcr.io/coolcow/rclone:latest

LABEL maintainer="Jean-Michel Ruiz (coolcow) <mail@coolcow.org>"

ENV LABEL_MAINTAINER="Jean-Michel Ruiz (coolcow) <mail@coolcow.org>" \
    LABEL_VENDOR="coolcow.org" \
    LABEL_IMAGE_NAME="ghcr.io/coolcow/rclone-cron" \
    LABEL_URL="https://ghcr.io/coolcow/rclone-cron" \
    LABEL_VCS_URL="https://github.com/coolcow/docker-rclone-cron" \
    LABEL_DESCRIPTION="Docker ghcr.io/coolcow/rclone image using crond as default entrypoint." \
    LABEL_LICENSE="GPL-3.0" \
    ENTRYPOINT_GROUP=rclone \
    ENTRYPOINT_HOME=/home \
    CROND_CRONTAB=/crontab

RUN touch $CROND_CRONTAB

ENTRYPOINT ["/entrypoint_crond.sh"]

CMD ["-f"]

#

ARG LABEL_VERSION="latest"
ARG LABEL_BUILD_DATE
ARG LABEL_VCS_REF

# Build-time metadata as defined at http://label-schema.org
LABEL maintainer=$LABEL_MAINTAINER \
      org.opencontainers.image.title=$LABEL_IMAGE_NAME \
      org.opencontainers.image.description=$LABEL_DESCRIPTION \
      org.opencontainers.image.version=$LABEL_VERSION \
      org.opencontainers.image.created=$LABEL_BUILD_DATE \
      org.opencontainers.image.revision=$LABEL_VCS_REF \
      org.opencontainers.image.authors=$LABEL_MAINTAINER \
      org.opencontainers.image.licenses=$LABEL_LICENSE \
      org.opencontainers.image.source=$LABEL_VCS_URL \
      org.opencontainers.image.url=$LABEL_URL
