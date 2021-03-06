# spring-cassandra-example
Spring Data for Apache Cassandra example
## Install
### Install Cassandra
*Local OR Docker install (select only one)
#### Local
```
echo "deb http://www.apache.org/dist/cassandra/debian 311x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list
curl https://www.apache.org/dist/cassandra/KEYS | sudo apt-key add -
sudo apt-get update
sudo apt-get install cassandra
```
for more details [cassandra.apache.org](http://cassandra.apache.org) <br>
#### Docker (recommended)
#### Cassandra for docker
```
sudo docker run --name dev-cassandra -p 7000:7000 -p 7001:7001 -p 9160:9160 -p 9042:9042 -d cassandra:3.11.2
```
##### Cassandra cqlsh
```
docker exec -it __CONTAINER_ID__ cqlsh
```
## Examples
### Save person
```
curl -X POST \
  http://localhost:8080/persons \
  -H 'Content-Type: application/json' \
  -d '{
	"uuid": "8781d82d-08bc-4148-b00f-4ad7750b4934",
	"email": "cemserit@gmail.com",
	"name": "Cem Serit",
	"age": 27
}'
```
### Update person
```
curl -X PUT \
  http://localhost:8080/persons/8781d82d-08bc-4148-b00f-4ad7750b4934 \
  -H 'Content-Type: application/json' \
  -d '{
	"uuid": "8781d82d-08bc-4148-b00f-4ad7750b4934",
	"email": "cemserit@gmail.com",
	"name": "Cem",
	"age": 27
}'
```
### Get all persons
```
curl -X GET \
  http://localhost:8080/persons 
```
### Get person (find by uuid)
```
curl -X GET \
  http://localhost:8080/persons/8781d82d-08bc-4148-b00f-4ad7750b4934 
```
### Get person (find by age)
```
curl -X GET \
  http://localhost:8080/persons?age=27
```
### Get person (find by email and age)
```
curl -X GET \
  http://localhost:8080/persons?email=cemserit@gmail.com&age=27
```
### Delete person
```
curl -X DELETE \
  http://localhost:8080/persons/8781d82d-08bc-4148-b00f-4ad7750b4934
```