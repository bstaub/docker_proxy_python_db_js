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

```

## Links

https://www.noip.com/
