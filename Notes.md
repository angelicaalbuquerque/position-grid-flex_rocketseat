# Position, grid e flexbox

### Layouts

Posicionar elementos com CSS nem sempre é uma tarefa fácil, principalmente para quem está começando.

Alguns dos métodos usados para posicionar os elementos na tela usados mais antigamente eram dos tipos:

- Tables (tabelas para deixar elementos ao lado do outro)
- Floats e clear (float deixa o elemento flutuante e clear era usado para parar de flutuar o elemento e não afetar próximos elementos)
- Frameworks e Grid Systems (pegavam a tela e a divia com linhas e colunas)

Atualmente, os tipos mais utilizados para posicionar elementos de formas mais fáceis e interessantes são:

- Flexbox
- Grid

### Position

A propriedade `position` ontrola onde, na página, o elemento irá ficar, alterando o fluxo normal dos elementos.

Lembrando que o fluxo normal dos elementos (tipo block) é ficar um abaixo do outro, a não ser no caso de elementos inline, que ficam um ao lado do outro.

- Name: position
- Value: static | relative | absolute | fixed

### Static

Por padrão, os elementos são `static`. Isso significa que os elementos irão seguir o fluxo normal do HTML, ficando um abaixo do outro.

### Relative

O `position` indica onde o elemento vai ser posicionado na página.

Ao usar o `position: relative` podemos adicionar outras propriedades como top, right, bottom, left e z-index, que vão determinar o posicionamento final do elemento.

No caso abaixo, eu movo a box1 para a esquerda com 100px e empurro 80px, mas mantenho o fluxo normal das outras caixas, ou seja, as outras caixas não foram afetadas e ficam no seu local correto.

