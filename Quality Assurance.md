# Quality Assurance

- **Created:** March 9, 2023 3:10 PM
- **Updated:** March 13, 2023 7:01 PM

## BDD - Behavior Driven Development (Desenvolvimento Guiado por Comportamento)

A semântica para estruturar esse cenário de teste utiliza as palavras-chave dado, quando e então da seguinte maneira:

- **DADO:** Pré-condições devem ser verdadeiras para que eu execute o teste?
- **QUANDO:** Qual ação será executada no sistema que fornecerá o resultado validado?
- **ENTÃO:** De acordo com a ação disparada, qual será o resultado esperado?

**Exemplo:**
Dado que há um usuário no sistema <AluraPic>, quando ele digitar o username e a senha incorreta e clicar no botão para confirmar, então deverá receber uma mensagem de senha incorreta.


## Testes e Cenários de Teste

- **Testes Funcionais:** São os testes definidos de acordo com os requisitos funcionais do software.
- **Fluxos de Teste:** Podemos pensar nos testes construindo E ou tabelas de decisão conforme as regras de negócio do projeto.
- **Conceitos de Cenário de Teste:** Definem “O que” deve ser testado, enquanto os Casos de Testes definem “Como”, ou seja, o passo a passo. O caso de teste é mais detalhado.
- **Plano de Teste:** Define e comunica a intenção e esforço do teste. Serve, por exemplo, para ganhar a aceitação e aprovação dos envolvidos, comunicar e justificar o prazo de teste planejado.

## Qualidade

**Manifesto de Teste Ágil:**
- Testar durante o desenvolvimento.
- Prevenir bugs.
- Testar o entendimento, não só a funcionalidade.
- Construir um sistema melhor.
- Todo o time é responsável pela qualidade.

- **Qualidade de Software:** Pode ser entendida como um conjunto de características a serem satisfeitas, de modo que o produto atenda às necessidades de seus usuários. Falamos de fazer o software certo para o usuário certo.
- **Papel de QA em um Time Ágil:** Exige ser generalista, olhar o software como um todo de maneira que minimize custos, tempo e efeitos indesejáveis. Isso deve ser feito o mais breve possível, ajudando assim a construir um projeto melhor.
- **Ciclo de Desenvolvimento de Software em Cascata:** As etapas do projeto são feitas uma após a outra de forma síncrona. Portanto, neste esquema, é dada muita ênfase às fases de análise e projeto antes de partirmos para a programação de fato. Uma desvantagem é que dessa forma fica difícil prevenir erros, dado que a etapa de testes fica apenas no final.
- **Modelos Ágeis:** A abordagem iterativa enfatiza a entrega rápida de uma aplicação em componentes funcionais completos, com entregas menores. A pessoa responsável de QA consegue participar de todo o processo de desenvolvimento.
- **Critérios de Aceite:** São os valores máximos ou mínimos aceitáveis para uma funcionalidade ser aceita.
- **Definição de Pronto (DoD - Definition of Done):** São pontos que definem se uma atividade foi concluída ou não. Ela deve valer para o projeto como um todo.

## Aprofundando nos Tipos de Teste

- **Teste de Regressão:** É uma técnica que consiste na aplicação de testes na versão mais recente do software, garantindo que não surgiram novos defeitos em componentes já analisados. Então, ao juntar uma nova funcionalidade, garantimos que os componentes restantes do sistema não apresentem novos defeitos.
- **Teste de Sanidade:** É o subconjunto do teste de regressão e também é realizado quando não temos tempo suficiente para fazer o teste mais elaborado. Ele tem um nível superficial e verifica se as funcionalidades mais críticas do sistema estão conforme o esperado.
- **Teste de Limite:** Consistem em testar os valores mínimo e máximo (ou primeiro e último valores) de uma partição. Essa técnica é geralmente usada para testar requisitos que exigem um intervalo de números (incluindo datas e horas).
- **Teste de Estado:** É utilizado para testar a capacidade que o software tem de entrar em e sair de estados definidos através de transições válidas e inválidas.
- **Testes Não Funcionais:** Têm como objetivo testar aspectos do software que não são associados a funcionalidades. Exemplo: escalabilidade, desempenho, segurança.
- **Teste de Performance:** Carga, Capacidade, Stress.
- **Teste de Usabilidade:** Tem como objetivo observar usuários reais usando o software para descobrir problemas e pontos de melhoria.
- **Teste de Segurança**

## Pirâmide de Testes

- **Testes de Caixa Branca:** É usado para testar um sistema de software com base em sua arquitetura. Exemplos: teste unitário, teste de integração de componentes, testes de serviços.
- **Teste de Caixa Preta:** É usado para testar a funcionalidade do sistema, independentemente de seu código. Exemplo: testes de aceitação, teste de sistema, teste de usabilidade.

**Evidência de Teste:** São imagens e/ou vídeos que comprovam que um determinado teste foi executado e o resultado esperado foi obtido. Exemplo: gravador de passos do Windows.

**Pirâmide de Testes:** Na base da pirâmide ficam os testes da menor parte testável de uma aplicação, aqueles que testam a classe ou uma função dentro do código, ou seja, os testes de unidade. No meio, os testes de integração, que testam como diferentes módulos do sistema interagem entre si, como os de comunicação entre serviços, comunicação com bancos de dados e assim por diante. No topo, teremos os testes de ponta a ponta que buscam testar todo o fluxo de funcionamento da aplicação.

## Estratégia de Teste

O escopo de testes fala sobre a abrangência dos testes, o que será executado e o que ele deixa de fora, tipos e níveis de testes que serão executados, responsabilidades e como será feito o lançamento do sistema.

**Ferramentas para QAs:** TestLink, Jira,
