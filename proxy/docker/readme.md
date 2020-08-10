## Build the Docker Image
```
docker build -t bstaub/node-proxytest-server .
docker login
docker push bstaub/node-proxytest-server:latest
```
## Start diffrent Docker Proxies
```
docker run -p 6001:9999 -d -e APPID=6001 bstaub/node-proxytest-server
docker run -p 6002:9999 -d -e APPID=6002 bstaub/node-proxytest-server
docker run -p 6003:9999 -d -e APPID=6003 bstaub/node-proxytest-server
docker run -p 6004:9999 -d -e APPID=6004 bstaub/node-proxytest-server
```
## Start Debug
```
docker run -p 6001:9999 -e APPID=6001 bstaub/node-proxytest-server
```
## Docker aufräumen
```
docker ps -a
docker container stop xxx
docker container kill xxx
docker container rm xxx
docker container ls -a
docker images
docker image rm xxx
```
## Proxy Test URL's
```
http://localhost:6001

http://localhost:6001/app1

http://localhost:6001/app2

http://localhost:6001/admin
```

