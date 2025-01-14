# Docker

Tags: toPutOnRemote
Created: July 8, 2023 4:14 PM
Updated: January 14, 2025 5:15 PM

```
🔷 docker runtime 
basically allows us to stop and run containers. 
there is a low level runtime wich is known as runc. the role of this runtime 
is to work with the operating system to stop and run containers. 
the second one is containerd. this one is on a higher level
implementation and basically manages runc and stuff like how to make 
containers interact with networks

🔷 client - server achitecture
the client is the CLI and the server/daemon works with 
the runtime to do stuff. the CLI talks to the server via API rest 

🔷 dockerfile
a text document that contains a set of instructions or commands 
used to assemble a - -  -Docker image.Dockerfile typically includes
instructions for installing dependencies, configuring the environment,
setting up directories, copying files, and running commands 
necessary to create a functioning environment for your application.

🔷 docker image
🔸A Docker image is a lightweight, standalone, executable 
package that includes everything needed to run a piece of software,
including the code, runtime, libraries, environment variables, 
and configuration files. Docker images are built from Dockerfiles. 
🔸When you run the **docker build** command, Docker reads the instructions
from the Dockerfile and creates a Docker image based on those 
instructions. containers are running instances of an image
🔸Uma imagem é como se fosse a base de um container. dentro do container eu 
posso adicionar camadas a essa imagem, camadas com instalações e serviços especificos, 
mas usando como base aquela imagem
🔸Na criação de uma imagem, eu posso usar como base outras imagens
🔸Um container é uma imagem com uma camada adicional de read and write
🔸O docker run cria um novo container e o executa. O docker exec 
permite executar um comando em um container que já está em execução.

🔷redes
O docker dispõe por padrão de três redes: bridge, host e none
A rede bridge é usada para comunicar containers em um mesmo host
Redes bridges criadas manualmente permitem comunicação via hostname
A rede host remove o isolamento de rede entre o container e o host
A rede none remove a interface de rede do container

🔸iptable: comandos pra utilizar o netfilter
🔸namespaces: modulo do kernel linux utilizado pelo docker. faz isolamento em alto nivel
🔸cgroups: modulo do kernel linux utilizado pelo docker. 
faz isolamento isolamento em baixo nivel
```

DOCKER bin

```bash
run <image>                        - to run an image to create a container
run <image> sleep <tempo>          - pra rodar a imagem por um tempo especifico
```

CONTAINER bin

```
container inspect <id>              - inspecionar um container

container ls                     
-a: to see what's there but no running

container run <img>
-d: pra rodar sem travar o terminal. vai rodar como daemon
-ti: pra rodar em primeiro plano
-p: set the ports
-n: set a name
-e: add environment variables

container attach <ID>              - to get into a container
container exec -ti <ID>            - executo comandos no container. lembrar que 
<commands> bash                      o container precisa ter o shell

container stop <id> , pause<id>,   - pausar, parar e recomeçar
unpause<id> restart<id> start<id>
container rm <id> --force          - parar forçado
container prune                    - remove todos os que estão parados
docker rm -f $(docker ps -aq)      - remove todos

container stats <id>               - pra ver a utilização dos recursos da maq.
container top <id>                 - pra ver os processos

```

IMAGES bin

```bash
image ls                            - to see all the images downloaded
pull <imagem>                       - baixar uma imagem
build <docker file>                 - buildar a image
image tag                           -<nome do usuario no dockerhub>/<nome da imagem>
-t: por um nome
```

NETWORK bin

```bash
network create --driver bridge <nome da bridge>          - criar uma rede
network ls                                               - listar as redes
container port <id>                     - ver as portas em relação com o host
```

VOLUME bin

```
*BIND: quando ja tenho um diretorio e quero montar 
esse diretorio especifico dentro do container*
--mount type=bind,src=<path>,dst=<path> <img>

*VOLUME: se eu não especificar na hora de rodar, 
por default vai ser do tipo volume
by default docker monta o volume em: /var/lib/docker/volumes/
-- mount type=volume,src=<vol>,dst=<path> <img>*

volume create
**volume ls                             
volume inspect <vol>
volume rm <vol>
volume prune                      - remove all volumes not used by any container
                                    be careful because it removes the data from the volume
```

DOCKERFILES

