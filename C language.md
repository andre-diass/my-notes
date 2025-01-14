# C

Created: June 10, 2024 8:08 PM
Updated: December 4, 2024 4:55 PM

Tipos de variavés em C

| `char` | 1 byte |
| --- | --- |
| `short` |  2 bytes |
| `int` | 4 bytes |
| `long` | 4 bytes |
| `long long` | 8 bytes |
| `float` | 4 bytes |
| `double` | 8 bytes |

Sequencias de escape                                                                                            Modificadores

| Nulo (`null`) | \0 |
| --- | --- |
| Campainha (`bell`) | \a |
| Retrocesso (`backspace`) | \b |
| Tabulação horizontal | \t |
| Nova linha (`new line`) | \n |
| Tabulação vertical | \v |
| Alimentação de folha (f`orm feed)` | \f |
| Retorno de carro (`carriage return`) | \r |
| Aspas (") | \" |
| Apóstrofo (') | \' |
| Interrogação (?) | \? |
| Barra invertida (\) | \\ |

| `signed` | que char ou int podem ter valores negativos |
| --- | --- |
| `unsigned` | que char ou int so poderão ter valores positivos |
| `short`  | determina que uma variavel do tipo int terá apenas 16 bits |
| `long` | determina que uma variavel do tipo int terá 32 bits |
|  |  |
|  |  |

Libs

*stdio.sh*

`printf()` `printf(“%d %f\n”,x,y)`

---



| `%ld` | long integer |
| --- | --- |
| `%x` | hexdecimal |
|  |  |

`scanf() scanf(“%d%d”,&x,&z)`

---

FUNÇÕES

```
🔸ela deve ser definida ou declarada antes de ser utilizada, ou seja, 
antes da cláusula main().Pode-se também declarar uma função depois da cláusula main(). 
Nesse caso, é preciso declarar antes o protótipo da função.

🔸O protótipo de uma função não precisa incluir os nomes das variáveis passadas como
parâmetros. Apenas os seus tipos já são suficientes.

🔸Dependendo da função, ela pode não possuir nenhum parâmetro. Nesse caso, pode-
se optar por duas soluções:
• Deixar a lista de parâmetros vazia: void imprime().
• Colocar void entre parênteses: void imprime(void).
Na primeira declaração, não é especificado nenhum parâmetro, portanto a função pode
ser chamada passando-se valores para ela. O compilador não vai verificar se a função
é realmente chamada sem argumentos, e a função não conseguirá ter acesso a esses
parâmetros. Já na segunda declaração, nenhum parâmetro é esperado. Nesse caso, o
programa acusará um erro se o programador tentar passar um valor para essa função

🔸O valor retornado por uma função não pode ser um array. A linguagem C não suporta 
a atribuição de um array para outro. Poresse motivo, não se pode ter um 
array como retorno de uma função. É possível retornar um array indiretamente, 
desde que ele faça parte de uma estrutura.

🔸Na linguagem C, os argumentos para uma função são sempre passados por valor
(by value), ou seja, uma cópia do dado é feita e passada para a função. Esse tipo de
passagem de parâmetro é o padrão para todos os tipos básicos predefinidos (int, char,
float e double) e estruturas definidas pelo programador (struct).

🔸Para passar para a função um parâmetro por referência, a função precisa usar ponteiros.

```

ARRAYS

```
🔸O nome de um array indica onde esses dados começam na memória

🔸O valor inicial de um array é o lixo de memória contido no espaço 
reservado para ele

🔸Não se pode fazer atribuição de um array pra outro

🔸Strings são arrays. Portanto, não se pode fazer atribuição de strings.

🔸Difference between string literal/string constant and string variable
int main void{
char msg1[] = "Hello World"
char *pmsg2[] = "Hello World"}

the first one is a string variable and the second one is a string literal, but 
why is that?

the strings Hello world ara part of the initial binary code, so they start in 
flash memory, and since the variables are local (to main) they will copied to 
RAM. In the first case, msg1 value will be copied to the heap, in the second case, the
pointer will point to flash, and data in flash cannot be changed, that's why it's 
a string literal and should actually be initilized as char const *pmsg2[] = "Hello 
World"}
```

PONTEIROS

```
🔸Variável: é um espaço reservado de memória usado para guardar um valor que
pode ser modificado pelo programa.
	 Ponteiro: é um espaço reservado de memória usado para guardar um endereço
de memória.

🔸Para saber o endereço onde uma variável está guardada na memória se usa o &
tip: O endereço de memoria quando é argumento (na chamada da função) 
uso o & e quando é parametro uso * 

🔸para acessar o conteúdo da posição de memória
para a qual o ponteiro aponta, usa-se o operador asterisco (*)

🔸***RESUMO***: pra declarar o ponteiro, o * significa que aquela variabel é um ponteiro (endereço 
de memória). pra acessar o valor de um ponteiro, tb uso o * (isso que é confuso 
mas é preciso separar). e pra acessar o endereço de um valor, uso o &

🔸Na linguagem C, quando declaramos um ponteiro, informamos ao compilador
para que tipo de variável poderemos apontá-lo. Um ponteiro do tipo int* só pode
apontar para uma variável do tipo int (ou seja, esse ponteiro só poderá guardar o endereço
de uma variável int

🔸Um ponteiro pode ter um valor especial NULL, que é o endereço de nenhum lugar.

🔸A constante NULL está definida na biblioteca stdlib.h. Trata-se de um valor reservado
que indica que aquele ponteiro aponta para uma posição de memória inexistente.
O valor da constante NULL é ZERO na maioria dos computadores. Não confunda um ponteiro apontando para NULL com um ponteiro não inicializado.
O primeiro possui valor fixo, enquanto um ponteiro não inicializado pode possuir
qualquer valor.

🔸toda vez quea variável passada por referência for usada dentro da função, 
o operador “*” deverá ser usado na frente do nome da variável

🔸Arrays são sempre passados por referência para uma função. Além do parâmetro 
do array que será utilizado na função, é necessário declarar um segundo parâmetro 
(em geral, uma variável inteira) para passar para a função o tamanho do array **separadamente**.
Quando passamos um array por parâmetro, independentemente do seu tipo, o que 
é de fato passado para a função é o endereço do primeiro elemento do array. 

🔸A passagem de arrays por referência evita a cópia desnecessária de grande quantidade
de dados para outras áreas de memória durante a chamada da função, o que afetaria o
desempenho do programa.

🔸Para arrays com mais de uma dimensão é necessário especificar o tamanho de todas
as dimensões, exceto a primeira.

🔸The point size is architecture driven. I can print the return of a pointer using
%ld (long integer). I have to type cast though, because a pointer is actually 
a char. So I have to type cast from char to long integer

🔸why is that??
For 64 bit architecture, the pointer size will be 8 bytes
For 32 bit architecture, the pointer size will be 4 bytes. 
For 16 bit, 2 bytes.
```

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *p = (int *)malloc(sizeof(int)); // p holds the address of allocated memory
    
    if (p == NULL) {
        fprintf(stderr, "Memory allocation failed\n");
        return 1;
    }

    *p = 5000; // The value 5000 is stored in the memory location pointed to by p
    
    printf("Address of allocated memory: %p\n", (void *)p); 
    printf("Value stored at allocated memory: %d\n", *p);
    printf("Address of the pointer variable p: %p\n", (void *)&p); 

    free(p); // Free the allocated memory
    
    return 0;
}

Address of allocated memory: 0x55f89ca712a0
Value stored at allocated memory: 5000
Address of the pointer variable p: 0x7ffd17ae0000
```

ALOCAÇÃO DINÂMICA

```
🔸A alocação dinâmica permite ao programador “criar” arrays em tempo de
execução, ou seja, alocar memória para novos arrays quando o programa está sendo
executado, e não apenas quando se está escrevendo o programa. Ela é utilizada quando
não se sabe ao certo quanto de memória será necessário para armazenar os dados com
que se quer trabalhar. Desse modo, pode-se definir o tamanho do array em tempo de
execução, evitando assim o desperdício de memória

🔸A alocação dinâmica consiste em requisitar um espaço de memória ao computador, em
tempo de execução, o qual, usando um ponteiro, devolve para o programa o endereço
do início desse espaço alocado.

🔸Diferentemente das variáveis declaradas durante o desenvolvimento do programa,
as variáveis alocadas dinamicamente não são liberadas automaticamente por ele

```

```c
/*
Exemplo usando ponteiros
*/

include <stdio.h>
include <stdlib.h>
void soma _ mais _ um(int *n){
*n = *n + 1;
printf(“Dentro da funcao: x = %d\n”,*n);
}
int main(){
int x = 5;
printf(“Antes da funcao: x = %d\n”,x);
soma _ mais _ um(&x);
printf(“Depois da funcao: x = %d\n”,x);
system(“pause”);
```

```c
/*Declarar uma função que recebe um array*/
void imprime (int *m, int n);
void imprime (int m[], int n);
void imprime (int m[5], int n);

/*Mesmo especificando o tamanho de um array no seu parâmetro da função, a semântica
é a mesma das outras declarações, pois não existe checagem dos limites do array em
tempo de compilação.*/

/*Passagem de array como parâmetro*/
void imprime (int *n, int m){
int i;
for (i=0; i<m;i++)
printf(“%d \n”, n[i]);
}
int main(){
int v[5] = {1,2,3,4,5};
imprime(v,5);
system(“pause”);
return 0;
}
```

TIPOS DEFINIDOS PELO PROGRAMADOR

```
🔸Para criar um novo tipo de dado, um dos seguintes
comandos pode ser utilizado:
•• Estruturas: comando struct
•• Uniões: comando union
•• Enumerações: comando enum
•• Renomear um tipo existente: comando typedef

🔸**struturas: struct**
Uma estrutura pode ser vista como um conjunto de variáveis sob o mesmo nome,
e cada uma delas pode ter qualquer tipo (ou o mesmo tipo). A ideia básica por trás
da estrutura é criar apenas um tipo de dado que contenha vários membros, que nada
mais são do que outras variáveis. Em outras palavras, estamos criando uma variável que
contém dentro de si outras variáveis.
As estruturas podem ser declaradas em qualquer escopo do programa (global ou local).

🔸exemplo de definição de struct com typdef:
typedef struct cadastro{
char nome[50];
int idade;
char rua[50];
int numero;
} cad;

quando usar struct, pra acessar os valores posso usar dois operadores. Operador '.' ou 
'->'. Utilize o primeiro quando a variavél que to usando pra acessar não é o ponteiro
desse struct. Utilizar o segundo quando for um ponteiro

🔸Apesar disso, a maioria das estruturas é declarada no escopo global. Por se tratar de
um novo tipo de dado, muitas vezes é interessante que todo o programa tenha acesso
à estrutura. Daí a necessidade de usar o escopo global.

🔸A uma estrutura que contenha outra estrutura dentro dela damos o nome e struturas 
aninhadas (um tipo de objeto contendo outros tipos de objetos)

🔸Para o programador, uma enumeração pode ser vista como uma lista de constantes,
em que cada constante possui um nome significativo. Porém, para o compilador, cada
uma das constantes é representada por um valor inteiro, e o valor da primeira constante
da enumeração é 0

🔸unions
An union in C is similiar to a structure except that all of its members start at
at the same location in memory. An union variable can represent the value of only
one of its members at a time. So I should use an Union when Im going to use only 
one of its properties, since assigning writing to an union variable overrides 
the previous value
```

CLASSES DE ARMAZENAMENTO DE VARIAVÉIS

Definem o scopo, visibilidade e lifetime da variavél

| static | if I want a global variable that is private to a function and a file. I use it to define a variable inside of a given scope. This way, if I try to access that variable from another file using extern, it won’t allow |
| --- | --- |
| extern | used to access a global variable defined in another file. |
| auto  | A classe de armazenamento de variáveis auto em C é usada para declarar variáveis locais que são automaticamente desalocadas quando a função em que foram definidas termina sua execução. Na verdade, todas as variáveis locais, por padrão, são `auto`, então essa palavra-chave raramente é usada explicitamente
 |
| register | A classe de armazenamento register serve para especificar que uma variável será
muito utilizada e que seria interessante armazená-la no registrador da CPU do compu-
tador porque o tempo de acesso aos registradores da CPU é muito menor que o tempo
de acesso à memória RAM, onde as variáveis ficam normalmente armazenadas. |

MODIFIERS

```
Use cases for CONST
(1) uint_8 const data = 50;

(2) uint_8 const *pData = (uint*) 0x4000 => Modifiable pointer and const data
The pointer pData is modifiable but the data pointed by the pData cannot be modifiable
pData is a pointer pointing to a read-only variable. The address can change, but the 
value cannot

(3) uint_8 *const pData = (uint*) 0x400 => Modifiable data and constant pointer

(4) uint_8 const *const pData  = (uint*) 0x4000 => const data and const pointer

Volatile
use with variables to instruct the compiler not to invoke any optimization on the
variable operation. It tells the compiler that the value of the variable may change 
at any time with or without the programmer's consent. So, the compiler turns off 
optimizing the read-write operations on the variable wich are declared using 
volatile keyword

A variable must be declared using a volatile qualifier when there is a possibility
of unexpected changes in the variable value. The unexpected changes in the variable
may come from inside the code or outside the code ()

```

```c
/*Array de estruturas*/
struct cadastro{
char nome[50];
int idade;
char rua[50];
int numero;
};
int main(){
struct cadastro c[4];
int i;
for(i=0; i<4; i++){
gets(c[i].nome);
scanf(“%d”,&c[i].idade);
gets(c[i].rua);
scanf(“%d”,&c[i].numero);
}
system(“pause”);
```

```c
/*Um ponteiro pode receber um valor hexadecimal representando um endereço de memória
diretamente. Isso é muito útil quando se trabalha, por exemplo, com microcontroladores*/

#include <stdio.h>
#include <stdlib.h>
int main(){
//Endereço hexadecimal da porta serial
int *p = 0x3F8;
//O valor em decimal é convertido para seu valor
haxadecimal: 0x5DC
int *p1 = 1500;
printf(“Endereco em p: %p \n”,p);
printf(“Endereco em p1: %p \n”,p1);
system(“pause”);
return 0;
}
Saída Endereco em p: 000003F8
Endereco em p1: 000005DC
```

BUILD PROCESS

```
Preprocessing
Parsing
Produces object files
Links object files
Produces final executable
Post processing of final executable

🔸we download the executable into the flash memory of the microcontroller. so, how
does the generated data (eg. global variables) of the program ends up in the ram?
to analyze this, there's an executable that with a given flag displays the contents of 
the section header of the .elf file.

🔸LMA: Load memory address (source in flash). where the data is currently loaded
	VMA: virtual memory address (source in sram). (this is not really virtual). where data 
	should finally be copied to 
	
🔸moving the data from flash to ram, is done by software. In a STM32, for example, 
this is done by a startup code, wich implements some routines for handling this

🔸.elf: used for debugging
.bin and .hex: pure binaries executables, these are used for production
```

| .text | This section contains the executable code of the program. It includes the machine code generated from the C source files. |
| --- | --- |
| .data | This section contains initialized global and static variables. The data in this section can be modified at runtime |
| .bss | This section contains uninitialized global and static variables. It does not take up space in the disk file but is allocated in memory at runtime. |
| .rodata |  This section contains read-only data, such as string literals and constant variables |
| .debug | This section contains debugging information used by debuggers. It is usually present in ELF files compiled with debugging information (e.g., with the `-g` option). |
|  |  |

MICROCONTROLLERS

```
🔸Microcontrollers stores the executable in non volatile memory (flash or EEPROM) and 
stores data of the program in volatile (SRAM, RAM, FRAM..) memory

🔸Some IDEs give support for browsing the memory of the microcontroller and seeing by 
each address its content. For this I have to know the base address of the memories 
(at what address does it start saving bytes).

🔸disassemble is the process of translating a program, from machine code into higher 
level programming language. we can use objdump tool to disassemble the machine code 
generated. this is useful when I want to debug at the instruction level 

🔸A processor is tipically described as this example:
Processor: ARM Cortex M4
Processor architecture: ARMv7E-M
Instrunction set architecture(ISA): Thumb-2

🔸the assembly code, among other things, load and store data from the processor registers
back and forth to the memory 

🔸IO pins are controlled using peripheral registers (GPIO peripheral registers) 
which are mapped on to processor addressable memory locations.

🔸Processor addressable locations are the different locations serving different
	purposes. besides there's a picture of it 
	
🔸Cross compilation is to compiling code on a given host with a specific archictecture 
to a different architecture (the target)

🔸An embedded application never ends. if the application has nothing to do, it either puts 
the processor to sleep or executes an infinite looop

🔸32 bit address channel, means 2 to the power of 32 different memory locations

🔸A processor has an address generation unit that will get activated when a instruction
is decoded

🔸In a 32-bit system, each memory address typically points to an 8-bit byte of memory. Therefore, a 32-bit value spans 4 consecutive bytes in memory.

🔸ARM Cortex M4 talks to flash memory via I-Bus (instruction bus) and D-bus (data bus). These are two of the three Advanced High Perfomance (AHB) buses. 
The third one is S-Bus (system bus) 

🔸In a typical modern microcontroller there can be different sources for the clock, such as:
1 - Crystal oscillator (External source) (HSE -> High speed external)
2 - RC oscillator (Internal) (HSI -> High speed internal)
3 - PLL (Phase Locked Loop) (Internal). This is used to boost HSE and HSI
This is altered with RCC peripheral registers (RCC clock control registers)

Peripheral clocks of all almost all peripherals will be disabled by default to save power,
that's way before using it, I have to enable it, and before enablint it

RCC is a system related peripheral, mainly used for reset and clock control 

MCU vector table holds addresses of various exception and interrupt handlers. I can write error handlers for a giving domain by 
writing functions that take as pointers the address of the expection handler of that giving domain. At the vector table there are
addresses defined for each interrupt. When the interruption happens, that address will point to some other address, where handle
function is defined. In ARM, all interupts and exception handlers are connected to NVIC (Nested Vectored Interrupt Controller).
Some interrupts are delivered through EXTI lines before getting to NVIC, as another way of hardware control of the interrupts.
In STM32 GPIOs interrupts go through EXTI lines, so this connection has to be configured using its registers (Interrupt mask register)
```

GPIO

```

GPIOD PERIPHERAL REGISTERS
(one registers controls the given property of all the ports of a given GPIO)

1 - GPIO port mode register 
.
.
.
5 - GPIO port input data register
6 - GPIO port output data register 

🔸Procedure to turn on the led
- (1)Identify the GPIO port
- (2)Identify the GPIO pin and the memory address of the GPIO peripheral register
- (3)Activate the GPIO peripheral (RCC registers) (Enable the clock of its bus peripheral eg. AHB2) 
- (4)Configure the GPIO pin mode as input/output
- (5)Write to the GPIO pin high/low

Example:
Address of the clock control register (AHB2)
0x4002 1000(base address of RCC) + 0x4C(AHB2 offset) = 0x4002104c

Address of the GPIOB mode register (third picture on comments*)
0x4800 0400(base address of GPIOB) + 0x00(offset) = 0x48000400

Address of the GPIOB outuput data register (used to write)
0x4800 0400(base address of GPIOB) + 0x14(offset) = 0x48000414

```

OTHER

```
🔸Na linguagem C, um valor hexadecimal deve começar com “0x” (um zero seguido
de um x)

🔸In a 32-bit system, each memory address typically points 
to an 8-bit byte of memory. Therefore, a 32-bit value spans 4 consecutive 
bytes in memory.

🔸Registers are usually of 32 bit size

🔸In modern microcontrollers, flash memory has largely replaced traditional ROM. 
When we refer to ROM in the context of a microcontroller today, we are often 
actually referring to the flash memory where the firmware is stored. ROM is also refered to as
system memomry

🔸heap: for dynamic memory allocation
🔸stack: for transient data. a stack will be tracked by the stack pointer register
of the processor

🔸startup code copies global data to the part of the RAM that stores this kind of 
data. for data that goes to the stack, this is done during runtime

🔸compiler takes care of generating instructions wich will arrange wich will arrange
variables in the memory according to the variables natural size and that is called
align data storage

🔸O uso de um buffer é uma questão de eficiência. Para ler e escrever arquivos no
disco rígido é preciso posicionar a cabeça de gravação em um ponto específico do disco
rígido. E isso consome tempo. Se tivéssemos que fazer isso para cada caractere lido ou
escrito, as operações de leitura e escrita de um arquivo seriam extremamente lentas. As-
sim, a gravação só é realizada quando há um volume razoável de informações a serem
gravadas ou quando o arquivo for fechado.

🔸where are variables stored
🔸Global Variables:
Initialized globals: Initial values in flash, runtime storage in RAM.
Uninitialized globals: Zero-initialized in RAM at startup.
Constant globals: Stored in flash and cannot be altered even by its address
because flash is read protected
modifying the value of a global const variable during runtime makes a program crash
in the host. in the target, the operation has no effect. because flash is read protected

🔸Dado global não inicializado é armazenado na seção “.bss” da memória de dados 
(SRAM) e inicializado com o conteúdo zero. Esse dado não carrega informação 
importante. Dado global não inicializado não é armazenado na FLASH para não 
consumir espaço da memória de programa com informação não relevante.

🔸Dado global inicializado é armazenado na seção “.data” da memória de programa 
(FLASH), e também é copiado para a seção “.data” da memória de dados (SRAM), 
durante o processo de inicialização (startup code). Esse dado carrega informação 
importante.

🔸Dado global estático não inicializado é um dado privado, e é armazenado na 
seção “.bss” da memória de dados (SRAM) e inicializado com o conteúdo zero. 
Esse dado não carrega informação importante.

🔸Dado global estático inicializado é armazenado na seção “.data” da memória de 
programa (FLASH), e também é copiado para a seção “.data” da memória de dados 
(SRAM), durante o processo de inicialização (startup code). Esse dado carrega 
informação importante.

🔸Dado local não inicializado e inicializado é armazenado no “stack ou execution 
stack ou program stack” da memória de dados (SRAM). Esse dado está relacionado 
com o escopo da função, então, é um dado transiente que é criado e destruído dinamicamente. 
Quando o programa entra na função o dado é criado 
e quando retorna da função o dado é destruído.

🔸Dado local estático não inicializado é um dado global que é privado para o escopo 
da função, e é armazenado na seção “.bss” da memória de dados (SRAM), e 
inicializado com o conteúdo zero.

🔸Dado local estático inicializado é um dado global que é privado para o escopo 
da função, e é armazenado na seção “.data” da memória de programa (FLASH), que 
também é copiado para a seção “.data” da memória de dados (SRAM), durante o
processo de inicialização (startup code).

🔸Dado global constante é armazenado na seção “.rodata” da memória de 
programa/código (FLASH).

🔸Dado local constante é armazenado no “stack” da memória de dados (SRAM).
```

USEFUL STUFF FROM DATASHEET

```
Block diagram - datasheet
Memory map - reference manual 
Interrupt and exception vector table - reference manual
Alternate function pins - datasheet
EXTI block diagram
```

DRIVER DEVELOPMENT

```
🔸The driver layer exposes various APIs to the application layer. And the sample application will use the APIs provided by your
driver file in order to control the peripherals which are there in the microcontroller

🔸For Microcontrollers, we also have to write a device header file specific to that microcontroller. 
Which contains the microcontroller specific details such as:
(1) the base addresses of various memories present in a microcontroller such as flash,SRAM memories like 
SRAM1, SRAM2, ROM etc.
(2) Base addresses of various bus domains such as APB domain AHB domain
(3) Clock management macros like clock enable macros and clock disable macros in order to deal with the 
peripheral clock management of various peripherals
(4) IRQ definitions
(5) Peripheral register definition structures.
(6) (5) Peripheral register bit definitions.
```

UART

```
Data transmission steps
- Program the M bit in USART_CR1 to define the word length
- Program the number of stop bits in the USART_CR2 register
- Select the desired baud rate using USART_BRR register.
- Set the TE bit in the USART_CR1 to enable the transmit block.
- Enable the USART by writing the UE bit in USART_CR1 register to 1.
- Now, if TXE flag is set, then write the data byte to send, in the USART_DR register.

- Repeat this for each data to be transmitted. After writing the last data into the
USART_DR register, wait until TC flag is set to 1. 
This indicates that the transmission of the last frame is complete. Remember, after 
data transmission,if software wants to disable USART or UART peripheral, 
then it has to do it after TC bit is set where TC stands for Transmission 
Complete flag.

Data reception steps
- Program the M bit in the USARRT_CR1 to define the word length. Both transmitter 
and receiver must agree upon this word length
- Program the number of stop bits in the USART_CR2 register
- Select the desired baud rate using the baud rate register USART_BRR. 
The baud rate of UART transmitter and receiver must be same
- Enable the USART by writing the UE bit in the USART_CR1 register to 1
- Set the RE bit in the USART_CR1 register which enables the receiver block of 
the USART peripheral. Once the receiver block is enabled,it starts searching 
for the start bit.
- When the character is received, wait until the RXNE bit is set. If RXNE bit is 
set, it indicates that the content of the shift register is transferred to 
the read data register.

```

USEFUL TYPE ALIASES

| `Type` | `Description` |
| --- | --- |
| **`Fixed-Width Integer Types`** |  |
| int8_t | 8-bit signed integer |
| uint8_t | 8-bit unsigned integer |
| int16_t | 16-bit signed integer |
| uint16_t | 16-bit unsigned integer |
| int32_t | 32-bit signed integer |
| uint32_t | 32-bit unsigned integer |
| int64_t | 64-bit signed integer |
| uint64_t | 64-bit unsigned integer |
| **`Minimum-Width Integer Types`** |  |
| int_least8_t | At least 8-bit signed integer |
| uint_least8_t | At least 8-bit unsigned integer |
| int_least16_t | At least 16-bit signed integer |
| uint_least16_t | At least 16-bit unsigned integer |
| int_least32_t | At least 32-bit signed integer |
| uint_least32_t | At least 32-bit unsigned integer |
| int_least64_t | At least 64-bit signed integer |
| uint_least64_t | At least 64-bit unsigned integer |
| **`Fastest Integer Types`** |  |
| int_fast8_t | Fastest signed integer with at least 8-bit width |
| uint_fast8_t | Fastest unsigned integer with at least 8-bit width |
| int_fast16_t | Fastest signed integer with at least 16-bit width |
| uint_fast16_t | Fastest unsigned integer with at least 16-bit width |
| int_fast32_t | Fastest signed integer with at least 32-bit width |
| uint_fast32_t | Fastest unsigned integer with at least 32-bit width |
| int_fast64_t | Fastest signed integer with at least 64-bit width |
| uint_fast64_t | Fastest unsigned integer with at least 64-bit width |

| **`Integer Types with the Same Width as Pointer`** |  |
| --- | --- |
| intptr_t | Signed integer type capable of holding a pointer |
| uintptr_t | Unsigned integer type capable of holding a pointer |
| **`Integer Types with the Same Width as Size`** |  |
| size_t | Unsigned integer type for sizes |
| ptrdiff_t | Signed integer type for the difference between pointers |
| **`Limits for Fixed-Width Integer Types`** |  |
| INT8_MIN | Minimum value for int8_t |
| INT8_MAX | Maximum value for int8_t |
| UINT8_MAX | Maximum value for uint8_t |
| INT16_MIN | Minimum value for int16_t |
| INT16_MAX | Maximum value for int16_t |
| UINT16_MAX | Maximum value for uint16_t |
| INT32_MIN | Minimum value for int32_t |
| INT32_MAX | Maximum value for int32_t |
| UINT32_MAX | Maximum value for uint32_t |
| INT64_MIN | Minimum value for int64_t |
| INT64_MAX | Maximum value for int64_t |
| UINT64_MAX | Maximum value for uint64_t |

| `Biwise operator` | `Name` | `Example` | `Explanation` |
| --- | --- | --- | --- |
| `&` | Bitwise AND | a & b | 0101 & 0011 = 0001  |
| | | Bitwise OR | a | b | 0101 | 0011 = 0111 |
| `^` | Bitwise XOR | a ^ b | 0 if they are equal is 1, if different  0 |
| ~ | Bitwise NOT (Complement) | ~a | ~0101 = 1010 (Bitwise complement) |
| << | Bitwise Left Shift | a << 2 | 0101 << 2 = 010100 (Result is 20 in decimal) |
| >> | Bitwise Right Shift | a >> 2 | 0101 >> 2 = 0001 (Result is 1 in decimal) |

| `Testing of bits` | $ |
| --- | --- |
| `Setting of bits` | | |
| `clearing of bits` | & |
| `toggling of bits` | ^ |

| Directive | Description |
| --- | --- |
| `#include` | Includes the contents of a specified file into the current file. |
| `#define` | Defines a macro, which can be a constant value or a function-like macro. |
| `#undef` | Undefines a previously defined macro. |
| `#ifdef` | Checks if a macro is defined and includes the following code block if it is. |
| `#ifndef` | Checks if a macro is not defined and includes the following code block if it is not. |
| `#endif` | Ends a conditional directive started with `#if`, `#ifdef`, or `#ifndef`. |
| `#error` | Outputs an error message during compilation and stops the compilation process. |

| `#if` | Tests a compile-time constant expression and includes the following code block if it evaluates to true. always end with and  |
| --- | --- |
| `#else` | Provides an alternative code block if the previous `#if` or `#ifdef` condition is false. |
| `#elif` | Stands for "else if" and provides an additional condition if the previous `#if` or `#ifdef` was false. |
