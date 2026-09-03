# Aula 05 — Criando APIs para o Front-end

**Disciplina:** Frameworks Front-end  
**Foco:** Construção de APIs RESTful com Express.js, Protocolo HTTP, JSON, Deploy no Render, Integração com Front-end e Documentação no Postman.  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@edu.senai.br`)  

---

## 📌 Sumário

1. [Conceitos Fundamentais: API, HTTP e Web Services](#1-conceitos-fundamentais-api-http-e-web-services)
2. [Métodos HTTP](#2-métodos-http)
3. [Endpoints e Formato JSON](#3-endpoints-e-formato-json)
4. [Framework Express.js](#4-framework-expressjs)
5. [CORS e Segurança Básica](#5-cors-e-segurança-básica)
6. [Hospedagem de APIs no Render](#6-hospedagem-de-apis-no-render)
7. [Projeto Prático: API RESTful CRUD de Notas](#7-projeto-prático-api-restful-crud-de-notas)
8. [Questões para Reflexão (Arquitetura e Segurança)](#8-questões-para-reflexão-arquitetura-e-segurança)
9. [Documentação de APIs com Postman](#9-documentação-de-apis-com-postman)
10. [Atividades Práticas](#10-atividades-práticas)
11. [Resumo da Aula](#11-resumo-da-aula)
12. [Referências](#12-referências)

---

## 1. Conceitos Fundamentais: API, HTTP e Web Services

- **API (Application Programming Interface):** Conjunto de rotas, rotinas e padrões de programação fornecidos por uma aplicação para que outros softwares possam utilizar suas funcionalidades sem conhecer a implementação interna.
- **Servidor Backend:** Sistema responsável por processar requisições, aplicar regras de negócio, comunicar-se com bancos de dados e fornecer respostas para os clientes (web, mobile, etc.).
- **Web Service:** Serviço disponibilizado na web que possibilita a comunicação entre sistemas heterogêneos (desenvolvidos em diferentes linguagens e plataformas) através dos protocolos HTTP/HTTPS.

---

## 2. Métodos HTTP

Os métodos (ou verbos) HTTP definem a ação a ser executada no servidor sobre um recurso específico:

| Método | Finalidade | Características |
|---|---|---|
| **GET** | Recuperar informações do servidor | **Seguro** (não altera dados) e **Idempotente** (múltiplas chamadas idênticas geram o mesmo resultado). |
| **POST** | Criar novos recursos no servidor | **Não Idempotente** (chamadas repetidas criam múltiplos registros). |
| **PUT** | Substituir/Atualizar **completamente** um recurso | **Idempotente** (substitui o registro com os novos dados). |
| **PATCH** | Atualizar **parcialmente** um recurso | Usado para modificar apenas campos específicos. |
| **DELETE** | Remover um recurso específico | **Idempotente** (apagar um recurso que já foi removido não gera efeito colateral). |

---

## 3. Endpoints e Formato JSON

### Endpoint
Um **endpoint** é a URL específica através da qual o cliente acessa um recurso ou funcionalidade exposta pela API.
- *Exemplo de base URL:* `https://api.exemplo.com`
- *Exemplo de recurso:* `GET /api/notes` (Lista notas) ou `POST /api/notes` (Cria uma nota).

### JSON (JavaScript Object Notation)
Formato leve, textual e independente de linguagem usado para troca de dados entre cliente e servidor.
- **Estruturas básicas:**
  - Objetos: Pares `chave: valor` envoltos por `{}`.
  - Arrays: Listas ordenadas de valores envoltas por `[]`.

```json
[
  {
    "id": "1",
    "titulo": "Lembretes",
    "texto": "Comprar leite e pão",
    "criadoEm": "2026-04-28T10:00:00Z"
  }
]
```

---

## 4. Framework Express.js

O **Express.js** é um framework minimalista e flexível para Node.js que simplifica significativamente o desenvolvimento de servidores web e APIs RESTful.

### Comparativo: Node.js Puro vs. Express.js

- **Node.js Puro (`http` module):** Exige tratar manualmente a leitura de URL, verbos HTTP, cabeçalhos, parsing de corpo de requisição e roteamento complexo.
- **Express.js:** Fornece um sistema intuitivo de roteamento (`app.get()`, `app.post()`), suporte nativo a *middlewares* e facilidade para retornar respostas JSON (`res.json()`).

