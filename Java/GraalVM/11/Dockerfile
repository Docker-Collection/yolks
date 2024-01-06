FROM container-registry.oracle.com/graalvm/jdk-ee:ol9-java11-22

RUN apt-get update -y && \
    apt-get install -y iproute2 && \
    useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]