# Diferença entre `docker service create` e `docker run`

*docker service*: Cria um serviço para uma imagem capaz de gerenciar varios container para aquela imagem, por exemplo, um container que precisa ser escalado. Um swarm precisa de um service para rodar o container

*docker run*: Cria o layer e execução da imagem e um unico container