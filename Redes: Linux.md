# Redes - Linux

Created: June 7, 2023 12:47 PM
Updated: August 30, 2024 11:13 AM

```
ip addr                                 - pra visualizar o ip da maquina
ip loopback                             - interface de rede virtual que permite 
                                          que um cliente e um servidor se comuni     
                                          quem no mesmo host; tipo o localhost
link/ether                              - meu mac address
mascara                                 - qual o range de ips que meu ip ta trab
                                          alhando, geralmente é a quinta palavra 
                                          que separada com um barra;
eth0                                    - o ip propriamente dito
gateway                                 - o ip do roteador

ssh<potions> <nome da maquina>@<ip>     - pra conectar do windows na maquina vir
                                          tual; Por default, o comando SSH utili
                                          za a porta 22
ssh username@remote_server_ip_address   - para um servido remoto
sudo apt update
traceroute                              - com os diferentes parametros posso dia
                                          gnosticar comunicação entre a meu pc                                            
                                          e um IP usando diferentes protocolos
curl ifconfig.me                        - verificar ip publico da maquina
telnet <ip> <porta>                     - pegar informações da conexão
sudo tcpdump port 80 -v -n              - pra escutar conexões nessa porta
top                                     - pra visualizar oq a maquina ta executando
ps                                      - visualizar os processos
```

```
ssh        //protocolo de rede utilizado por padrão para acesso e controle remot o de computadores e servidores com sistemas Linux
DNS        //existem diferentes servidores de dns. posso configurar na minha maquina qual servidor usar, fazer consultas de ip usando diferentes servidores e etc

```

The unix command line

```
echo                                         - basically means print

curl
-l: When a server responds to a request with a redirect status code (like 3xx), 
it's instructing the client (in this case, curl) to make another request to a 
different URL. This redirection might be for various reasons, such as when a URL 
has been moved permanently or temporarily.

The -L option in curl instructs it to follow these redirects. 
This means that if the server responds with a redirect, curl will 
automatically make another request to the new URL specified in the 
redirect response and retrieve the content from there instead.

-f: Fail silently on server errors.
-s: Silent mode. Don't show progress or error messages.
-S: Show error messages if there are any.
```

```
COMMANDS
ls                                           - list
ls -a                                        - list with hidden files. 
ls *.fileExtension                           - list all files with that ending with that 
                                               string after the wildcard
ls -l                                        - shows more info like when it was last modified
ls -al                                       - shows as a list
ls -rtl                                      - shows last modified by order
ls --help                                    - to see documentation for commands
ls <files firt letters>                      - to see all the files beginning with those letters
.                                            - diretorio corrente
cd                                           - change directory
cd ~                                         - cd to root
cd ~/<folder name>                           - cd to root then to a parent folder
cd -                                         - volta ao diretorio que estava antes
cd..                                         - go back a folder
../                                          - diretorio anterior
cd../../                                     - go back as many folders as I want
pwd                                          - print working directory
tab                                          - auto fill
up/down keys                                 - navigate through the commands
hold alt                                     - mouse cursor to select
cntrl a                                      - go to the start of the command line
cntrl e                                      - go to the end of the command line
cntrl u                                      - clear the entire command line
cntrl l                                      - clear the terminal
clear                                        - clear the console
cat                                          - to dump the contents of a single file
>                                            - redirects an output content to a file
>>                                           - append operator
history                                      - pra ver o histórico de comandos

less fileName                                - navigate through the file
/<string>                                    - search file for string. after using the l
                                               ess command
head <file>                                  - Display first part of file
tail <file>                                  - Display last part of file

mkdir folderName                             - make folder
mkdir -p /<path name>/<path name>            - make folder with folder in it. can have   
                                               as many subdir as I want
touch fileName.extension                     - make file
start fileName                               - open file with default application
start -applicatioName fileName.extension     - specify what applic. I want to open with
rm fileName.extension                        - remove file
rm -r folderDirectory/                       - remove folder
rm -rf folderDirectory/                      - remove folder hadouken version
mv dir1 dir2                                 - move folder
mv dir1/* dir2                               - move tudo a partir de dir1 para dir2
mv arq1 arq2                                 - rename file
cp fileName newFileName                      - copy file
cp -r * <path>                               - copy all the files from the path where im            
                                               at to the following specified path

GLOBBING:
?                                            - caractere coringa
[range inicio - range final]                 - posso colocar na posição do caractere em que quero o range
*                                            - basicamente vai significar um qualquer coisa
-i                                           - ignorar o case da letra

cat                                          - visualizar o arquivo. se não exis
                                               tir o arquivo ele vai criar
vi <file name>                               - abrir o arquivo especificado pra editar
grep <string> <file name>                    - fazer uma busca
grep -l <string> *                           - procura o arquivo com o conteudo da strin 
                                               g que eu passei
grep -r <string> *                           - inclui os subdiretorios na busca
more <comando q eu quiser>                   - uma forma de navegar o conteudo. 'b' volt
                                               a a pagina. 'q' sai da pagina
less <comando q eu quiser>                   - mesma coisa que o more so que usando as s
                                               etas cima e baixo
sudo find                                    - pra o find eu posso usar parametr  
                                                os como-amin e -atime pra buscar 
                                                arquivos criados em um tempo esp     
                                                ecifico outros parametros: -size
locate                                       - to find stuff as well                                               

```

