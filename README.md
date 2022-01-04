# Microservices

## Architecture
![Architecture](architecture.png)


## How to run

Change to directory k8s-specifications and run the next command:

    kubectl create -f .

## Redis

    docker run -d --name=redis redis

## PostgreSQL

    docker run -d --name=db postgres:9.4

## Voting App

    docker run -d --name=vote -p 5000:80 --link redis:redis voting-app

## Result App

    docker run -d --name=result -p 5001:80 --link db:db result-app

## Worker .NET

    docker run -d --name=worker --link db:db --link redis:redis worker

## Goals

- Deploy Containers
- Enable Connectivity
- External Access

## Steps

- Deploy PODs
- Create Services (ClusterIP)
  - redis
  - db
- Create Services (NodePort)
  - voting-app
  - result-app

## Docker Images

- Voting App (kodekloud/examplevotingapp_vote:v1)
- Result App (kodekloud/examplevotingapp_result:v1)
- Redis (redis)
- DB (postgres:9.4)
- Worker (kodekloud/examplevotingapp_worker:v1)

### Notes

- Link it's deprecated
