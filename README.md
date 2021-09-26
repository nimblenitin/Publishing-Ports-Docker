# Publishing-Ports-Docker

Steps to publish a swarm service’s port to external hosts in different ways-

a. Publish a swarm service’s port using the Routing Mesh

```

1. If Docker Swarm is not initialized on the master node, initialize docker swarm-
$ sudo docker swarm init

2. Use --publish <PUBLISHED-PORT>:<SERVICE-PORT> to publish a port externally to the swarm:
$ sudo docker service create --name service1 \
> --replicas 3 --publish published=8080,target=80 nginx

3. Use the following command to check whether your service has started on port 8080:
$ curl localhost:8080

```

b. Publish a swarm service’s port directly on the swarm node

```

1. Use the mode=host option with --publish flag along with --mode global flag to publish a port directly on the swarm node-
$ sudo docker service create --mode global \
> --publish mode=host,target=80,published=8081 \
> --name=service2 nginx:latest

2. Use the following command to check whether your service has started on port 8081:
$ curl localhost:8081

```
