## Insight´s

1. 
- A ordem do codigo importa um ex..: 
// ❌ ERRADO
adicionarBolinhoNaTabelaDeServida(); // (Nada acontece!)
misturaIngredientes();
assarBolo();

// ✅ CERTO
misturaIngredientes();
assarBolo();
adicionarBolinhoNaTabelaDeServida(); // Agora o bolo existe!

- Por isso o codigo segue uma logica 
DADOS (array) → LÓGICA → INTERFACE (UI)

employees.push()  →  updateDashboard()  →  Usuário vê atualizado

A ordem é sempre:

1. Validar entrada
2. Modificar estado (push)
3. Atualizar interface (funções que modificam o DOM)
4. Limpar formulário

2. carregamento inicial da pagina 

- em algumas paginas é necessario que uma pagina carregue o js antes das informações existirem exemplo..:

const employees = [];

function updateDashboard() {
    const stats = calculateStats();
    statsContainer.innerHTML = `...cartões com ${stats.total}...`;
}

// ❌ SEM ISSO: Página abre com stats-container vazio
// ✅ COM ISSO: Página abre com stats-container mostrando 0 funcionários

updateDashboard();  // Renderiza na primeira carga

<!-- neste exemplo o container states esta 100% vazio pois não há informações dentro do array 
e por não haverem informações logo o container ainda não existe e somente após um funcionario ser adicionado o container passa a existir por isso é necessario que ele carregue antes  -->


<!-- != / quer dizer diferente 
5 != 2
true 

agora 

5 !== "5"
true / por que o !== compara o tipo + o valor  -->

<!-- neste case 
let nome = "saulo"



console.log(!nome) 

o ! transforma verdade em falso e falso em verdade 

então sem ! a pergunta fica nome tem valor? mas com ! a pergunta fica nome Não tem valor?


existem algumas situações que são consideradas falsy que no caso viram true
false
0
-0
0n       // BigInt zero
""       // String vazia
null
undefined
NaN -->


<!-- Callback 


Um **callback** é uma **função que é passada para outra função para ser executada posteriormente**.

Ou seja:

* ❌ Não é uma função que chama outra função.
* ✅ É uma função que **é chamada por outra função**.

### Exemplo simples

```javascript
function saudacao() {
    console.log("Olá!");
}

function executar(callback) {
    callback();
}

executar(saudacao);
```

O que acontece?

1. Criamos a função `saudacao`.
2. Criamos a função `executar`, que recebe um parâmetro chamado `callback`.
3. Dentro de `executar`, fazemos:

```javascript
callback();
```

Quem chamou `saudacao`?

➡️ Foi a função `executar`.

Nesse caso:

* `executar` = função principal
* `saudacao` = callback

---

## Outro exemplo (bem comum)

```javascript
const numeros = [1, 2, 3];

numeros.forEach(function(numero) {
    console.log(numero);
});
```

Aqui acontece algo parecido:

```javascript
forEach(callback)
```

A função anônima

```javascript
function(numero) {
    console.log(numero);
}
```

é o callback.

O `forEach` vai chamá-la uma vez para cada elemento do array.

---

## Exemplo com `addEventListener`

```javascript
const botao = document.getElementById("btn");

botao.addEventListener("click", function () {
    console.log("Botão clicado!");
});
```

A função

```javascript
function () {
    console.log("Botão clicado!");
}
```

é um callback.

Você **não a executa diretamente**. Quem faz isso é o `addEventListener` quando o evento `"click"` acontece.

---

## Uma analogia

Imagine que você diz para um amigo:

> "Quando a pizza chegar, **me liga**."

A frase "**me liga**" é o callback.

Você não está ligando naquele momento. Você apenas entregou uma instrução para ser executada depois, quando um determinado evento acontecer.

---

## Resumindo

Um callback é uma função que:

* é passada como argumento para outra função;
* fica "guardada";
* será executada quando a função que a recebeu decidir.

Exemplo clássico:

```javascript
function dizerOi() {
    console.log("Oi");
}

function executar(callback) {
    callback();
}

executar(dizerOi);
```

Aqui:

* `dizerOi` → callback.
* `executar` → função que recebe e executa o callback.

> Uma observação importante: o nome `callback` é apenas uma convenção. Você poderia escrever:

```javascript
function executar(minhaFuncao) {
    minhaFuncao();
}
```

botao = {
    addEventListener: function(evento, callback) {
        // código interno...
    }
} 

e continuaria sendo um callback. O que define um callback não é o nome do parâmetro, mas o fato de uma função ser passada para outra para ser executada posteriormente.
-->