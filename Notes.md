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

É o empilhamento de elementos. Podemos usar o z-index para determinar a ordem da posição do elemento. Quanto maior o z-index, mais "acima" vai aparecer o elemento.

### Flex

**Flexbox**

- Nos permite posicionar os elementos dentro da caixa;
- Controle em uma dimensão (horizontal ou vertical);
- Alinhamento, direcionamento, ordenar e tamanhos.

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

```HTML
<div class="container">
  <div class="box blue"></div>
  <div class="box red"></div>
  <div class="box green"></div>
</div>
```

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

### Grid

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
