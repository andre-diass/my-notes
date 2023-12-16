# SQL: Consultas avançadas

## CONDICIONAIS

- `OR`, `AND` e `NOT`: condições podem ser usadas.
- `IN`: para testar mais de uma condição ao mesmo tempo.
- `LIKE`: preciso usar os sinais em volta depois de `LIKE '%<condição>%'`. Aqui vai retornar células que tenham a condição no nome, mesmo que o nome tenha outras coisas.
- `SUBSTR`: extrai uma substring de uma string.

## APRESENTAÇÃO DE DADOS

- `DISTINCT`: vai retornar linhas somente com valores diferentes. Uso depois do SELECT.
- `LIMIT <quantidade>` ou `<intervalo, intervalo>`: limita o número de linhas exibidas.
- `ORDER BY <campo>, <campo>..`: determinar direção (`ASC` ou `DESC`), os campos selecionados anteriormente serão uma ordenação secundária quando o primeiro campo retornar o mesmo valor.
- `GROUP BY`: 
    ```sql
    SELECT <campo>, <SUM/MAX/MIN/AVG/COUNT>(<campo>) AS <alias> FROM <tabela> GROUP BY <campo>;
    ```
    Pensa que o `GROUP BY` vai agrupar em uma só linha valores iguais de diferentes linhas da mesma coluna. Usando `COUNT`, por exemplo, como segunda coluna, posso saber quantos desse valor tem naquela coluna.
- `HAVING`: é um filtro como o `WHERE`, mas esse eu posso usar antes do `GROUP BY`.
- `CASE`:
    ```sql
    SELECT <campo>, CASE WHEN <condição> THEN <como vai ficar no novo campo> ELSE... END AS <novo campo> FROM <tabela>;
    ```
- `WHERE`: se liga que o `FROM` vem antes.

## JUNTANDO TABELAS E CONSULTAS

- `LEFT JOIN`: pego todo mundo da esquerda, se não tiver correspondência da direita, fica como `NULL` na direita.
- `RIGHT JOIN`: pego todo mundo da direita, se não tiver correspondência na esquerda, fica como `NULL` na esquerda.
- `FULL JOIN`: mesma lógica aplicada juntamente.
- `CROSS JOIN`: faz um produto cartesiano de todas as relações.
- `UNION`: é necessário que as tabelas que serão unidas tenham o mesmo número e tipo de campo. Quando há registros idênticos, o `UNION` faz um `DISTINCT` automático. Para executar sem o `DISTINCT`, faço um `UNION ALL`.

## FUNÇÕES

**PRA FUNÇÕES TRADICIONAIS VERIFICAR DOCUMENTAÇÃO**

- `REGEXP`: [Documentação](https://www.tutorialspoint.com/mysql/mysql-regexps.htm)
  - `^`: Beginning of string 
  - `$`: End of string 
  - `.`: Any single character  
  - `[...]`: Any character listed between the square brackets 
  - `[^...]`: Any character not listed between the square brackets 
  - `p1|p2|p3`: Alternation; matches any of the patterns `p1`, `p2`, or `p3` 
  - `*`: Zero or more instances of preceding element 
  - `+`: One or more instances of preceding element 
  - `{n}`: n instances of preceding element 
  - `{m,n}`: m through n instances of preceding element

**NUMERIC FUNCTIONS**
```sql
SELECT TRUNCATE(345.156, 0); // Return a number truncated to 0 decimal places
SELECT ROUND(135.375, 2);    // Round the number to 2 decimal places
