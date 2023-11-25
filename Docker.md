# Docker Commands

- `run <image>`: to run an image
- `run <image> sleep <tempo>`: para rodar a imagem por um tempo especifico
- `run -it <image> <> bash`: para rodar e ficar rodando
- `run -d <image>`: para rodar sem travar o terminal
- `run -d -p 8080:80 <image>`: para rodar sem travar o terminal e colocando a porta 80 do container em conexão com 8080 do host
- `stop <id>`, `pause<id>`, `unpause<id>`: pausar, parar e recomeçar
- `run -it --name <nome> --network <nome-net><img> bash`: para rodar com um nome especifico e em uma rede criada
- `pull <imagem>`: baixar uma imagem
- `rm <id> --force`: para forçado
- `start <id>`: começar
- `exec -it <id> bash`: para ir para o terminal do meu container
- `container ls -a`: para ver o que está no dock
- `ps`: para ver o que está rodando
- `port <id>`: ver as portas em relação ao host
- `inspect <id>`: inspecionar um container
- `network create --driver bridge <nome-da-bridge>`: criar uma rede
- `network ls`: listar as redes

## Docker Concepts

- Um container é uma imagem com uma camada adicional de read and write
- O `docker run` cria um novo container e o executa. O `docker exec` permite executar um comando em um container que já está em execução.
- Uma imagem é como se fosse a base de um container. Dentro do container, posso adicionar camadas a essa imagem, camadas com instalações e serviços específicos, mas usando como base aquela imagem
- Na criação de uma imagem, posso usar como base outras imagens 
- Imagens são imutáveis, ou seja, depois de baixadas, múltiplos containers conseguirão reutilizar a mesma imagem
- Imagens são compostas por uma ou mais camadas. Dessa forma, diferentes imagens são capazes de reutilizar uma ou mais camadas em comum entre si
- Podemos querer que os dados da nossa aplicação sejam persistentes, porque assim garantimos que ela esteja distribuída e disponível se precisarmos consultá-la. Porém, se escrevermos os dados nos containers, por padrão eles não ficarão armazenados nesta camada, criada para ser descartável. Para contornar esse problema temos algumas opções: Volumes (escrever os dados em uma camada persistente); Bind mounts (escrever os dados em uma camada persistente baseado na estrutura de pastas do host)
- A rede `host` remove o isolamento entre o container e o sistema, enquanto a rede `none` remove a interface de rede.
- O docker dispõe por padrão de três redes: `bridge`, `host` e `none`
- A rede `bridge` é usada para comunicar containers em um mesmo host 
- Redes `bridges` criadas manualmente permitem comunicação via hostname 
- A rede `host` remove o isolamento de rede entre o container e o host
- A rede `none` remove a interface de rede do container
