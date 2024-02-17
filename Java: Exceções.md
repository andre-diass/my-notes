# Java: Exceções

**Criado:** March 20, 2023 10:25 AM  
**Atualizado:** March 21, 2023 5:11 PM

## Pilha de Execução; Call Stack

- As exceções ajudam a melhorar o código do programa de várias maneiras:
  - **a)** Exceções têm um nome expressivo, documentando o problema que está ocorrendo.
  - **b)** Exceções podem ter uma mensagem, descrevendo o problema e o estado das variáveis.
  - **c)** Exceções alteram o fluxo de execução, evitando que o problema siga o fluxo "normal".
  - **d)** Exceções podem ser tratadas, permitindo que o programa volte à execução "normal" após resolver o problema.

- A pilha de execução (call stack) existe para saber qual método está sendo executado no topo e lembrar quais métodos ainda precisam ser executados.
- Quando uma exceção ocorre, ela entra na pilha de execução e altera o fluxo. Se não forem encontradas soluções dentro da pilha de execução, elas serão impressas no console.

## Tratamento de Exceções

- **Try e Catch:**
  - Para tratar uma exceção, utilizamos um bloco try-catch.
  - Exemplo de catch: `catch(<nome da classe do erro> <nome de uma variável>)`.
  - Podemos tratar múltiplas exceções com mais de um bloco catch ou usando Multi-Catch.

## Checked e Unchecked

- Existem duas categorias de exceções: Checked e Unchecked.
  - **Checked Exceptions (estendem diretamente de Exception):**
    - Exceções verificadas são aquelas que o compilador exige que o código lide ou declare.
    - Exemplos incluem IOException, SQLException, ClassNotFoundException, etc.
  - **Unchecked Exceptions (estendem de RuntimeException):**
    - Exceções não verificadas, também conhecidas como exceções de tempo de execução, não são verificadas em tempo de compilação pelo compilador.
    - Exemplos incluem NullPointerException, ArrayIndexOutOfBoundsException, IllegalArgumentException, etc.
    - Essas exceções podem ocorrer durante a execução do programa e o código de chamada não é obrigado a tratá-las ou declará-las.

## Capturando Exceções


FORMA TRADICIONAL
```JAVA
try {
 metodoPerigosoQuePodeLancarVariasExcecoes();
} catch(MinhaExcecao ex) {
 ex.printStackTrace();
} catch(OutraExcecao ex) {
 ex.printStackTrace();
}
```

FORMA MAIS ATUAL
```JAVA
try {
 metodoPerigosoQuePodeLancarVariasExcecoes();
} catch(MinhaExcecao | OutraExcecao ex) { //multi-catch
 ex.printStackTrace();
}
```
CATCH GENERICO
```JAVA
try {
    metodoPerigosoQuePodeLancarVariasExcecoes();
} catch(Exception ex) {
    ex.printStackTrace();
}
```

FINALLY E TRY WITH RESOURCES

```
quando há um bloco finally o bloco catch é opcional;

o bloco finally é sempre executado, sem ou com exceção;

O try com recursos é basicamente adicionar um parametro ao try, e dentro dele chamar o construtor e a classe apontando pra ele. porem nessa classe eu vou ter uma interface assinando um metodo pra fechar lidar com algo, tipo a sobrescrista do metodo close da interface autoclosoable

```
