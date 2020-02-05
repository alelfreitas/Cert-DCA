# Proteger swarm

Para proteger os serviços, o docker encripta diversas informações e configurações usando o TLS e as chaves se propagam entre as aplicações no swarm, isso é feito pela opção `autolock`.

Quando ativada, deve ser destravada qunado o docker reiniciar, porém não precisa quando novos serviços entrarem no cluster.

Para habilitar:

`docker swarm init --autolock`

retorno:

```
Swarm initialized: current node (k1q27tfyx9rncpixhk69sa61v) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-0j52ln6hxjpxk2wgk917abcnxywj3xed0y8vi1e5m9t3uttrtu-7bnxvvlz2mrcpfonjuztmtts9 \
    172.31.46.109:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

To unlock a swarm manager after it restarts, run the `docker swarm unlock`
command and provide the following key:

    SWMKEY-1-WuYH/IX284+lRcXuoVf38viIDK3HJEKY13MIHX+tTt8
```

Guarde a chave em um local seguro ela é necessária caso você precise destravar o swarm.

Para habilitar ou desabilitar o autolock em um swarm existente:

`docker swarm update --autolock=true`
`docker swarm update --autolock=false`

Para destravar um swarm:

`docker swarm unlock`

Será solicitada a chave gerada quando o swarm com `--autolock`.

Para pegar a chave novamente digite: `docker swarm unlock-key`

Para aumentar a segurança é recomendável que você troque a chave de tempos em tempos, para isso digite:
`docker swarm unlock-key --rotate`

Um aviso: Quando trocar a chave, sempre guarde a antgiga por alguns minutos, pois caso algum nó caia durante a troca, você pode precisar da chave antiga para desbloquear.