FILE PERMISSIONS

| ls -l <file name> | - to see what permissions the 
three types of roles have for that file. the permissions can only be read, write and execute. the role are user, group and other |
| --- | --- |
| chmod u=<permissions>,g=<permissions>, o=<permissions> <file name> | to alter the permissions; example: chmod u=rwx <file name> |
| sudo chown root <file name> | sudo makes command run as root user. If I apply this command to to a file, the given file will have be owned by root, and only root will be able to access. (with sudo, of course) |

INSTALL APS

```bash
apt 
apt get ?
apt update  
apt upgrade
apt install
apt remove 
apt search
wich <lib>
```

CONCEITOS

```
uma maquina tem um ip publico e um ip privado. o NAT que é protocolo do roteador faz essa tradução. com o ip privado posso estabelecer conexão com maquinas do mesmo network. posso consultar esses ips usando o curl. e pra consultar conexão posso usar o telnet

```

| `PATH=$PATH:<caminho do executável >` | pra adicionar paths pra variável path eu faço  |  |
| --- | --- | --- |
| `grep <text> <file>` | search for text within file | `*` (on the place of the file will apply the command on all the files in the directory) `-r` ( will search recursevly on the entire specified directory) `-i` (case insentive) |
| `cat <file>` | display the contents of a file  |  |
| `cat <file> | grep <text>` | search for text within file |  |
| `htop and ps x` | see what process are running | ps `-He` to show the process in hierarchy `aux` shows the processes and by wich user it was triggered |
| `stdin, stdout, stderr` | standar input, output and erros. input are commands, for example, output is the return of the command, and errors the same idea | `echo $?`  to see if there were any return errors from the last command. if it returns 0 there was no error. when using output redirection `>` I can specify 2 for error and 1 for stdout `<number> >` |
| >  | output rediretion operator | when using `>>` I append the output to the end of the file instead of rewriting the file |

ENVIRONMENT VARIABLES

In Linux, environment variables are dynamic named values that affect the way processes behave and how they interact with the operating system. These variables are part of the environment in which a process runs and are inherited from parent processes to child processes. They can store information such as system configuration settings, user preferences, or data necessary for proper operation of programs.

Here are a few key points about environment variables in Linux:

1. **Definition and Usage**: Environment variables are typically defined as pairs of variable names and their corresponding values. They are set using the syntax **`NAME=value`**, where **`NAME`** is the name of the variable and **`value`** is its value. These variables are accessible by all processes running under that environment.
2. **Common Environment Variables**: Linux systems often come with several predefined environment variables, such as **`PATH`**, **`HOME`**, **`USER`**, **`LANG`**, **`TERM`**, etc. Each of these variables serves a specific purpose, like defining the user's home directory, setting the language and character encoding, determining the search path for executable files, etc.
3. **Setting Environment Variables**: Environment variables can be set temporarily within a shell session using the **`export`** command. For example:
    
    ```bash
    export VARIABLE=value
    ```
    
    This makes **`VARIABLE`** and its value available to all subsequent processes spawned from that shell session.
    
4. **Persistent Environment Variables**: To make environment variables persistent across sessions, they can be defined in configuration files like **`~/.bashrc`**, **`~/.bash_profile`**, **`~/.profile`**, or system-wide configuration files like **`/etc/profile`**, **`/etc/environment`**, etc., depending on the shell and distribution.
5. **Relating to Commands**: Environment variables often relate to commands by influencing their behavior. For instance:
    - **`PATH`**: This variable determines the directories in which the shell looks for executable files when a command is entered. If the command's executable is not found in any of the directories listed in **`PATH`**, you would need to provide the full path to the executable.
    

```
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Cortex Debug",
      "cwd": "${workspaceFolder}",
      "executable": "${workspaceRoot}/build/test.elf",
      "request": "launch",
      "type": "cortex-debug",
      "runToEntryPoint": "main",
      "servertype": "openocd",
      "device": "STM32L476RGTx",
      "configFiles": ["interface/stlink.cfg", "target/stm32l4x.cfg"]
    }
  ]
}

```

How to automate stuff

```jsx
(1) 
- on zshrc or bashrc
- alias <command>='<command I want to automate>'

(2) 
- sudo nano /usr/local/bin/<name_of_the_script>
- create the script. for automating input use expect bin 
- sudo chmod +x /usr/local/bin/<name_of_the_script>
```
