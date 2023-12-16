# SQL: Consultas básicas

## Introdução

- `DDL:` DDLs são a parte da linguagem SQL que permite a manipulação das estruturas do banco de dados. Como, por exemplo, criar um banco, tabelas, índices, apagar as tabelas e alterar a política de crescimento de índice
- `DML:` Esse grupo visa gerenciar os dados: incluindo, alterando e excluindo informações nas estruturas do banco, como as tabelas
- `DCL:` Administrar o banco de dados como, por exemplo, o controle de acesso, o gerenciamento do usuário, gerenciar o que cada usuário(a) pode ou não visualizar, gerenciar o banco ao nível de estrutura

## Notas

- `MISSÃO CRÍTICA:` todo sistema tecnológico fundamental para que os serviços de uma empresa continuem operando sem interrupções.
- `SOBRE CHAVES E INDÍCES:` Quando temos uma chave estrangeira, automaticamente o banco de dados cria índices nos campos que se interrelacionam, para que seja viável, por exemplo, ao cadastrar um cliente na "tabela_vendas" o banco de dados, internamente, verifique se o cliente consta na "tabela_cadastro_clientes" e para encontrar rápido é proveitoso que a tabela original já possua índice
- `CONCEITOS RESUMO_1:` No banco de dados há diversas tabelas, composta por campos (colunas) e registros (linhas), essas tabelas possuem chaves estrangeiras, primárias e podem conter índices.

## Definições

- `ENTIDADES:` Estruturas que organizam como os dados são armazenados.
- `TABELA:` Uma das principais entidades e podendo conter várias no mesmo banco de dados.
- `CAMPO:` Seria a coluna.
- `REGISTROS:` Linhas.
- `CHAVE PRIMÁRIA:` Valores de uma linha que não podem se repetir.
- `CHAVE PRIMÁRIA COMPOSTA:` O que não pode repetir é a combinação entre as colunas.
- `CHAVE ESTRANGEIRA:` No banco de dados podemos ter várias tabelas, cada uma possui fragmento da informação armazenada, podendo essas tabelas se relacionarem através da chave estrangeira.
- `INTEGRIDADE:` Relação e conexão entre as tabelas.
- `ÍNDICE:` O índice permite, por exemplo, que a busca se inicie nas linhas que os nomes começam com a letra X e a partir disso, procurar o nome Xictorino, tornando a busca mais rápida. Portanto, o índice serve para facilitar e agilizar a procura.
- `ESQUEMAS:` É o conjunto de tabelas que representam o mesmo assunto. As tabelas de esquemas diferentes podem se relacionar, transformar em Schemas é apenas uma forma de agrupar as tabelas por tema, sendo mais utilizado no sentido de organização.
- `VIEW:` Após conseguir unir duas ou mais tabelas e gerar um resultado para uma consulta, podemos transformar-lá em uma view. A view possui um comportamento similar a tabela, mas que por trás dela já há uma consulta estabelecida com as regras de negócio para agrupar as informações solicitadas. Em SQL, tratamos as views como tabelas já existentes, contudo, na verdade, é uma lógica por trás. Algumas views podem ter performances não muito ágeis caso seja construída por comandos SQL muito custosos ou rebuscado.
- `JOIN:` Temos no SQL comandos de consultas (queries) e ao realizar essa consulta precisamos definir em quais tabelas gostaríamos de buscar essas informações. Caso esses dados que queremos, esteja apenas em uma tabela, basta incluir o nome dela. Já se essas informações estiverem em mais de uma tabela, será necessário utilizar a cláusula.
- `PROCEDURES:` Para fazer algum tipo de lógica estruturada com if, while, entre outros comandos de repetições.
- `FUNÇÃO:` Cálculos montados com campos que podemos usar dentro de um comando de consulta. Podemos criar uma função que facilite uma visualização ou contabilização e usa-lá para realizar as consultas.
- `TRIGGER:` Este é um aviso programado caso algo ocorra no banco de dados ou tabela. Como, se quisermos ser avisados caso alguém realize alguma alteração ou delete informações nas tabelas.

## Comandos básicos

- `SELECT * FROM <tabela>`
- `SELECT <campo> <campo>.. FROM <tabela>`
- `SELECT <campo> <campo>.. FROM <tabela> WHERE <campo>`  <!-- No WHERE, posso usar os símbolos de operação de maior e menor -->

- `USE <database>`
- `CREATE DATABASE <database>`
- `DROP <database>`
- `DROP TABLE <table>`
- `INSERT INTO <table> (<coluna>, <coluna>..) VALUES (<valor>, <valor>..)`
- `UPDATE <tabela> SET <campo> = <novo valor> WHERE <chave primária ou um valor único>`
- `DELETE FROM <tabela> WHERE <chave primária ou um valor único>`
- `ALTER TABLE <tabela> ADD PRIMARY KEY <nome da coluna que vai ser a chave primária>`
- `ALTER TABLE <tabela> ADD COLUMN (<nova coluna> <tipo de dado>)`

# Tipos de Dados

## Campos Numéricos (Inteiros e Decimais):

- **Inteiros:**
  - `TINYINT`
  - `SMALLINT`
  - `MEDIUMINT`
  - `INT`
  - `BIGINT`

- **Decimais:**
  - Precisão Fixa e Ponto Flutuante (`FLOAT` OU `DOUBLE`)
  - Decimais Fixos: `DECIMAL` E `NUMERIC`
  - `BIT`

## Data e Hora: <!-- Ao trabalhar com datas no formato '2015-01-01', posso selecionar algo específico, como `YEAR(<nome do campo que tem a data>)` -->

- `DATE`
- `DATETIME`
- `TIMESTAMP`
- `TIME`
- `YEAR`

## String:

- `CHAR`
- `VARCHAR`: Não armazena os espaços
- `BINARY`
- `VARBINARY`
- `BLOB`: `TINYBLOB`, `BLOB`, `MEDIUMBLOB` e `LONGBLOB`
- `TEXT`: `TINYTEXT`, `TEXT`, `MEDIUMTEXT` e `LONGTEXT`

## Outros:

- `SPATIAL`
- `POINT`
- `LINESTRING`
- `GEOMETRY`
- `POLYGON`

## Atributos de Campos Numéricos:

- `signed` e `unsigned`
- `zerofill`
- `auto_increment`
- `set` e `collate`: Estão relacionados com as cadeias de caracteres que serão usados para armazenar o texto. Caso queira guardar texto em alguma língua diferente, por exemplo



## SQL pelo Shell:

`mysql -h localhost -u root -p`  => Depois de ter executado o SQL executável <br>
`mysqlsh`                                => spin up the server <br>
`\connect localhost -u root -p`          => conectar à porta <br>
`\sql`                                   => mudar pra sql <br>

