## PRINCIPIOS DA ORIENTAÇÃO A OBJETOS

`Coesão` é o grau em que os elementos dentro de um módulo (classe, método, pacote) trabalham juntos para realizar uma tarefa específica. 
Quanto mais coeso um módulo, mais concentradas são suas responsabilidades e mais fácil é entender e modificar seu comportamento.
Isso significa que uma classe deve ter uma única responsabilidade e métodos devem ser bem definidos para cumprir apenas uma tarefa.



`Encapsulamento` é o princípio que consiste em esconder a implementação de um objeto e permitir que os usuários acessem seus dados e comportamentos apenas por meio de uma interface pública. 
Isso significa que o estado interno de um objeto deve ser protegido contra alterações não autorizadas. Isso é alcançado definindo os campos de uma classe como privados e fornecendo métodos públicos 
para acessá-los (getters) e alterá-los (setters) de maneira controlada.



`Acoplamento` é a medida da dependência entre os módulos em um sistema. Um alto acoplamento significa que as mudanças em um módulo podem afetar vários outros módulos, 
o que torna o sistema menos flexível e mais difícil de manter. Por outro lado, um baixo acoplamento significa que os módulos são independentes e podem ser modificados 
sem afetar outros módulos. O ideal é buscar um acoplamento baixo, o que é alcançado por meio da definição de interfaces claras entre os módulos, bem como da utilização de padrões de design que 
promovem o baixo acoplamento, como o padrão de Injeção de Dependência.Em resumo, coesão, encapsulamento e acoplamento são três conceitos fundamentais em Java que ajudam a criar sistemas mais organizados, 
flexíveis e fáceis de manter. Quando aplicados corretamente, esses conceitos podem ajudar a tornar o código mais legível, reutilizável e escalável.

## Single Responsibility Principle (SRP)
A class should have only one reason to change, meaning it should have only one responsibility or function within a system.
classes/métodos/funções/módulos devem ter uma única responsabilidade bem definida;

## Open Closed Principle (OCP)
The Open/Closed Principle (OCP) is a fundamental principle of object-oriented programming (OOP) that states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, you should be able to extend the behavior of a software entity without modifying its source code. The idea behind the OCP is to create software that is modular, flexible, and easily extensible. By following this principle, you can create software that 
is easier to maintain, test, and modify over time. The OCP is typically achieved through the use of abstraction, inheritance, and polymorphism.

## Liskov Substitution Principle (LSP)
LSP states that a subclass should be able to substitute for its superclass in any context without introducing any errors or unexpected behaviors. This means that any method that works for the superclass should also work for its subclass without any modifications or special handling.
To illustrate the LSP, consider an example where you have a program that takes a list of shapes and calculates their total area. If you have a Rectangle class and a Circle class that both inherit from a Shape class, you should be able to replace any instance of the Shape class in 
the program with an instance of either the Rectangle or Circle class, without affecting the correctness of the program.

## Dependecy Inversion Principle (DIP)
states that high-level modules should not depend on low-level modules, but both should depend on abstractions.
In other words, the DIP states that classes and modules should depend on abstractions (i.e., interfaces or abstract classes), rather than concrete implementations. 
This allows for easier modification, testing, and swapping of different implementations without affecting the behavior of the higher-level modules.

## Interface Segragation Principle(ISP)
emphasizes the importance of designing interfaces that are focused and specific to the needs of the clients that use them. It was introduced by Robert C. Martin and states that clients should not be forced to depend on interfaces that they do not use.
In other words, the ISP states that interfaces should be designed in a way that each client only depends on the subset of methods that they actually use. This helps to reduce the coupling between the client and the implementing class or module, and promotes better separation of concerns.
To illustrate the ISP, consider an example where you have an interface that defines several methods, but a client only uses a subset of those methods. Instead of having the client depend on the entire interface, you could create a smaller, more focused interface that only contains the methods that the client uses. This allows the client to depend only on the subset of methods that they actually need, rather than the entire interface.
By following the ISP, you can create interfaces that are more modular, easier to understand, and more flexible over time. It also promotes better separation of concerns and promotes better overall software design.
