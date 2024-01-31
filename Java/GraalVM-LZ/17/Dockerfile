FROM busybox as tools

FROM rust:buster as lazymc

WORKDIR /lazymc

RUN apt-get update && \
    apt-get install -y git && \
    git clone https://github.com/Docker-Collection/lazymc.git . && \
    cargo build --release && \
    chmod +x target/release/lazymc

FROM container-registry.oracle.com/graalvm/jdk-ee:ol9-java17-22

RUN useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY --from=tools /bin/ip /bin/
COPY --from=lazymc /lazymc/target/release/lazymc /bin/lazymc
COPY entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]