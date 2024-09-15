# Why node:8 and not node:10? Because (a) v8 is LTS, so more likely to be stable, and (b) "npm update" on node:10 breaks on Docker on Linux (but not on OSX, oddly)
FROM node:14-slim

RUN apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get -qqy upgrade \
  && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -yqq \
    nodejs \
    ca-certificates \
    git \
    libboost-all-dev \
    libssl-dev \
    make \
    sed \
    gcc \
    g++ \
    libsodium-dev\
  && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/dvandal/cryptonote-nodejs-pool.git /pool
WORKDIR /pool/
COPY example_config.json /pool/.

# turtlecoin-multi line must be removed, it's not applicable for Kryptokrona
# asyc must be of version 1.5.2 or you might run into issues with unlocking blocks.
# Redis requires to be version 3.1.2 or it won't be able to talk to redis due to old integration code!
RUN sed -i '/turtlecoin-multi.*/d' package.json \
    && sed -i 's/"async": "\^3.2.0*",/"async": "1.5.2",/' package.json \
    && sed -i 's/"redis": "\*",/"redis": "3.1.2",/' package.json \
    && npm update \
    && mkdir -p /config \
    && apt-get -y remove git make gcc g++ \
    && apt -y autoremove \
    && rm -rf /var/lib/apt/lists/*

EXPOSE 8117
EXPOSE 8119
EXPOSE 3333
EXPOSE 4444
EXPOSE 5555
EXPOSE 7777
EXPOSE 9999

VOLUME ["/config"]
CMD node init.js -config=/config/config.json
