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
* firewall-cmd --permanent --zone=public --add-port=27017/tcp
* systemctl restart firewalld.service

## Run
```
    git clone https://github.com/black-atom/microservices-deployment.git
    cd microservices-deployment
    git submodule update --init --recursive
    git submodule foreach git pull origin master
    docker-compose up -d 
    docker ps - to check whether it is running or not
```

## Update
```
    git submodule foreach git pull origin master
    docker-compose up --force-recreate  --build -ds
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
* GET POST DELETE PUT /api/clientes
* GET POST DELETE PUT /api/funcionarios
* POST /login
* GET POST DELETE PUT /api/atendimentos
* POST /atendimentos/:id/imagens


## Websockets
ip:3000