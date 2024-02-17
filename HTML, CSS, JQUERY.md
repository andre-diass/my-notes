# HTML, CSS, jQuery

**Criado:** March 20, 2022 10:42 AM  
**Atualizado:** February 17, 2024 9:05 PM

## Manipulando o DOM

- `.getElementByTagName("")`: Retorna uma matriz.
- `.getElementByClassName("")`: Retorna uma matriz.
- `.getElementById("")`: Retorna um único objeto.
- `path.querySelector('.element // class // id')`: Retorna apenas um objeto. O primeiro se encontrar vários.
- `path.querySelectorAll('.element // class // id')[index]`: Retorna uma matriz; posso iterar sobre esta matriz com um loop for.

### Propriedade Classlist e seus Métodos

- `class.classList.add('element')`
- `class.classList.remove('element')`
- `class.classList.toggle('element')`
- `class.classList.contains('element')`

### Event Listeners

- `element.addEventListener('click', function)`:
  - Observações:
    1. Se quiser especificar uma função, só escreva o nome da função sem os '()', pois isso chamaria imediatamente a função.
    2. Se usar `document.addEventListener`, estou criando um evento para o projeto inteiro, globalmente. Isso funciona para manipulação de teclado, por exemplo.
    3. A função também pode receber um parâmetro e, dessa forma, posso acessar as propriedades do objeto que o ouvinte de eventos criou por meio de `parâmetro.objetoPropriedade`.
    4. Para evitar o carregamento da página novamente, posso usar `e.preventDefault()`.

### Propriedades e Métodos Relacionados

- `.value`: Obtém o valor de um campo de entrada.
- `.innerHTML`: Altera o HTML.
- `.insertAdjacentHTML`
- `.textContent`
- `.style."propriedade do objeto"`: São os atributos que altero no CSS, mas em vez de ir para o CSS, posso alterá-los selecionando a propriedade do objeto.
- `.attributes`
- `.getAttribute()`
- `.setAttribute(atributo, novo valor)`

**Observações:**
- Para todos os métodos acima, posso selecioná-los usando a palavra-chave `this` ou `querySelector` ou as infinitas maneiras prováveis de selecionar um objeto.
- As classes podem ter pseudoclasses e posso usar dois pontos ":" para selecionar um estado.

## HTML

### Modelo de Caixa

- `width`: Largura; `border-width`: Largura da borda; `padding`: Espaço entre o texto e a borda do elemento; `margin`: Espaço de um elemento para o outro.

### Display

- `inline`: Apenas ocupa a largura e altura do elemento; não pode ajustar o tamanho.
- `block`: Pode ajustar o tamanho, mas ocupa toda a largura da tela.
- `inline-block`
- `none` / `visibility` / `opacity`

### Como as Coisas São Renderizadas

1. O conteúdo determina o tamanho.
2. A ordem vem do código.
3. Os filhos se sentam nos pais.

### Posicionamento

- Static
- Relative (Top, bottom, left, right): Posição relativa ao local onde deveria estar.
- Absolute (Posição relativa ao elemento pai de margem): Por exemplo, se "right", é x pixels da margem direita do elemento pai, na maioria dos casos o corpo, então é do lado direito da tela.

### Ordem de Empilhamento

- A ordem de empilhamento dos elementos é definida pela ordem no código HTML.
- Para alterar a ordem de empilhamento com CSS, posso usar o z-index. Por padrão, o z-index é 0. E isso só funciona se eu tiver definido uma posição para os elementos, usando `position: absolute`, por exemplo, porque caso contrário, eles serão block, inline...

### Centralização

- `text-align: center`: Funciona apenas se eu tiver elementos inline-block ou blocos de largura total, em outras palavras, elementos que não têm largura definida; se tiverem uma largura definida, então tenho que centralizá-los usando `margin: 0 auto 0 auto` (horizontalmente) ou `auto 0 auto 0` (verticalmente); para esse padrão de centralização, consulte a documentação.

### Fonte

- `1em = 16px = 100%`
  - Observação: em é herdado pelos elementos filhos. O tamanho da fonte aumenta, enquanto o px não, então use rem (em raiz).

## jQuery

- `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>`: Coloque isso acima do `<script.js>`.

### Seletores e Manipulação

- `$` ou `jQuery` = `document.querySelector` ou `.querySelectorAll`.
- `$("element").css("propriedade", "novo valor")`: Definindo um valor.
- `$("element").css("propriedade")`: Obtendo um valor.
- `$("element").text("novoConteúdoTexto")`: `.textContent`.
- `$("element").html("novoHTML")`: `.innerHTML`.
- `$("element").before("novoCódigoHTML")`: Para adicionar um elemento antes do elemento especificado; como `innerHTML`, mas aplicado antes do elemento especificado.
- `$("element").after("novoCódigoHTML")`: Para adicionar um elemento após o elemento especificado;
- `$("element").preappend("novoCódigoHTML")`
- `$("element").append("novoCódigoHTML")`.

### Manipulação de Exibição

- `$("element").hide()`: Para ocultar esse elemento.
- `$("element").show()`: Para mostrar.
- `$("element").toggle()`: Para ocultar.
- `$("element").fadeout()`: Para desaparecer.
- `$("element").slideup()`
- `$("element").slidedown()`
- `$("element").slidetoggle()`

### Animação

- `$("element").animate({"propriedadeCSS"})`: Somente CSS que tem um valor numérico.

### Manipulação de Atributos

- `$("element").attr("nomeDoAtributo")`: `.getAttribute`, obtém o valor do atributo; isso inclui classes, porque as classes também são atributos HTML.
- `$("element").attr("nomeDoAtributo", "novoValorDoAtributo")`: `.getAttribute`, define o novo valor do atributo.

### Event Listeners

- `$("element").click(function(){});`: Ouvinte de eventos para um evento de clique; já se aplica a todos os elementos que ele encontra, não preciso fazer um loop para selecionar.
- `$("element").keypress(function(){});`: Ouvinte de eventos para um evento de teclado; ou apenas escolha o elemento `document` (sem aspas) para ouvir qualquer pressionamento de tecla.
- `$("element").on("tipoDeEvento", function(){});`: Para escolher um tipo de evento diferente.

### Manipulação de Classes

- `$("element").addClass("primeiraClasse segundaClasse")`.
- `$("element").removeClass("classe")`.
- `$("element").hasClass("classe")`: Verifica se essa classe está aplicada; retorna um booleano.
