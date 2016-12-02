## MongoDB 3.4 (NoSQL Database)
---
### Pull image latest (with Ubuntu 14:04)
```
docker pull izone/mongodb
```
#### Create a directory for import collections and Include directory created above on flag "-v"
```
mkdir $HOME/mongodb/data/db
```
### Run pulled image
```
docker run --rm -h mongodb --name MongoDB \
	-p 27017:27017 -p 28017:28017 \
	-e AUTH=no \
	-v $HOME/mongodb/data/db:/data/db mongodb
```
#### MongoDB without password
```
	-e AUTH=no
```
#### Configure user and password
```
	-e MONGODB_PASS="mypass" \
	-e MONGODB_USER="user" \
```
#### In other new terminal
```
docker exec -ti MongoDB bash
```
### Copy json files to the created directory and import into mongodb
```
mongoimport --stopOnError --db loja --collection clientes < "/data/db/clientes.json"
```


