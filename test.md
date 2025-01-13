# Computer Science and other concepts

Tags: toPutOnRemote
Created: March 2, 2024 11:42 AM
Updated: January 13, 2025 5:25 PM

```

**🔷 compilação estática x dinâmica:** 
pra linkar estaticamente as libs com meu código, preciso dos binários antes deles se tornarem .dll ou .so. aqui não vou me preocupar com as dependências. 
é oq o Go faz, baixa o código fonte das dependências, compila e linka tudo estaticamente. pra linkar dinamicamente posso usar um header pra dizer quais bibliotecas vou utilizar e 
reutilizar as que já estão instaladas no sistema operacional. aqui se eu precisar mudar uma lib, recompilo só essa lib, ao invés de ter que recompilar tudo, como linkar estaticamente.
linguagens como go, preferem que vc baixe o código fonte das dependências e compilar tudo de novo, do que baixar dependências pré compiladas. go, não é uma maquina virtual nem um 
interpretador, é mais próximo de c++, que compila direto pra um binário nativo, e é feito pra fazer aplicações e não driver e coisas de mais baixo nível como em C. e prefere compilação 
estática, e vc tem que gerar um código binário único, que fica enorme de tamanho mas que vc pode mover pra outro lugar e simplesmente funciona. pra usar dependências vc baixa o código fonte 
das dependências. então a menos que a sintaxe da linguagem não mude de uma forma drástica de uma versão pra outra, vc sempre consegue um binário que não quebre no final. o rust faz
algo similiar com cargo. isso é diferente de java que vc baixa o binário que são os .jars

**🔷 instrunções interpretadas:**
um interpretador consegue compilar o código e traduzir pra instruções de maquina sem necessariamente precisar compilar esse código em binário nativo. o interpretador é só um programa 
que recebe como parâmetro o arquivo de texto que escrevi, vai usar um parser, vai transformar em uma estrutura que ele entende, como uma arvore e finalmente vai interpretar e executar. 
assim que funcionam linguagens como como perl, php, python, ruby e javascript. em interpretadores como perl, python, php ou ruby, dependem do sistema operacional por baixo. 
pra fazer isso se usa binding, que é uma forma do interpretador expor a uma biblioteca de código nativo o acesso as suas estruturas interna e memoria. então ao invés de escrever uma 
biblioteca inteira de código nativo como criptografia, eles só mapeiam pra oq o sistema operacional já oferece, por isso não pode se esperar que um código interpretado rode da mesma forma 
em diferentes OS. pq as bibliotecas são diferentes. por isso é preferível rodar linguagens interpretadas em Linux ou mac. os interpretadores criados pra linux, funcionam bem só em linux

**🔷 processos vs threads:**
em unix criar processos é mais "barato", em windows tem um overhead maior. num servidor tcp, só se consegue servir um cliente tcp por vez, pra conseguir atender todos pode se fazer um 
fork do processo, reutilizando os bits do programa original, o tal do copy on write. um servidor web como apache, no começo, só utlizava fork. pra códigos complexos que utilizam file 
system e conectam a banco de dados isso começou a se tornar um problema pq era custoso terminar e começar esses programas toda hora. surgiram formas de evitar ter que recarregar tudo 
com o fastcgi, que funciona paralelo ou apache, que se comunica via tcp pra se comunicar com o apache. o fastcgi tinha função de lidar com a interpreatação do codigo fonte. em windows não 
tem o fork. ai começa o dilema de multiplos processos ou processos com multiplas threads. hj em dia se usa muito mais threads. mas a primeira ainda é usada. o problema de multiplas 
threads é que não tem isolação da memoria como em processos

🔸em um sistema que só opera com uma thread real, os problemas de dead lock e etc. meio que não existe pq o scheduler do sistema operacional vai deixar uma thread só realmente rodar, 
mas em maquinas com 2 cores ou mais, duas threads podem rodar realmente no mesmo instante com paralelismo real 

🔸Corotinas, também conhecidas como "coroutines" em inglês, são um conceito de programação que se refere a rotinas cooperativas, isto é, rotinas que podem ser suspensas e retomadas em 
pontos específicos durante a execução, permitindo uma forma de multitarefa cooperativa. Em sistemas operacionais, as corotinas podem ser usadas para permitir a execução concorrente de 
tarefas em um único thread de execução. pode se usar fibers pra programar coroutines tb. isso ajuda pra linguagens que tem dificuldade de paralelismo com threads reais e usam GIL 
ou lock global como python. as que tem acesso a threds reais, como java e c#. pra elas, existem as threads pools. 

🔸In summary, multithreading is suitable for achieving concurrency within a single process, sharing resources efficiently, and handling tasks that benefit from parallel execution within a 
shared memory space. Multiprocessing, on the other hand, is suitable for achieving parallelism across independent processes, providing fault isolation, scalability, and load balancing 
across multiple CPU cores or machines. The choice between multithreading and multiprocessing depends on factors such as the nature of the task, scalability requirements, resource constraints,
 and programming language considerations.

**🔷 java e computação em paralelo:**
java usa conceito de interpradores e compiladores. a jvm, é um proprio sistema operacinal que abstrai a maquina por baixa. pra o java so exite a jvm. o sistema da sun separa a fase 
de compilação da fase de execução, que pega o codigo fonte em java e compila numa representação intermediaria, que é o bytecode. como um interpretador, a jvm carrega o programa 
abstraindo o sistema operacional. java não é bom pra fazer fork, pq carrega muito mais coisas na inicialização e tem um gerenciador de memoria muito mais complexo. o melhor caso 
de uso do java é rodar um unico processo no host e seus programas rodam em paralelo dentro da jvm, e jvm substitui o sistema operacional pra gerenciar os programas rodando em paralelo. 
alem disso a jvm melhora em tempo de execução como o prgrama roda otimizando o codigo nativo binario. o just in time compilation. a vantagem da jvm é nao precisar ter um compilador 
pra cada arquiteura como interl ou arm. em java se tem tudo que um sistema operacioanl como windows e linux oferecem, mas escrito tudo em java e embutido na jvm. como a jvm executa 
bytecode binario, a sintaxe pode ser diferente, como scala, clojure e kotlin 

**🔷 how do computers do math?**
 we have components like full adders, full subtractors.. all made of logic gates and transistors. all of these circuits are inside the ALU. the ALU receives operands and an op code from 
 the execution of binaries. the op code tells what operation has to be done, and the ALU chooses the circuit with a multiplexer based on the op code

**🔷 concorrência e paralelismo**
multi thread sao duas tarefas começando com o mesmo material ao mesmo tempo. só multi core tem paralelismo. multi thread começa a fica complicado quando precisam utilizar mesmos espaços 
de memória. pra iniciar um processo é preciso carregar o binario do programa, alocar memoria do sistema, checar permissões de segurança. em suma, thread são ordens de grandeza menor, 
sao menos custosos pra executar, porém são mais sucetiveis a bugs
dead lock: problema de threads querendo usar recursos compartilhados mas sem coordenação e com os flags que determinam sua execução uma bloqueando a flag da outra.
The operating system can assign one or more threads from different processes to each core. 
**Without Hyper-Threading**: Each core runs one thread, so a 4-core CPU handles 4 threads (which could belong to 4 processes or multiple threads from fewer processes.
**With Hyper-Threading**: Each core can run two threads, so a 4-core CPU handles 8 threads, potentially running more processes or handling more threads from the same process.

**🔷 formas de comunicação entre processos:**
a saida de um ser a entrada de um outro
um enviar um sinal pra o outro ao terminar ou ao começar
utilizarem um mesmo arquivo, em que um lê e outro escreve
abrir um fifo em dois processos diferentes. os named pipes. um dos processos abre o named pra ler

**🔷 how do programs and the operating system share the same hardware?**
 If a program is running, and the same time the operating system, how do they interact with the cpu at the same time? Well, the answer is that they dont. When the program needs something 
 of the OS, and interrupt is triggered to for the OS operations to take place, and when it’s done, the context switches back to the program. But there is a problem with this approach, 
 once the cpu is allocated to a process, it retains control until the process voluntarily releases either by terminating or entering in a waiting state invoking the operating system, 
 and for avoiding this to happen, programs getting control over the cpu, either voluntarily or not, a hardware timer is employed that trigger an interrupt
 
 🔷 **diferença entre arquivo binário e arquivo texto**
```

