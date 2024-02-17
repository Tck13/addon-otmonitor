ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION
ARG BUILD_FROM

################################################################################
## Stage 2 -> 1: Build the addon container                                         ##
################################################################################
FROM ${BUILD_FROM}
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
        nginx \
        python3-tk \
        unzip \
 && ln -sf /dev/stderr /var/log/nginx/error.log \
 && ln -sf /dev/stdout /var/log/nginx/access.log \
 && rm -fr \
     /tmp/* \
     /var/cache/* \
     /var/lib/apt/lists/* \
     /etc/nginx

COPY rootfs /

WORKDIR /opt
RUN chmod +x /opt/otmonitor

LABEL \
    io.hass.name="otmonitor" \
    io.hass.description="otmonitor add-on" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Tycho <tycho.tck13@gmail.com>" \
    org.label-schema.description="otmonitor add-on" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="otmonitor" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://addons.community" \
    org.label-schema.usage="https://github.com/tck13/addon-otmonitor/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/tck13/addon-otmonitor" \
    org.label-schema.vendor="TCK13"

