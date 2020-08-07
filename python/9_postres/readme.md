# Postgres with Docker
Author: Bruno Staub
Inspired by: Hussein Nasser :-)

Datum: 07.08.2020

## Setup
```
docker run -p 5555:80 --name pgadmin -e PGADMIN_DEFAULT_EMAIL="bruno" -e PGADMIN_DEFAULT_PASSWORD="password" dpage/pgadmin4
```

## Login with the above credentials
http://localhost:5555/


## Setup Databases Example interactive or as service or with username
```
docker run -p 5432:5432 --name container-pg -e POSTGRES_PASSWORD=password postgres

docker run -p 5431:5432 --name container-pg2 -e POSTGRES_PASSWORD=password -d postgres

# this creates also a database with name bruno
docker run -p 5430:5432 --name container-pg3 -e POSTGRES_USER=bruno -e POSTGRES_PASSWORD=password -d postgres

# with restart policy, must be stopped, otherwise it will start automatically
docker run -p 5429:5432 --name container-pg4 -e POSTGRES_PASSWORD=password --restart=unless-stopped -d postgres
```

## Debuging Docker

docker ps -a
docker container stop xxx
docker container rm xxx
docker container list
docker container stop xxx
connect with pgdmin -> hostname must be: host.docker.internal  !!!
                    -> user: postgres  (default)


## Restart Policy
https://docs.docker.com/compose/compose-file/#restart


## Stackoverflow Help
```
Help1:

Pull the latest postgres

docker pull postgres:latest

run the postgres containner:

docker run -d -e POSTGRES_USER=user -e POSTGRES_PASSWORD=password123 --name db-my -p 5432:5432  --restart=always postgres

Then installed the latest version of pgAdmin4 from pgadmin website

Run pgAdmin 4 create new server, and input as following Host: 127.0.0.1 Port: 5432 User name: user password: password123

Then everything is ok, connect to docker postgres instance succes


Help2:

for postgres
docker run -p 5432:5432  --name container-postgresdb -e POSTGRES_PASSWORD=admin -d postgres
for pgadmin
docker run -p 5050:80  -e "PGADMIN_DEFAULT_EMAIL=name@example.com" -e "PGADMIN_DEFAULT_PASSWORD=admin"  -d dpage/pgadmin4

Connection string for pgadmin
host: host.docker.internal
database: postgres
user: postgres
password: admin
```
