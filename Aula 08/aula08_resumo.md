# Aula 08 — Projeto React

Repositório de anotações da disciplina de **Frameworks Front-end**, contendo revisão de JavaScript moderno (ES6+) e fundamentos essenciais da biblioteca **React** (JSX, componentes funcionais, props, Virtual DOM, renderização de listas e renderização condicional).

**Professor:** Prof. Me. Deivison S. Takatu  
**Material de Apoio:** [Aula 08 - Projeto React.pdf](./Aula%2008%20-%20Projeto%20React.pdf)

---

## 📌 Conteúdos da Aula

- Revisão de JavaScript para Front-end:
  - Inserção de scripts e interação dinâmica
  - Variáveis e escopo (`var`, `let`, `const`)
  - Tipos de dados e operadores
  - Estruturas condicionais e de repetição
  - Funções tradicionais e Arrow Functions
  - Manipulação básica do DOM nativo
  - Métodos funcionais de Arrays (`forEach`, `filter`, `map`)
  - Objetos e métodos
- Fundamentos do React:
  - O que é DOM vs Virtual DOM e Reconciliação
  - Sintaxe JSX e expressões JavaScript
  - Criação e hierarquia de Componentes
  - Props (Propriedades) e fluxo unidirecional de dados
  - Renderização de coleções/listas e o papel da `key`
  - Estratégias de Renderização Condicional
- Atividade Prática

---

## 1. Revisão de JavaScript (ES6+)

Antes de dominar o React, é indispensável compreender os recursos modernos do ecossistema JavaScript:

### Inclusão no HTML
* **Tags `<script>`:** inseridas no final do `<body>` ou no `<head>` com `defer`;
* **Arquivos externos:** `<script src="app.js"></script>` para garantir código modular e manutenível.

### Escopo de Variáveis
* **`var`:** escopo de função ou global, suscetível a *hoisting* indesejado (evitar o uso moderno).
* **`let`:** escopo de bloco `{ }`, permite reatribuição de valor.
* **`const`:** escopo de bloco `{ }`, valor constante e imutável por reatribuição (recomendado como padrão).

### Tipos de Dados
* **Primitivos:** `string`, `number`, `boolean`, `undefined`, `null`, `symbol`, `bigint`.
* **Complexos:** `object`, `array`, `function`.
* **Operador `typeof`:** verifica dinamicamente o tipo de um valor em tempo de execução.

### Operadores de Comparação
* `==` e `!=` realizam coerção implícita de tipos (não recomendados).
* `===` e `!==` realizam **comparação estrita** (comparam valor e tipo simultaneamente).

### Funções e Arrow Functions
```javascript
// Função tradicional
function somar(a, b) {
    return a + b;
}

// Arrow function (sintaxe concisa padrão no React)
const somar = (a, b) => a + b;
```

### Métodos Modernos de Array
* **`forEach`:** itera sobre os elementos sem produzir retorno.
* **`filter`:** cria um novo array com os itens que satisfazem uma condição booleana.
* **`map`:** percorre a coleção e transforma cada item, retornando um novo array de mesmo tamanho (essencial no React para gerar elementos visuais).

---

## 2. O que é o DOM e o Virtual DOM?

### DOM Tradicional (Document Object Model)
O **DOM** é a representação estruturada em árvore de todos os nós HTML renderizados pelo navegador. Modificar o DOM nativo de forma direta (`document.querySelector`, `element.appendChild`) em aplicações ricas pode ser lento e difícil de sincronizar quando múltiplos estados mudam ao mesmo tempo.

### Virtual DOM do React
O **Virtual DOM** é uma representação leve da interface mantida em memória pelo React:
1. **Renderização:** quando o estado muda, o React gera uma nova árvore virtual em memória.
2. **Reconciliação (*Diffing*):** o React compara a nova árvore virtual com a versão anterior e calcula a menor quantidade necessária de alterações.
3. **Atualização Otimizada:** apenas as partes estritamente alteradas são sincronizadas no DOM real do navegador, proporcionando máxima performance e fluidez.

---

## 3. JSX (JavaScript XML)

O **JSX** é uma extensão de sintaxe que permite escrever código com aparência de HTML diretamente dentro do código JavaScript.

```jsx
const Titulo = () => {
    const usuario = "Maria";
    return <h1>Olá, {usuario}! Seja bem-vinda.</h1>;
};
```

### Principais Regras e Diferenças do JSX para o HTML:
* **Interpolação com Chaves `{ }`:** qualquer expressão JavaScript válida pode ser inserida entre chaves.
* **Atributos em CamelCase:**
  * Usa-se `className` no lugar de `class`;
  * Usa-se `htmlFor` no lugar de `for`.
* **Fechamento de Tags:** todas as tags sem filhos precisam ser auto-fechadas (ex: `<img />`, `<input />`, `<br />`).
* **Elemento Raiz Único:** o componente deve retornar um único elemento pai ou um Fragment (`<> ... </>`).

