## Test HA-PRoxy mode tcp or http
```
haproxy -f test.cfg
telnet 127.0.0.1 80
GET /
Enter
and do the Test again Layer 7 or Layer 4 LB
```

## Test HA-PRoxy acl and diffrent backends
```
haproxy -f test2.cfg
http://127.0.0.1
http://127.0.0.1/app1  (balance source)
http://127.0.0.1/app2
http://127.0.0.1/admin  (deny)
```

## Test HA-PRoxy https with noip / lets encrypt ssl
```
 sudo certbot certonly --standalone
 ..
 port 80 darf nicht besetzt sein!
 beim fqdn den zertifikatsnamen angeben!
 wenn alles Erfolgreich für haproxy public und private key in ein file schreiben!
 ..
 
sudo cat /etc/letsencrypt/live/webapp.ddns.net/fullchain.pem /etc/letsencrypt/live/webapp.ddns.net/privkey.pem | sudo tee ~/VisualStudioCode/docker_proxy_python_db_js/proxy/ha-proxy/webapp.ddns.net.pem
```

## Test with for node backend server (test1.cfg, test2.cft, test3.cfg)
```
docker run -p 6001:9999 -d -e APPID=6001 bstaub/node-proxytest-server
docker run -p 6002:9999 -d -e APPID=6002 bstaub/node-proxytest-server
docker run -p 6003:9999 -d -e APPID=6003 bstaub/node-proxytest-server
docker run -p 6004:9999 -d -e APPID=6004 bstaub/node-proxytest-server
```


## Example SSL Config with http to https redirect
```
flaskblog_noip_ssl.cfg
haproxy -f flaskblog_noip_ssl.cfg
haproxy -f flaskblog_noip_ssl_h2.cfg   (https2 mode)
```

## Links

https://www.noip.com/
