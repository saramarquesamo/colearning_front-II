# Colearning Front II

## 1. Sintaxe da linguagem Javascript

### 1.1. Variáveis

```js
// Valor dinâmico.
var valor1 = 0;
let valor2 = 1;

// Valor imutável.
const valor3 = 2;
```

**Nota:** Existem algumas diferencas sutis, porém poderosa, de variaveis declaradas com `var` e `let` no Javascript. Quando declaradas com `var`, o seu contexto nem sempre irá proteger o acesso a variável, também e possível redeclará-las.

```js
// Representa um escopo.
{
    // Variável declarada com valor inicial 0.
    var valor1 = 0;
}
// Conseguimos acessar o valor, mesmo que fora do escopo.
console.log(valor1); // 0
// Também conseguimos redeclarar a variavel.
var valor1 = "";
```

Para resolução deste problema, declara-se a variavel com `let`.

### 1.2. Tipos de valores 

```js
true; // boolean 
10; // number
""; // string
[]; // array
{}; // object
function(){}; // object
```

### 1.3. Operadores

#### 1.3.1. Operadores aritmetricos

```js
+ // Somar.
- // Subtrair.
* // Multiplicar.
/ // Dividir.
% // Resto da divisao.
** // Potenciacao.
```

#### 1.3.2. Operadores de atribuicao

```js
= // Atribuicao.
+= // Somar e atribui o resultado.
-= // Subtrair e atribui o resultado.
*= // Multiplicar e atribui o resultado.
/= // Dividir e atribui o resultado.
```

#### 1.3.3. Operadores logicas

```js
< // Menor que...
> // Maior que...
<= // Menor ou igual a...
>= // Maior ou igual a...
== // Igual a...
=== // Identico a...
!= // Diferente de...
!== // Completamene diferente de...
```

#### 1.3.4. Operador ternario

### 1.4. Condicionais

#### 1.4.1. If...Else...

```js
if(5 < 6) {
    console.log("Valor é menor.");
}
else {
    console.log("Valor é maior.");
}
```

#### 1.4.2. If...Else If...Else...

```js
if(5 > 6) {
    console.log("Valor é maior.");
}
else if(typeof(5) == "number") {
    console.log("Valor é um número.");
}
else {
    console.log("Valor não é um valor válido.");
}
```

#### 1.4.3. Switch...Case...Default
```js
let Tipo = typeof(5);

switch(Tipo) {
    
    case "function":
        console.log("É uma função.");
    break;

    case "string":
        console.log("É um texto.");
    break;

    case "number":
        console.log("É um número.");
    break;

    default:
        console.log("Não é um valor reconhecido.");
    break;
}
```

### 1.5. Listas

#### 1.5.1. Sintaxe de declaracao
```js
// Tipos de valores suportados...
let Lista = [0, "Oi", true, {}, []];
```

### 1.6. Objetos

#### 1.6.1. Sintaxe de declaracao

```js
let Perfil = {
    nome: "Willian",
    sobrenome: "Sant Anna",
    nomeCompleto: function() {
        return `${nome} ${sobrenome}`;
    }
}

console.log(Perfil.nome); // Willian
console.log(Perfil.sobrenome); // Sant Anna
console.log(Perfil.nomeCompleto()); // Willian Sant Anna
```

### 1.7. Estruturas de repeticao

#### 1.7.1. for...

```js
for(let contador = 0; contador < 5; contador++) {
    console.log(`Estamos na repetição de número ${contador}.`);
}
```

#### 1.7.2. while...

```js

function retornarFalsoDepoisDeCincoSegundos() {
    return setTimeOut(() => false, 5000);
}

while(retornarFalsoDepoisDeCincoSegundos) {
    console.log("Estamos repetindo...");
}
```

#### 1.7.3. do...while...

```js
do {
    console.log("Intrução que deverá ser repetida.");
} while(false);
```

#### 1.7.4. foreach...

```js
let Numeros = [5, 10, 15, 20, 25];

Numeros.forEach(Numero => Numero / 5);
```

### 1.8. Funções

#### 1.8.1. function nomeDaFuncao() { }

