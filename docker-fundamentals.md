# Docker

Docker é uma solução para o uso de Containers em Aplicações.

# O que são containers?

Abstração de processos dento do kernel, possível definir recuros como memória, rede e etc

Docker é feito em Go (Linguagem de programação)

Features (Por que utilizar?)

- Unificação de ambientes (produção e desenvolvimento);

- Possibilidade de manter o ambiente limpo e executar somente serviços necessários;

- Reutilização de imagens comunicação entre recursos através de networks;

- Receita de como a aplicação deve se comportar independente do sistema operacional;

# Comandos mais utilizados no dia a dia


O docker exec serve para executar comandos e recursos dentro de um container.
`sudo docker exec -it ID_CONTAINER /bin/bash`

docker logs ID_CONTAINER

Trava o terminal com log

docker logs ID_CONTAINER -f 

docker stop ID_CONTAINER (para container)

docker rm ID_CONTAINER (remove o container)

docker kill ID_CONTAINER (mata o container forçando a parada)




