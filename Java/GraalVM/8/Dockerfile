FROM busybox as tools
FROM container-registry.oracle.com/graalvm/jdk-ee:ol9-java8-21

RUN useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY --from=tools /bin/ip /bin/
COPY entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]