```makefile
FROM: em qual imagem vou me basear
RUN: comando que vai rodar quanto tiver fazendo build da imagem
ENV: criar variaveis de ambiente
LABEL: adicionar labels
VOLUME: docker vai criar um volume 
EXPOSE: porta que vai ser exposta
ENTRYPOINT: vai definir um processo principal pra ser executado na inicialização
CMD: passa parametros(comandos) para o shell padrão da sistema operacional que tiver rodando. 
se eu utilizar ENTRYPOINT  o principal processo vai ser o binario que for executando por esse 
comando do entrypoint, nesse caso, no CMD, não posso o shell da mesma forma pq ele não é mais o principal processo
COPY/ADD: copia um arquivo do host pra o container
WORKDIR: 
In this Dockerfile, WORKDIR is a directive used to set the working 
directory for any subsequent instructions in the Dockerfile. 
It defines the directory within the container where commands such 
as RUN, COPY, CMD, and ENTRYPOINT will be executed.
ARG: um parametro que posso passar pra o container, com --build-arg quando for fazer o build 
HEALTHCHECK: um comando que vai fazer um teste a cada determinado periodo de tempo 
```

DOCKERHUB

```
o registry é como se fosse o repositorio. eu posso criar o registery
dentro de um cointainer e salvar esse registry, por exemplo, localmente
na verdade, esse <username>, que vem na frente, é o local que ta o registry
pra salvar localmente eu preciso criar um registry local 

docker push <username>/<image name>:<tag>
docker container run -d -p 5000:5000 --name registry <nome que vou dar pra o registry local>

```

SHORTKEYS

```
 
ctrl + d                       - sair do container
ctrl + p + q                   - sair do container sem terminar o processo
```

SOME NICE COMMANDS

```bash
*Install on Ubuntu*
curl -fsSL https://get.docker.com | bash

*run stress test on nginx*
apt-get update
apt-get install stress
stress --vm 1 --cpu 1 --vm-bytes 80M

*to get info about the machine*
cat /proc/cpuinfo

setting up and ec2 instance
sudo su -
hostname andre-01
sudo hostname andre-01
bash

```

## DOCKER BUILD CONTEXT

1. **Specify Build Context**: When you run the **`docker build`** command, you specify a directory as the build context. For example:
    
    ```arduino
    arduinoCopy code
    docker build -t my-image .
    
    ```
    
    In this command, **`.`** indicates that the current directory is the build context. You can also specify a different directory by replacing **`.`** with the path to the desired directory.
    
2. **Create a Tarball**: Docker creates a tarball (a compressed archive) of the specified build context directory. This tarball includes all files and subdirectories within the build context, except for those excluded by patterns defined in the **`.dockerignore`** file.
3. **Transfer to Docker Daemon**: Docker transfers the tarball to the Docker daemon, which is responsible for managing Docker objects such as images and containers. This transfer can occur locally if you're building images on your local machine or remotely if you're using Docker in a client-server setup.
4. **Extract Build Context**: The Docker daemon extracts the contents of the tarball and uses them as the build context for building the Docker image. This includes the **`Dockerfile`** located in the build context directory, along with any other files referenced by **`COPY`** or **`ADD`** instructions within the **`Dockerfile`**.
5. **Build Image**: Docker reads the instructions in the **`Dockerfile`** and executes them one by one to build the Docker image. This may involve running commands such as **`COPY`**, **`RUN`**, **`ADD`**, and **`CMD`** to configure the image according to your specifications.
6. **Resulting Image**: Once the build process is complete, Docker produces an image based on the specified instructions in the **`Dockerfile`** and the contents of the build context. This image contains all the necessary dependencies, configurations, and files required to run your application.

Why do we exclude npm packages but not the source code, since I’m already copying that too into the container

**Copying in Dockerfile vs. Build Context**: While it might seem redundant to copy the source code both in the Dockerfile (**`COPY . .`**) and include it in the build context, there's a key difference. The **`COPY`** instruction in the Dockerfile copies files from the host machine into the Docker image, specifically into the image filesystem. On the other hand, including the source code in the build context allows Docker to access these files during the build process (e.g., for the **`RUN`** instructions in the Dockerfile), but they are not directly added to the image filesystem.

```docker
# syntax=docker/dockerfile:1

FROM node:lts-alpine AS base

WORKDIR /app
COPY ["package.json", "package-lock.json*", "./"]  
//from host machine TO the container

FROM base AS dev
ENV NODE_ENV=dev
RUN npm install --frozen-lockfile
COPY . .
//from the build context TO ther current working directory
//Paths specified in the COPY and ADD instructions in the Dockerfile are 
relative to the build context.
//By default, the build context is the directory containing the Dockerfile
//Additionally, you can exclude files and directories from the build context using a .dockerignore file
CMD ["npm", "run", "start:dev"]

FROM base AS prod
RUN npm install --frozen-lockfile --production
COPY . .
RUN npm install -g @nestjs/cli
RUN npm run build
CMD ["npm", "run", "start:prod"]

```