---

## 4. Componentes no React

Componentes são blocos de construção independentes, modulares e reutilizáveis da interface:

```jsx
// Declaração de componente funcional
function Cabecalho() {
    return (
        <header className="header">
            <h1>Portal de Cursos</h1>
        </header>
    );
}

// Utilização em outro componente
function App() {
    return (
        <main>
            <Cabecalho />
            <p>Conteúdo da aplicação.</p>
        </main>
    );
}
```

### Vantagens da Componentização:
* Divisão de telas complexas em partes menores e testáveis;
* Reutilização em múltiplas páginas do sistema;
* Organização hierárquica em árvore de componentes (`App -> Cabecalho, Lista, Rodape`).

---

## 5. Props (Propriedades)

**Props** são os argumentos ou dados de entrada passados de um componente pai para um componente filho, estabelecendo um **fluxo unidirecional de dados**.

```jsx
// Componente reutilizável recebendo props via desestruturação
function CardConceito({ titulo, descricao }) {
    return (
        <article className="card">
            <h2>{titulo}</h2>
            <p>{descricao}</p>
        </article>
    );
}

// Utilização com conteúdos diferentes mantendo o mesmo layout
function Catalogo() {
    return (
        <section>
            <CardConceito titulo="JSX" descricao="Sintaxe declarativa para interfaces." />
            <CardConceito titulo="Props" descricao="Dados transmitidos entre componentes." />
        </section>
    );
}
```

* Props podem transportar textos, números, booleanos, objetos, arrays e funções de callback.
* Props são **somente leitura** (*read-only*), garantindo previsibilidade.

---

## 6. Renderização de Listas e Keys

Para renderizar coleções de dados dinâmicas, utilizamos o método funcional `.map()` do JavaScript:

```jsx
const cursos = [
    { id: 1, nome: "React Fundamentos" },
    { id: 2, nome: "Next.js Avançado" },
    { id: 3, nome: "Tailwind CSS Moderno" }
];

function ListaCursos() {
    return (
        <ul>
            {cursos.map((curso) => (
                <li key={curso.id}>{curso.nome}</li>
            ))}
        </ul>
    );
}
```

### O papel crucial da propriedade `key`:
* A `key` é um identificador exclusivo utilizado pelo algoritmo de reconciliação do React;
* Permite que o React identifique quais itens foram alterados, adicionados ou excluídos sem recriar toda a lista no DOM;
* Deve-se priorizar IDs únicos estáveis em vez do índice do array.

---

## 7. Renderização Condicional

Permite alternar ou exibir trechos da interface com base no estado atual da aplicação:

### Abordagens Comuns:
1. **Operador Ternário (`condicao ? <A /> : <B />`):** ideal para alternar entre dois estados (ex: carregando vs conteúdo).
2. **Operador Lógico AND (`condicao && <Componente />`):** exibe o elemento apenas quando a condição for verdadeira.
3. **Cláusula Guarda com Early Return:** encerra a renderização antes do bloco principal caso os dados não existam.

```jsx
function MensagemAcesso({ autenticado, usuario }) {
    if (!autenticado) {
        return <p>Por favor, faça login para continuar.</p>;
    }

    return (
        <div>
            <h2>Bem-vindo de volta, {usuario}!</h2>
            {usuario === "admin" && <button>Painel de Controle</button>}
        </div>
    );
}
```

---

## ✅ Atividade Prática

1. Desenvolver uma aplicação React completa incorporando todos os tópicos fundamentais da aula:
   * Sintaxe JSX limpa e semântica;
   * Arquitetura componentizada em árvore hierárquica;
   * Transmissão e desestruturação de `props`;
   * Renderização de coleções utilizando `.map()` com propriedades `key` únicas;
   * Renderização condicional com ternários ou operador `&&`.
2. Publicar o projeto em um repositório público no GitHub.
3. Elaborar um `README.md` detalhado documentando a descrição do projeto, funcionalidades construídas, arquitetura de componentes e instruções de execução local.

---

## 📝 Resumo

```
JavaScript ES6+ → Virtual DOM & Reconciliação → JSX → Componentes → Props → Listas com Keys → Renderização Condicional
```

O React transforma o desenvolvimento front-end ao substituir manipulações imperativas e manuais do DOM por uma abordagem **declarativa**, baseada em componentes reutilizáveis e fluxo previsível de dados.

---

**Referências:**
* [Documentação Oficial do React](https://react.dev)
* [MDN Web Docs — JavaScript Guide](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
* Takatu, Deivison S. *Material de Apoio React*, SENAI.
* Repositórios de suporte: [aula-react](https://github.com/deivisontakatu/aula-react) e [projeto-react](https://github.com/deivisontakatu/projeto-react).
