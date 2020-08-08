## Mongo Datenbank und Datenowner mittels Commandline anlegen
```
docker-compose up -d      #Docker mit mongo starten, man muss im Verzeichnis docker-compose.yml sein!
mongo -u root -p root     #als Admin auf der command line anmelden

```
## Datenbanken anzeigen / neue db mit use xxx mit collection db.user.xxx anlegen, dann DatenOwner anlegen
```
show dbs
use nodeshop
db   #anzeigen in welcher DB man sich gerade befindet
db.user.insert({name: "Bruno", age: 47})
show dbs   #Datenbank wird erst angezeigt wenn Sie einen Inhalt hat!
show collections   #datenbank Collections anzeigen
db.createUser({
            user: 'nodeshop',
            pwd: 'nodeshop',
            roles: [ { role: 'readWrite', db: 'nodeshop' } ]
        })
use xxx
db.getUsers()
db.dropUser('xxx')
use xxx
db.dropDatabase()
```


## Help / Trouleshooting / Building
```
docker-compose up --build -d mongodb     #image neu bauen, docker-compose.yml von image auf build anpassen!
source .env               #Falls die enviroment Variablen nicht ausgeführt wurden
./create-app-user.sh      #ausführen, falls der Benutzer nicht angelegt wurde, chmod -x create-app-user.sh
https://docs.mongodb.com/manual/reference/method/db.createUser/
https://docs.mongodb.com/manual/reference/method/db.getUsers/
https://docs.docker.com/compose/environment-variables/
https://robomongo.org/  -> connect 127.0.0.1  name: mongodb  adress: localhost  database: admin   user: root   pass: root
https://zgadzaj.com/development/docker/docker-compose/containers/mongodb  (mongo hacker shell enhancement)
docker_proxy_python_db_js/python/mongo/.docker/mongodb
docker build -t bstaub/mongo-server .
docker push bstaub/mongo-server:latest
dce mongodb bash  #Mongo-Hacker Console in Container ausführen
mongo -u root -p root
```