# Microservices Deployment 
# Requirements
* Docker
* Docker Compose
* MongoBD

## Databse Setup
It is important to mention that your databse must be listening in the same network interface as the docker-daemon which defaults to 172.17.0.1. To do that, follow the steps bellow
* vi /etc/mongod.conf
* search for bindIp
* add 172.17.0.1 to the list of ips to bind

## Run
```
    git clone https://github.com/black-atom/microservices-deployment.git
    cd microservices-deployment
    docker-compose up -d 
    docker ps - to check whether it is running or not
```
## Security
By Default, all the endpoints are secured. To make a request you need to pass a token
* POST ip:3000/login passing the following object
```
{
	"username": "funcionario-username",
	"password": "funcionario-password"
}
```

## Endpoints
* /api/clientes
* /api/funcionarios
* /api/atendimentos

## Websockets
ip:3000