### Quando utilizar o Express.js?
- **Recomendado:** APIs REST/RESTful, backends para SPAs (React, Vue, Angular), microsserviços, prototipagem rápida e aplicações web tradicionais.
- **Evitar:** Aplicações pesadas em tempo real com conexões persistentes (onde WebSockets / Socket.io são mais adequados) ou tarefas intensivas de processamento de CPU (onde Worker Threads ou outras linguagens são melhores).

---

## 5. CORS e Segurança Básica

### O que é CORS?
**CORS (Cross-Origin Resource Sharing)** é um mecanismo de segurança implementado pelos navegadores que bloqueia requisições HTTP feitas a domínios diferentes daquele que originou a página.

### Liberando CORS no Express
Para permitir que uma aplicação Front-end (ex: rodando na Vercel ou `localhost:5173`) consuma a API, utiliza-se um middleware de cabeçalhos:

```javascript
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
  res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');
  next();
});
```

---

## 6. Hospedagem de APIs no Render

O **Render** (`render.com`) é uma plataforma em nuvem moderna para hospedagem de aplicações backend, bancos de dados e Web Services.

### Vantagens do Render:
- Deploy automático integrado ao GitHub/GitLab.
- SSL/HTTPS gratuito automático.
- Plano gratuito ideal para projetos acadêmicos.

### Passo a passo para Deploy no Render:
1. Suba o código da sua API para um repositório no GitHub.
2. Acesse `dashboard.render.com` e crie um **New Web Service**.
3. Conecte o repositório do GitHub.
4. Defina as configurações:
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js` (ou `node api.js`)
5. Clique em **Create Web Service**. Ao finalizar, a API estará acessível em uma URL pública `.onrender.com`.

---

## 7. Projeto Prático: API RESTful CRUD de Notas

Aplicação desenvolvida em Node.js com Express para realizar operações completas de **CRUD** (Create, Read, Update, Delete) utilizando um arquivo `data.json` para persistência simples.

### Estrutura de Arquivos
```text
projeto-notas/
├── package.json
├── data.json
└── server.js
```

### Instalação das Dependências
```bash
npm init -y
npm install express body-parser
```

### Código Completo (`server.js`)

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const fs = require('fs');

const app = express();
const PORT = 3000;
const FILE = 'data.json';

// Middleware para parsing de JSON
app.use(bodyParser.json());

// Middleware para CORS
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');
  res.header('Access-Control-Allow-Headers', 'Content-Type');
  next();
});

// Função auxiliar: Ler arquivo JSON
function readNotes() {
  try {
    const data = fs.readFileSync(FILE, 'utf-8');
    return JSON.parse(data);
  } catch (err) {
    return [];
  }
}

// Função auxiliar: Salvar no arquivo JSON
function saveNotes(notes) {
  fs.writeFileSync(FILE, JSON.stringify(notes, null, 2));
}

// 1. GET /api/notes - Listar todas as notas
app.get('/api/notes', (req, res) => {
  const notes = readNotes();
  res.json(notes);
});

// 2. GET /api/notes/:id - Obter uma nota por ID
app.get('/api/notes/:id', (req, res) => {
  const notes = readNotes();
  const note = notes.find(n => n.id === req.params.id);
  if (note) {
    res.json(note);
  } else {
    res.status(404).json({ erro: 'Nota não encontrada' });
  }
});

// 3. POST /api/notes - Criar uma nova nota
app.post('/api/notes', (req, res) => {
  const notes = readNotes();
  const novaNota = {
    id: Date.now().toString(),
    titulo: req.body.titulo,
    texto: req.body.texto,
    criadoEm: new Date().toISOString()
  };
  notes.push(novaNota);
  saveNotes(notes);
  res.status(201).json(novaNota);
});

// 4. PUT /api/notes/:id - Editar uma nota existente
app.put('/api/notes/:id', (req, res) => {
  const notes = readNotes();
  const index = notes.findIndex(n => n.id === req.params.id);
  if (index >= 0) {
    notes[index].titulo = req.body.titulo;
    notes[index].texto = req.body.texto;
    saveNotes(notes);
    res.json(notes[index]);
  } else {
    res.status(404).json({ erro: 'Nota não encontrada' });
  }
});

// 5. DELETE /api/notes/:id - Excluir uma nota por ID
app.delete('/api/notes/:id', (req, res) => {
  const notes = readNotes();
  const novasNotas = notes.filter(n => n.id !== req.params.id);
  if (notes.length !== novasNotas.length) {
    saveNotes(novasNotas);
    res.json({ mensagem: 'Nota removida com sucesso' });
  } else {
    res.status(404).json({ erro: 'Nota não encontrada' });
  }
});

// Inicialização do Servidor
app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});
```

