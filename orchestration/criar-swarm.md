# Complete o setup do cluster swarm subindo o manager e os workers

Após a instalação do swarm, para iniciar um novo swarm o comando é:

`docker swarm init`

Retorno será parecido com:

```
Swarm initialized: current node (dxn1zf6l61qsb1josjja83ngz) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c 

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

Pode ser usado a flag `--advertise-addr` seguido do IP da maquina onde está o manager, isso configura o cluster para manager para publicar o ip. Os outros nodes porém devem devem estar preparados para conectar via IP.

Retorno com a flag:

```
Swarm initialized: current node (dxn1zf6l61qsb1josjja83ngz) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c \
    192.168.99.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

Para ver o estado do swarm podemos utilizar o `docker info`:

```
Containers: 2
Running: 0
Paused: 0
Stopped: 2
  ...snip...
Swarm: active
  NodeID: dxn1zf6l61qsb1josjja83ngz
  Is Manager: true
  Managers: 1
  Nodes: 1
  ...snip...
  ```

  Para ver informações sobre o node `docker node ls`

  ```
  ID                           HOSTNAME  STATUS  AVAILABILITY  MANAGER STATUS
dxn1zf6l61qsb1josjja83ngz *  manager1  Ready   Active        Leader
```

O `*` indica que você está conectado nesse node.