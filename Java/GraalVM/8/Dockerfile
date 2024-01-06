FROM container-registry.oracle.com/graalvm/jdk-ee:ol9-java8-21

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]