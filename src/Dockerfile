# syntax=docker/dockerfile:1
FROM debian:bookworm-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates curl \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/srbminer \
    && curl -fsSL https://github.com/doktor83/SRBMiner-Multi/releases/download/3.5.5/SRBMiner-Multi-3-5-5-Linux.tar.gz \
       | tar -xz -C /opt/srbminer --strip-components=1

WORKDIR /opt/srbminer

# Replace RYourVerusAddressHere with your VRSC address (.docker = worker name)
ENTRYPOINT ["/bin/sh", "-c", "exec ./SRBMiner-MULTI --algorithm verushash --pool ap.luckpool.net:3960 --wallet RCaNK3s5WimS5kgQKvZb7H1Hg2TqeUGrqo.docker --password x --cpu-threads $(nproc) --disable-gpu"]
