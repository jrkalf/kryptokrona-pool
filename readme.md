# Kryptokrona-pool

## Origin
Original code is based on the [cryptonote-nodejs-pool](https://github.com/dvandal/cryptonote-nodejs-pool).
The file Dockerfile.dvandal-cryptonote is only compatible with x86_64. I can't get it to run on arm64 (Raspberry Pi 3 or 4).

The newer file [Dockerfile](Dockerfile.kryptokrona-nodejs-pool) is based on the [kryptokrona-nodejs-pool](https://github.com/kryptokrona/kryptokrona-nodejs-pool) of the kryptokrona project itself.
This file is compatible with arm64/v8.

## Basics
This repo contains a docker file to rebuild the code into a working x86_64 solution.
No arm64 or Arm/v7 compatibility. Old software

Edit your example_config.json to match the required data and underlying products like kryptokrona-node, kryptokrona-service, kryptokrona-redis. And don't forget the kryptokrona-pool-website.

## Docker run
```
docker run -dit --restart always -p 8117:8117 -p 3333:3333 -p 5555:5555 -p 7777:7777 -v $(pwd)/config:/config --name kryptokrona-nodejs-pool jrkalf/kryptokrona-nodejs-pool:latest
```

## Docker viewing logs
```
docker logs -f kryptokrona-nodejs-pool
```