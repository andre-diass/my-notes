# Java: Entendendo a Orientação a Objetos

**Criado:** March 9, 2023 11:35 AM  
**Atualizado:** April 11, 2023 10:29 AM

## Notas

- Dado e funcionalidade andam juntos.
- A variável que vem depois do nome da classe é uma referência ao `new <objeto>`.
- Ao construir objetos em Java, todos os atributos são zerados. O valor default para tipos numéricos como `int`, `double`, e `long` é 0. Para o tipo booleano, o valor é `false`.
- A palavra-chave `this` refere-se ao objeto atual em um método ou construtor. Seu uso mais comum é para eliminar a confusão entre os atributos da classe e parâmetros com o mesmo nome.
- Cuidado com o modelo anêmico.
- **Sobrescrita** não é igual a **sobrecarga**. Sobrescrita está relacionada à herança, reescrevendo um método da classe pai. Sobrecarga envolve ter vários métodos para receber diferentes argumentos.

## Instanciação, Atributos e Referências

- **Classes:** ou tipos.
- **Atributos:** características de uma classe.
- **Objeto ou Instância:** 
- **Instanciação:**
- **Construtor / Construtor Padrão**
- **Atributo Imutável**
- **Static:** para que um atributo fique como uma variável global, é necessário chamar `<nome da classe>.<nome da variável>`. Para chamar um método sem uma referência ou objeto criado, ele precisa ser static.
- **Composição de Objetos**

## Encapsulamento

- **Private:** Quando um atributo se torna privado, ele não pode ser lido ou modificado fora da própria classe.
- **Getters e Setters**

## Herança

- **Extends:** Palavra-chave para fazer uma classe filha herdar os atributos de uma classe, permitindo a reutilização de código.
- **Super Class:** ou classe base.
- **Child Class:**
- **Protected:** Visível dentro da classe e também para suas subclasses.
- **Super e Reescrita de Métodos:** Reescrita permite redefinir um comportamento previsto na classe mãe através da classe filha. O novo método na classe filha possui a mesma assinatura.
- **Sobrecarga:** Vários métodos em uma mesma classe, geralmente com o mesmo nome, mas recebendo diferentes quantidades de argumentos.

## Polimorfismo

- **Polimorfismo:** Possibilidade de criar uma instância usando o construtor de uma classe, mas usando uma variável que faz referência a outro tipo.
- **Como Funciona:** A referência define o que pode ser chamado.
- **Observações:** 
  - Objetos não mudam de tipo.
  - A referência pode mudar, permitindo o polimorfismo.
  - O polimorfismo permite usar referências mais genéricas para a comunicação com um objeto.
  - O uso de referências mais genéricas permite desacoplar sistemas.

## Herança e o Uso de Construtores

- **Construtores não são herdados:** Os construtores pertencem somente à sua própria classe e não são herdados automaticamente. É necessário reescrevê-los.
- Um construtor da classe mãe pode ser chamado através do `super()`.

## Classes e Métodos Abstratos

- Classes abstratas não podem ser instanciadas. Para instanciar, deve-se criar primeiro uma classe filha não abstrata.
- **Abstract:** É uma palavra-chave que pode ser utilizada antes de uma classe ou método.
- **Métodos Abstratos:** Não têm implementação e devem ser implementados por suas classes filhas.

## Interfaces

- Não há herança múltipla em Java para evitar duplicação de métodos. Interfaces são utilizadas para contornar essa situação.
- Todos os métodos de uma interface são abstratos.
- Interfaces garantem que todos os métodos de classes que as implementam possam ser chamados com segurança.
- Com composições e interfaces, há mais flexibilidade no código, evitando o acoplamento da herança.
- Interfaces oferecem uma alternativa ao polimorfismo, enquanto a composição oferece uma alternativa à reutilização de código.
