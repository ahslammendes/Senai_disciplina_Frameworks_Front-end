# Aula 04 — Consumindo APIs no Front-end

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@edu.senai.br`)  

---

## 📌 Sumário

1. [API (Application Programming Interface)](#1-api-application-programming-interface)
2. [Arquitetura REST](#2-arquitetura-rest)
3. [Protocolo HTTP](#3-protocolo-http)
4. [Métodos HTTP](#4-métodos-http)
5. [Como Funciona uma Requisição na Prática](#5-como-funciona-uma-requisição-na-prática)
6. [Endpoints e Formato JSON](#6-endpoints-e-formato-json)
7. [Catálogo de APIs Públicas](#7-catálogo-de-apis-públicas)
8. [Servidor Backend e Web Service](#8-servidor-backend-e-web-service)
9. [Criando e Hospedando Web Services no Render](#9-criando-e-hospedando-web-services-no-render)
10. [Atividades Práticas](#10-atividades-práticas)

---

## 1. API (Application Programming Interface)

Uma **Interface de Programação de Aplicações** é um conjunto de protocolos, rotinas, regras e ferramentas para construção de software. Ela estabelece contratos que definem como diferentes componentes e sistemas heterogêneos devem interagir e trocar informações sem que um precise conhecer a implementação interna do outro.

---

## 2. Arquitetura REST

**REST (Representational State Transfer)** é um estilo arquitetural para o desenvolvimento de sistemas distribuídos na web. Seus princípios fundamentais incluem:
* **Comunicação Cliente-Servidor sem estado (*stateless*):** cada requisição carrega todas as informações necessárias para ser processada; o servidor não armazena estado de sessão do cliente.
* **Uso padronizado dos métodos HTTP:** operações são mapeadas diretamente nos verbos padrão da web.
* **Recursos identificados por URIs:** cada entidade acessível possui um endereço próprio e explícito.
* **Representação de dados padronizada:** trafegada predominantemente em JSON.

---

## 3. Protocolo HTTP

O **HTTP (Hypertext Transfer Protocol)** é a espinha dorsal de comunicação da World Wide Web.
* **Modelo Cliente-Servidor:** o cliente (navegador/aplicação front-end) emite requisições e o servidor processa e retorna respostas.
* **Stateless:** cada ciclo requisição-resposta é independente.
* **Baseado em texto:** mensagens legíveis e padronizadas.

---

## 4. Métodos HTTP

| Método | Finalidade | Características |
|---|---|---|
| **GET** | Recuperar informações do servidor | Seguro (não modifica dados no backend) e idempotente. |
| **POST** | Criar um novo recurso no servidor | Não idempotente (múltiplas chamadas geram novos registros). |
| **PUT** | Substituir completamente um recurso existente | Idempotente (recoloca o registro no estado informado). |
| **PATCH** | Atualizar dados parciais de um recurso | Altera apenas propriedades específicas. |
| **DELETE** | Remover um recurso específico | Idempotente (remover um recurso inexistente ou já apagado produz o mesmo resultado final). |

---

## 5. Como Funciona uma Requisição na Prática

1. **Front-end / Usuário:** o usuário interage com a tela ou clica em uma ação.
2. **Requisição HTTP:** a aplicação dispara uma chamada (`GET`, `POST`, `PUT`, `DELETE`).
3. **Servidor Backend (ex: Express.js):** intercepta a requisição, roteia para o controlador adequado e executa as regras de negócio.
4. **Banco de Dados ou API Externa:** o backend consulta ou persiste dados.
5. **Resposta JSON:** o servidor serializa a resposta em formato JSON com o código de status HTTP adequado.
6. **Atualização da Interface:** o front-end recebe os dados e atualiza o estado/componentes na tela.

---

## 6. Endpoints e Formato JSON

* **Endpoint:** URL específica que mapeia o acesso a um recurso da aplicação (ex: `https://api.exemplo.com/usuarios`).
* **JSON (JavaScript Object Notation):** Formato leve e universal de intercâmbio de dados, estruturado em objetos (chave/valor) e coleções de arrays, simples de interpretar tanto por humanos quanto por código.

---

## 7. Catálogo de APIs Públicas

Repositórios públicos como [Free Public APIs](https://www.freepublicapis.com/) e a [AwesomeAPI Brasil](https://github.com/awesomeapibrasil/awesomeapi-cep) são recursos valiosos para simular consumo de dados reais no front-end (previsão do tempo, cotação de moedas, consulta de CEPs, etc.).

---

## 8. Servidor Backend e Web Service

* **Servidor Backend:** gerencia lógica de negócio, persistência em bancos de dados e regras de segurança.
* **Web Service:** serviço acessível via web através de HTTP/HTTPS que padroniza a troca de informações entre sistemas que utilizam diferentes linguagens ou tecnologias.

---

## 9. Criando e Hospedando Web Services no Render

O **Render** é uma plataforma moderna de computação em nuvem que permite hospedar aplicações Node.js diretamente conectadas ao repositório GitHub com deploy contínuo (CI/CD):
1. Criação do servidor mínimo em Express (`api.js`) com tratamento de porta dinâmica: `const PORT = process.env.PORT || 3000;`.
2. Habilitação de **CORS** (`app.use(cors())`) para viabilizar o consumo por navegadores em domínios distintos.
3. Criação de Web Service no Render conectado ao repositório GitHub.
4. Configuração dos comandos: Build (`npm install` ou `node`) e Start (`node api.js`).
5. Disponibilização pública da URL HTTPS com certificado SSL incluso gratuitamente.

---

## 10. Atividades Práticas

* **Atividade 01:** Pesquisa e análise de 10 projetos no GitHub que consomem APIs externas, documentando framework utilizado, rotas e arquitetura em uma tabela Markdown.
* **Atividade 02:** Construção de uma API com Express que devolve data e hora atual, publicação no Render, e desenvolvimento de uma aplicação front-end que consome esse endpoint e exibe os dados para o usuário final, documentando o processo completo.