```js
function Falar(Mensagem) {
    return Mensagem;
}

Falar('Ola');
```

#### 1.8.2. let variavel = function() { }

```js
let Falar = function(Mensagem) {
    return Mensagem;
}

Falar('Ola');
```

#### 1.8.3. Arrow funcion

```js
let Falar = Mensagem => Mensagem;

Falar('Ola');
```

## 2. Manipular o DOM

Para desenvolvimento de uma **aplicação reativa**, basicamente serão necessárias três características fundamentais:

1. Seleção do(s) elemento(s).
2. Criação e manipulação de elemento(s).
3. Criação e manipulação de atributo(s).

### 2.1. Seleção do(s) elemento(s) 

```js
var coordenadaLinhaUmColunaTres = document.querySelector(".coordenada#linha-1_coluna-3");
```

### 2.2. Criação e manipulação de elemento(s)

```js
coordenadaLinhaUmColunaTres.innerHTML = "<span>X<span>";
// ou 
let coordenadaLinhaUmColunaUm = document.createElement("span");
var coordenadaLinhaUmColunaUmTexto = document.createTextNode("O");
coordenadaLinhaUmColunaUm.appendChild(coordenadaLinhaUmColunaUmTexto);
document.body.appendChild(coordenadaLinhaUmColunaUm);
```

### 2.3. Criação e manipulação de atributo(s)

```js
// Estilos
coordenadaLinhaUmColunaTres.style.backgroundColor = "orangered";
coordenadaLinhaUmColunaTres.style.color = "orange";
// Classes
coordenadaLinhaDoisColunaTres.classList.add('selecionado');
// Adicionar atributo
coordenadaLinhaDoisColunaTres.setAttribute("alt", "Descrição");
```

**Nota:** Você pode verificar se uma elemento possui ou não uma determinada classe. 

```js
let possuiClasseSelecionado = coordenadaLinhaDoisColunaTres.classList.contains("selecionado");
console.log("Possui a classe 'selecionado'?", possuiClasseSelecionado);
```

### 2.4. Capturando eventos

```js
let documento = document.body;

// 1. Criar o elemento que desejos adicionar aoAcnoss DOM
let botao = document.createElement("button");

// 2. Criamos o texto que iremos adicionar ao elemento
let botaoTexto = document.createTextNode("Abrir alerta");

// 3. Adicionamos o texto ao elemento como um nó de texto
botao.appendChild(botaoTexto);

// 4. Adicionamos o elemento que contém um nó de texto no DOM
documento.appendChild(botao);

// 5. Adicionamos atributo(s) e valores ao elemento
// Neste exemplo adicionaremos uma url de destino
//botao.setAttribute("href", "https://www.google.com");

// 6. Podemos aproveitar e adicionar uma classe para estilizar o elemento
botao.classList.add("botao");

// Observações:

// -> documento.innerHTML = "<h1>Manipulando o DOM</h1>";

// 7. Define qual tarefa você deseja realizar

// Funções = Rotina
function criarUmAlerta() {
    alert("Você clicou aqui...");
}

let criarUmAlerta = function() {
    alert("Você clicou aqui...");
}

// Método = Acionar/Chamar
// criarUmAlerta();

// 8. Capturar um evento específico do elemento e executa a tarefa
botao.addEventListener("click", criarUmAlerta);

// ----

let botaoRedirecionarPara = document.querySelector("#enviarPara");

// Função anônima
botaoRedirecionarPara.addEventListener("click", function() {
    window.location.replace("https://www.google.com.br");
});

// Função anônima + arrow function
botaoRedirecionarPara.addEventListener("click", () => window.location.replace("https://www.google.com.br"));
```

## Requisicoes HTTP

## Tratar excessoes/erros

## Callback

Em Javascript, um dos principais recursos utilizados para o reaproveitamento de codigo, e o Callback. Com esse recursos, e possivel definir uma funcao e tercerizar um trecho de sua responsabilidade a partir de um parametro, possibilitando que a funcao seja reutilizada de muitas formas. Ficou confuso?! Vamos deixar esse assunto um pouco mais claro.