DEVOPS

```jsx
no começo as aplicações web eram servidas por servidores web como apache. quem hospedava essas aplicações precisava manter em uma mesma maquina hospedagem pra diferentes 
clientes. os servidores web rodam como um unico processo, oq causava problemas de segurança, outra opção era rodar uma instancia da aplicação por usuario, oq consumia 
muito mais memoria

pra o mundo de devops, historicamnte, duas coisas evoluiram lado a lado, primeiro, a ideia de configurar maquinas com mais rapidez, e automatização com codigo, com 
coisas que eram as primeiras versões do que se tem hoje como ansible. o sysadmin nao precisava mais fisicamente instanciar maquinas no servidor. as ferramentas de 
virtualização e as maquinas passaram a utilizar protocolos como ssh que eram segruos para que vc acesse remotamente o terminal dessas maquinas. e paralelo a isso, 
a ideia de container foi avançando, aqui a ideia era isolar processos, fazer a kernel mentir pra os processos, fazendo eles pensarem que estão sozinhos. o sistema 
operacional e ate mesmo a arquitetura dos processadores, passaram a ter syscalls que facilitavam essa ideia de mentir pra os processos 

relembrando: um sistema operacional é um conjunto de binarios, a primeira coisa depois do boot loader é a kernel, é o primeiro grande binario que carrega com todos 
os privilegios no kernel space e é responsavel por carregar todo resto do sistema que são conjuntos de programas como os drivers, hypervisors e deamons. a diferença entre 
distribuições são justamente esses ultimos binarios, o sistema de diretorios, e o sistema de gerenciamento de pacotes

o tal do cgroups, consegue isolar os recursos da maquina e fazer os processos em user land enxergar so oq vc mandar ele enxergar, vai dizer o quanto de cpu e memoria o 
processo vai enxergar e assim como o conceito de chroot, ele pode mascarar o volume de disco e carregar um boot diferente do sistema hospedeiro. se vc carregar outro root 
com outros conjunto de programas em user land, na pratica vc pode ter um host e dentro do cgroups carregar os binarios que formam o ubuntu ou qualquer outra distro

o cgroups passou a vir na kernel do linux como namespaces que consegue etiquetar os processos. quando vc cria um namespace de processos, meu processo vira o PID o process 
id numero 1, e os filhos desse processo vão seguindo nessa sequencia. diferentes namespaces vão ter diferentes processos PID 1. eu posso ter namespaces de rede, assim meus 
processos podem se ligar a uma porta virtual e ainda posso ter namespaces de mount de volumes.

o chroot mascara o filesystem e cada processo enxerga o root do disco em lugares diferentes, assim dois processos nunca vão pisar um em cima do outro 

os containers parecem muito com o sistema operacional mas eles compartilham a kernel do mesmo sistema, diferente de hypervisors que gerenciam maquinas virtuais inteiras 
cada um com o ser kernel

em 2013, o docker, alem implementar o boot separado no container, passou a usar o Union FS(file system) que é como um file system que consegue montar uma imagem que é 
somente de leitura como o novo root desse container e toda vez que vc tenta escrever ele cria uma segunda camada ‘por cima’. é como o conceito de copy on write no linux, 
pra processos que fazem fork de si mesmo. inicialmente o novo processo compartilha o mesmo espaço de memoria ate que algo precise ser escrito, ou como a ideia de ter um 
repositorio e pra alterar o codigo vc faz um commit. por isso as imagens do docker são incrementais assim vc consegue empactoar esse file system inteiro em um so grande 
arquivo que são as imagens que o cliente de docker baixa 

docker é um conjunto de ferramentas pra organizar e facilitar o uso de cgroups, namespaces e union file systems
```
