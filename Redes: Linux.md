# Redes - Linux

**Tags:** onGit  
**Criado:** June 7, 2023 12:47 PM  
**Atualizado:** February 17, 2024 8:52 PM

## Comandos de Rede

- `ip addr`: Visualizar o endereço IP da máquina.
- `ip loopback`: Interface de rede virtual que permite a comunicação entre um cliente e um servidor no mesmo host, similar ao localhost.
- `link/ether`: Endereço MAC da máquina.
- `mascara`: Faixa de IPs na qual o IP está trabalhando, geralmente indicada pela quinta palavra separada por uma barra.
- `eth0`: Interface de rede que representa o IP da máquina.
- `gateway`: IP do roteador.

- `ssh <opções> <nome da máquina>@<IP>`: Conectar do Windows à máquina virtual. Por padrão, o SSH utiliza a porta 22.
- `ssh username@remote_server_ip_address`: Conectar a um servidor remoto.
- `sudo apt update`
- `traceroute`: Diagnosticar comunicação entre a máquina e um IP usando diferentes protocolos.
- `curl`: Pegar informações da conexão.
- `curl ifconfig.me`: Verificar o IP público da máquina.
- `telnet <IP> <porta>`: Obter informações da conexão.
- `sudo tcpdump port 80 -v -n`: Escutar conexões na porta 80.
- `top`: Visualizar os processos em execução na máquina.

## Comandos de Linha de Comando UNIX

- **Kernel:** Programa que interage com o hardware, o núcleo do sistema operacional.
- **Shell:** Interface do usuário para interagir com o kernel e, consequentemente, com o hardware; pode ser uma interface gráfica (GUI) ou de linha de comando (CLI).

### Comandos Básicos

- `ls`: Listar arquivos.
- `ls -a`: Listar com arquivos ocultos.
- `ls *.fileExtension`: Listar arquivos com determinada extensão.
- `ls -l`: Mostrar informações detalhadas.
- `ls -al`: Mostrar como lista detalhada.
- `ls -rtl`: Ordenar por última modificação.
- `ls --help`: Ver documentação para comandos.
- `ls <iniciais dos arquivos>`: Listar arquivos começando com as letras especificadas.
- `cd`: Mudar de diretório.
- `cd ~`: Navegar até o diretório raiz.
- `cd ~/<nome da pasta>`: Navegar até uma pasta específica a partir do diretório raiz.
- `cd -`: Voltar ao diretório anterior.
- `cd..`: Voltar um diretório.
- `../`: Diretório anterior.
- `cd ../../`: Voltar quantos diretórios desejar.
- `pwd`: Mostrar o diretório atual.
- `tab`: Autocompletar.
- Setas de cima/baixo: Navegar pelos comandos anteriores.
- `alt` + mouse: Selecionar texto.
- `ctrl a`: Ir para o início da linha de comando.
- `ctrl e`: Ir para o final da linha de comando.
- `ctrl u`: Limpar toda a linha de comando.
- `ctrl l`: Limpar o terminal.
- `clear`: Limpar o console.
- `cat`: Exibir o conteúdo de um único arquivo.
- `>`: Redirecionar saída para um arquivo.
- `>>`: Operador de anexo.
- `history`: Ver histórico de comandos.

### Visualização de Arquivos

- `less <nome do arquivo>`: Navegar pelo arquivo.
- `/<string>`: Buscar uma string no arquivo.
- `head <arquivo>`: Exibir a primeira parte do arquivo.
- `tail <arquivo>`: Exibir a última parte do arquivo.

### Manipulação de Arquivos e Diretórios

- `mkdir <nome da pasta>`: Criar uma pasta.
- `mkdir -p /<nome do caminho>/<nome do caminho>`: Criar uma pasta com subpastas.
- `touch <nome do arquivo>.<extensão>`: Criar um arquivo.
- `start <nome do arquivo>`: Abrir o arquivo com o aplicativo padrão.
- `start -nomeDoAplicativo <nome do arquivo>.<extensão>`: Especificar qual aplicativo abrir.
- `rm <nome do arquivo>.<extensão>`: Remover um arquivo.
- `rm -r <diretório>`: Remover uma pasta.
- `rm -rf <diretório>`: Remover uma pasta com força total.
- `mv <dir1> <dir2>`: Mover uma pasta.
- `mv <dir1>/* <dir2>`: Mover tudo de um diretório para outro.
- `mv <arq1> <arq2>`: Renomear um arquivo.
- `cp <nome do arquivo> <novo nome do arquivo>`: Copiar um arquivo.
- `cp -r * <caminho>`: Copiar todos os arquivos do caminho atual para outro caminho.

### Globbing

- `?`: Caractere curinga.
- `[inicio - final]`: Range de caracteres.
- `*`: Qualquer coisa.
- `-i`: Ignorar o case das letras.

### Outros Comandos

- `vi <nome do arquivo>`: Abrir o arquivo para edição.
- `grep <string> <nome do arquivo>`: Fazer uma busca em um arquivo.
- `grep -l <string> *`: Procurar arquivos com o conteúdo da string especificada.
- `grep -r <string> *`: Incluir subdiretórios na busca.
- `more <comando>`: Navegar pelo conteúdo com as teclas 'b' para voltar e 'q' para sair.
- `less <comando>`: Similar ao more, mas usando as setas para cima e para baixo.
- `sudo find`: Buscar arquivos usando parâmetros como `-amin` e `-atime`.

## Comandos Explorados

- `sudo find / -name *conf`: Buscar em todo o sistema arquivos com a extensão `.conf`.

## Arquivos

- `/etc/services`: Lista com descrições de protocolos por porta.

## Conceitos

- Uma máquina tem um IP público e um IP privado. O NAT, um protocolo do roteador, faz essa tradução.
- Com o IP privado, posso estabelecer conexão com máquinas na mesma rede.
- Posso consultar esses IPs usando o `curl` e para testar a conexão, posso usar o `telnet`.
