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