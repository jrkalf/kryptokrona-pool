# Kryptokrona-pool

## Origin
Original code is based on the cryptonote-nodejs-pool. 

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