Imagine que precisaremos calcular tres operacoes matematicas, sendo elas: **Somar**, **Subtrair** e **Multiplicar**. Essas funcoes deverao receber uma lista de valores e realizar a operacao matematica em sequencia conforme o codigo-fonte a seguir:

```js
function CalcularSoma(Valores) {

    ValorTotal = 0;
    
    Valores.map((Valor, Indice) => {
        
        let PrimeiroIndice = Indice == 0;

        if(PrimeiroIndice) {
            ValorTotal = Valor;
        } 
        else {
            // Calcula a Soma dos valores.
            ResultadoDaOperacaoSoma = ValorTotal + Valor;
            // Atualizo o valor inicial.
            ValorTotal = ResultadoDaOperacaoSoma;
        }
    });

    return ValorTotal;
}

function CalcularSubtracao(Valores) {

    ValorTotal = 0;
    
    Valores.map((Valor, Indice) => {
        
        let PrimeiroIndice = Indice == 0;

        if(PrimeiroIndice) {
            ValorTotal = Valor;
        } 
        else {
            // Calcula a Subtracao dos valores.
            ResultadoDaOperacaoSoma = ValorTotal - Valor;
            // Atualizo o valor inicial.
            ValorTotal = ResultadoDaOperacaoSoma;
        }
    });

    return ValorTotal;
}

function CalcularMultiplicacao(Valores) {

    ValorTotal = 0;
    
    Valores.map((Valor, Indice) => {
        
        let PrimeiroIndice = Indice == 0;

        if(PrimeiroIndice) {
            ValorTotal = Valor;
        } 
        else {
            // Calcula a Multiplicacao dos valores.
            ResultadoDaOperacaoSoma = ValorTotal * Valor;
            // Atualizo o valor inicial.
            ValorTotal = ResultadoDaOperacaoSoma;
        }
    });

    return ValorTotal;
}

console.log( CalcularSoma([1,2,3]) ); // 6
console.log( CalcularSubtracao([1,2,3]) ); // -4
console.log( CalcularMultiplicacao([1,2,3]) ); // 6
```

Observe que todas as funcoes implementadas precisaram: 

- Utilizar uma estrutura de repeticao para acessar cada valor da lista.
- Calcular sua respectiva operacao matematica.
- Atualizar o valor total. 
- Apos calcular todos os valores da lista, retornar o valor total.

Sendo assim, temos uma clara necessidade de repetir o codigo. 
Observe como podemos resolver este problema utilizando **Callback**:

```js
/* 
    Calcular fica responsavel por:
    - Utilizar uma estrutura de repeticao para acessar cada valor da lista.
    - Atualizar o valor total. 
    - Apos calcular todos os valores da lista, retornar o valor total.
    
    E o callback fica responsavel por:
    - Calcular sua respectiva operacao matematica.
    - Retornar o resultado da operacao matematica.
*/
function Calcular(Valores, OperacaoMatematica) {

    ValorTotal = 0;
    
    Valores.map((Valor, Indice) => {
        
        let PrimeiroIndice = Indice == 0;

        if(PrimeiroIndice) {
            ValorTotal = Valor;
        } 
        else {
            // Calcula a Operacao Matematica nos valores.
            ResultadoDaOperacaoMatematica = OperacaoMatematica(ValorTotal, Valor)
            // Atualizo o valor inicial.
            ValorTotal = ResultadoDaOperacaoMatematica;
        }
    });

    return ValorTotal;
}

// Declarei os Callbacks para cada Operacao Matematica.
let Somar = (ValorInicial, Valor) => ValorInicial + Valor;
let Subtrair = (ValorInicial, Valor) => ValorInicial - Valor;
let Multiplicar = (ValorInicial, Valor) => ValorInicial * Valor;

// Note que a funcao Calcular recebe apenas o nome dos Callbacks.
console.log( Calcular([1,2,3], Somar) ); // 6
console.log( Calcular([1,2,3], Subtrair) ); // -4
console.log( Calcular([1,2,3], Multiplicar) ); // 6
```