---

## 8. Questões para Reflexão (Arquitetura e Segurança)

1. **Riscos de Segurança:**
   - **CORS Liberado (`*`):** Permite que qualquer site faça requisições à API.
   - **Ausência de Autenticação/Autorização:** Qualquer usuário pode listar, alterar ou deletar notas de qualquer pessoa.
   - **Falta de Sanitização e Validação:** Sem tratamento dos inputs (`titulo`, `texto`), a API está suscetível a envios maliciosos ou payload corrompido.

2. **Uso de Arquivo JSON em Produção:**
   - **Vantagens:** Simplicidade de configuração, zero custo de banco de dados, fácil visualização para testes.
   - **Desvantagens:** Ausência de concorrência segura (operações simultâneas de escrita corrompem o arquivo), falta de índices para busca rápida e ausência de suporte a transações ACID.

3. **Limitações com Grandes Volumes (ex: 10.000+ registros):**
   - Ler e sobrescrever todo o arquivo `data.json` em disco a cada requisição gera **estouro de memória (RAM)** e **bloqueio de I/O**, tornando o servidor extremamente lento.
   - *Solução:* Substituir o arquivo por um Banco de Dados relacional (PostgreSQL, MySQL) ou NoSQL (MongoDB).

4. **Organização do Código:**
   - Colocar todas as rotas e regras no `server.js` gera um "código espaguete" difícil de manter.
   - *Solução:* Adotar uma arquitetura em camadas (MVC), dividindo em rotas (`routes/`), controladores (`controllers/`), serviços (`services/`) e modelos (`models/`).

---

## 9. Documentação de APIs com Postman

O **Postman** é a ferramenta padrão de mercado para testar, organizar, automatizar e documentar requisições HTTP.

### Recursos Principais:
- **Coleções (Collections):** Agrupamento de endpoints organizados por módulos.
- **Variáveis de Ambiente:** Permitem alternar facilmente entre `http://localhost:3000` e a URL de produção no Render.
- **Documentação Automática:** Gera documentação web interativa com exemplos de requisição e resposta.
- **Newman CLI:** Executa coleções do Postman em pipelines de Integração Contínua (CI/CD).

---

## 10. Atividades Práticas

### 📌 Atividade 01
- Criar um servidor básico com Express.js.
- Subir o projeto no GitHub e fazer o deploy no Render.
- Enviar o link do repositório no formulário fornecido.

### 📌 Atividade 02 (CRUD Completo de Notas)
1. **Back-end:** Construir a API RESTful de notas com suporte a CRUD completo e publicar no Render.
2. **Front-end:** Criar uma aplicação React que consuma a API do Render (substituindo o endpoint local pela URL do Render) e publicar na Vercel.
3. **Postman:** Criar uma coleção no Postman documentando as 4 operações (GET, POST, PUT, DELETE) com exemplos de respostas.
4. **Relatório:** Entregar um documento contendo prints do código, aplicação em funcionamento, link do GitHub, link do Vercel e link da coleção do Postman.

---

## 11. Resumo da Aula

```text
API RESTful → Métodos HTTP (GET/POST/PUT/DELETE) → Express.js → Persistence (JSON) → Deploy (Render) → Postman
```

Nesta aula aprendemos a transicionar do papel de apenas *consumidores* de APIs no Front-end para o de *criadores* de APIs no Back-end com Node.js e Express, cobrindo o fluxo completo do desenvolvimento até o deploy na nuvem e documentação.

---

## 12. Referências

- **Exemplo de Código da Aula (Backend):** [github.com/deivisontakatu/exemplo-api-backend](https://github.com/deivisontakatu/exemplo-api-backend)
- **Exemplo de Código da Aula (Frontend):** [github.com/deivisontakatu/exemplo-api-frontend](https://github.com/deivisontakatu/exemplo-api-frontend)
- SOUZA, Natan. *Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.* São Paulo: Casa do Código, 2018.
- MACHADO, Kheronn Khennedy. *Angular 11 e Firebase: construindo uma aplicação integrada.* São Paulo: Casa do Código, 2021.
- EIS, Diego. *Guia Front-end: o caminho das pedras para ser um dev front-end.* São Paulo: Casa do Código, 2015.
- NIEDERAUER, Juliano. *Desenvolvendo Websites com PHP.* 3. ed. São Paulo: Novatec, 2017.

---
**Material de Apoio:** Disciplina de Frameworks Front-end — Prof. Me. Deivison S. Takatu (SENAI).
