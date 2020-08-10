# Install nginx

## Test with for node backend server
```
docker run -p 6001:9999 -d -e APPID=6001 bstaub/node-proxytest-server
docker run -p 6002:9999 -d -e APPID=6002 bstaub/node-proxytest-server
docker run -p 6003:9999 -d -e APPID=6003 bstaub/node-proxytest-server
docker run -p 6004:9999 -d -e APPID=6004 bstaub/node-proxytest-server
```

## Nginx Config
```
brew install nginx
cd /usr/local/etc/nginx
cp -a nginx.conf nginx.conf.bak
delete and add new config from ./nginx_step1.conf to /usr/local/etc/nginx/nginx.conf
sudo nginx
Open Browser: http://loalhost:8080
delete and add new config from ./nginx_step2.conf to /usr/local/etc/nginx/nginx.conf
sudo nginx -s stop
sudo nginx
mkdir -p site1/index.html  (hello site1)
mkdir -p site1/index.html  (hello site2)
nginx -v
sudo nginx -t
sudo nginx -s reload
https://webapp.ddns.net/
```