[**Ver exemplo**](https://codepen.io/frontangie/pen/YzQLdpo)

```HTML
<div class="box box1"></div>
<div class="box box2"></div>
<div class="box box3"></div>
```

```CSS
.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.box1 {
  background-color: red;
  position: relative;
  left: 100px;
  top: 80px
}

.box2 {
  background-color: green;
}

.box3 {
  background-color: blue;
}
```

E se eu mexo para redimensionar minha tela, ainda tenho o fluxo normal, onde o espaço que "fica em branco" sobre o box verde é o espaço que seria preenchido pelo box 1.

### Absolute

Quando o posicionamento é `absolute`, ele também libera as propriedades top, right, bottom, left e z-index,, mas o elemento é deslocado, saindo do fluxo normal.

É como se eliminasse aquele "espaço em branco" deixado por um elemento (no nosso exemplo, o box1) e criasse uma nova camada, saindo do fluxo normal.

É como se o box vermelho estivesse numa camada acima/à frente da camada do verde e azul, que esta com fluxo normal.

O box vermelho passa, assim, ser referente à pagina inteira - podendo testar isso com left: 0; top: 0. Se for pra fazer relativo a outro elemento, esse outro elemento deve ter seu posicionamento padrão (static) alterado também.

O elemento de `position: absolute` é posicionado em relação ao seu _parent element_ mais próximo. Se esse elemento "pai" não existir, ele será posicionando em relação ao bloco contendo a raiz do elemento.

[**Ver exemplo**](https://codepen.io/frontangie/pen/KKqRbNq)

```HTML
<div class="box box1"></div>
<div class="box box2"></div>
<div class="box box3"></div>
```

```CSS
.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.box1 {
  background-color: red;
  position: absolute;
  left: 100px;
  top: 80px
}

.box2 {
  background-color: green;
}

.box3 {
  background-color: blue;
}
```

### Fixed

Quando aplicado o position **fixed** é como se criasse um elemento flutuante que fica fixo na página, independente do scrolling feito.

### Element Stacking

É o empilhamento de elementos, sendo a propriedade "z-index".

Podemos usar o z-index para determinar a ordem da posição do elemento. Quanto maior o z-index, mais "acima" vai aparecer o elemento.

No exemplo abaixo, os elementos estão empilhados em camadas, de modo que o último elemento (box3) tem mais força que o primeiro (box1).

Mas se eu quiser que o vermelho (box1) apareça sobre todos os outros, posso utilizar o z-index alterando sua camada como `z-index: 3;`.

Ou seja, trabalhando com z-index, é sempre eu inserir um valor maior que todos para que o elemento fica sobre todos os outros.

```HTML
<div class="box box1"></div>
<div class="box box2"></div>
<div class="box box3"></div>
```

```CSS
.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.box1 {
  background-color: red;
  position: absolute;
  left: 5px;
  top: 5px;
  z-index: 3;
}

.box2 {
  background-color: green;
  position: absolute;
  left: 10px;
  top: 10px
}

.box3 {
  background-color: blue;
  position: absolute;
  left: 15px;
  top: 15px
}
```

### Flex

**Flexbox**

- Nos permite posicionar os elementos dentro da caixa (imagine que teremos uma caixa "pai" e, dentro dela, os "filhos");
- Permite o controle em uma dimensão (horizontal ou vertical, sabendo que o padrão HTML é vertical);
- Conseguimos fazer alinhamento, direcionamento, ordenar e tamanhos.

De início, o que precisamos é pegar nossa `div` pai e aplicar o `display: flex`, para que seus filhos possam receber as popriedades Flexbox.

```css
div.parent {
  display: flex;
}
```

**Flex-direction**

- Qual a direção do flex: horizontal ou vertical
- row | column

**Alinhamento**

- justify-content
- align-items

Exemplo de aplicação de Flexbox:

```HTML
<div class="container">
  <div class="box blue"></div>
  <div class="box red"></div>
  <div class="box green"></div>
</div>
```

```CSS

body {
  height: 100vh;
  margin: 0;
  display: flex;
  align-items: center;
}

.container {
  width: 100vw;
  display: flex;
  justify-content: center;
}
.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.blue {
  background-color: blue;
}

.red {
    background-color: red;
}

.green {
    background-color: green;
}
```

Para alinhar esse elemento ao centro, poderíamos alterar o body e container da seguinte forma:

```CSS
.container {
    display: flex;
    justify-content: space-between;
}
.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.blue {
  background-color: blue;
}

.red {
    background-color: red;
}

.green {
    background-color: green;
}
```

Dessa forma, consigo sempre alinhar os elementos ao meio. Aplicando Flex em body estou posicionando os elementos dentro dessa caixa body, ou seja, somente o container. Agora, dentro de container, ao aplicar o Flex, estou mexendo em seus elementos.

### Grid

- Assim como o Flexbox, o Grid faz o posicionamento dos elementos dentro da caixa;
- Diferentemente do Flex, o Grid faz o posicionamento horizontal e vertical ao mesmo tempo;
- Pode ser flexível ou fixo;
- Cria espaços para os elementos filhos habitarem.

O grid cria colunas e linhas, como se fosse uma tabela na qual podemos escolher quais espaços queremos que o ambiente habite.

Exemplo de página com topo/conteúdo/infos adicionais/rodapé, utilizando grid, composta por duas colunas e três linhas (topo, main/aside, infos/rodape).

O grid é adicionado ao pai, que é o body, pois vai trabalhar com o posicionamento dos filhos.

```HTML
<header>Topo</header>
<main>Conteúdo</main>
<aside>Infos adicionais</aside>
<footer>Rodapé</footer>
```

```CSS
body {
  margin: 0;
  height: 100vh;

  display: grid;
}

header {
  background-color: green;
}

main {
  background-color: red;
}

aside {
  background-color: blue;
}

footer {
  background-color: gray;

}
```

Com a propriedade `grid-template-areas`, defino as áreas; cada uma dessas areas entre as aspas vai significar uma linha; e dentro delas eu defino as colunas.

```CSS
body {
  margin: 0;
  height: 100vh;

  display: grid;
  grid-template-areas:
    "header header"
    "main aside"
    "footer footer";
    /*coluna 1 - coluna 2*/
}
```

Depois de nomear as áreas no template, é hora de informar a `grid-area` nos estilos de cada tag HTML:

```CSS
body {
  margin: 0;
  height: 100vh;

  display: grid;
  grid-template-areas:
    "header header"
    "main aside"
    "footer footer";
}

header {
  grid-area: header;
  background-color: green;
}

main {
  grid-area: main;
  background-color: red;
}

aside {
  grid-area: aside;
  background-color: blue;
}

footer {
  grid-area: footer;
  background-color: gray;
}
```

Pra ficar ainda melhor, podemos definir o tamanho de cada uma das linhas utilizando a propriedade `grid-template-rows` no body.

A primeira linha quero que tenha 30px, mas a segunda quero que seja flexível, então posso escrever para que pegue uma fração (1fr), ou seja, a fração é uma ideia flexível que vai preencher tudo que estiver de espaço que estiver disponível e não foi definido. Já a última linha quero que tenha 40px.

Eu posso fazer o mesmo para as colunas, utilizando o `grid-template-columns`. Quero a primeira coluna flexível e a segunda fixa com 80px.

Sendo assim:

```CSS
body {
  margin: 0;
  height: 100vh;

  display: grid;
  grid-template-areas:
    "header header"
    "main aside"
    "footer footer";

  grid-template-rows:
    "30px 1fr 40px";

  grid-template-rows: "1fr 80px";
}

header {
  grid-area: header;
  background-color: green;
}

main {
  grid-area: main;
  background-color: red;
}

aside {
  grid-area: aside;
  background-color: blue;
}

footer {
  grid-area: footer;
  background-color: gray;
}
```

**_[Ver exemplo aqui](https://codepen.io/frontangie/pen/wveRgQq?editors=1100)_**

### Grid ou Flexbox

Podemos usar o Display Flex e Display Grid ao mesmo tempo.

```HTML
<body>
    <header>
        <div>Logo</div>
        <div>Menu</div>
    </header>
    <main>Conteúdo</main>
    <aside>Infos adicionais</aside>
    <footer>Rodapé</footer>
</body>
```

```CSS
body {
    margin: 0;
    height: 100vh;
    display: grid;
    grid-template-areas:
    "header header"
    "main aside"
    "footer footer";
    grid-template-rows: 30px 1fr 40px;
    grid-template-columns: 1fr 80px;
}

header {
    grid-area: header;
    background-color: green;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 8px;
}

main {
    grid-area: main;
    background-color: red;
}

aside {
    grid-area: aside;
    background-color: blue;
}

footer {
    grid-area: footer;
    background-color: gray;
}
```
