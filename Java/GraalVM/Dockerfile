ARG BUILD_SOURCE
ARG BUILD_VERSION

FROM busybox as tools

FROM ${BUILD_SOURCE}:${BUILD_VERSION}

RUN useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY --from=tools /bin/ip /bin/
COPY entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]