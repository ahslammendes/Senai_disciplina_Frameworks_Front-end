# Aula 03 — Projetos com Frameworks Front-end

**Disciplina:** Frameworks Front-end
**Foco:** Comparação entre frameworks, criação de projetos com React, Angular, Vue e Next.js, e importação de projetos prontos.
**Professor:** Prof. Me. Deivison S. Takatu

---

## 📌 Sumário

- Introdução aos Frameworks Front-end
- Framework × Biblioteca
- React, Vue, Angular e Next.js
- Comparação entre Frameworks
- Criação e estrutura de projetos
- Git e versionamento
- Atividade prática

---

## 1. Introdução aos Frameworks Front-end

Um framework front-end é um conjunto de ferramentas, bibliotecas e convenções que padronizam o desenvolvimento de interfaces web, fornecendo uma estrutura pré-definida que acelera a criação de aplicações complexas.

**Sem framework (Vanilla JS):** código manual, difícil manutenção, repetição.
**Com framework:** componentes reutilizáveis, estado gerenciado, atualizações eficientes.

---

## 2. Framework x Biblioteca

| Framework | Biblioteca |
|---|---|
| Controla o fluxo (inversão de controle) | Você controla quando chamar |
| Exige estrutura definida | Flexível, sem imposições |
| Exemplos: Angular, Vue | Exemplos: React, jQuery |

**Exemplo prático:**
- **Biblioteca:** você chama `ReactDOM.render()` quando quiser.
- **Framework:** o Angular decide quando renderizar os componentes.

---

## 3. Por que Utilizar um Framework?

- **Produtividade aumentada** — soluções prontas para roteamento, estado e renderização
- **Melhores práticas** — código organizado em componentes
- **Manutenção facilitada** — Virtual DOM (React), Change Detection (Angular)
- **Comunidade e suporte** — documentação extensa, plugins e soluções para problemas comuns

---

## 4. Exemplos de Frameworks

- **React** — criado pelo Facebook em 2013; tecnicamente é uma **biblioteca**, não um framework, mas é amplamente chamada assim
- **Angular** — desenvolvido pelo Google; framework completo para SPAs
- **Vue.js** — framework progressivo, fácil de adaptar conforme a aplicação cresce

> Fonte de popularidade: [Google Trends](https://trends.google.com.br/)

---

## 5. Características dos Frameworks Front-end

- **Estrutura de código organizada** — separação clara entre HTML, CSS e JS
- **Componentização** — componentes independentes e reutilizáveis
- **Programação reativa** — UI atualizada automaticamente com mudanças de estado
- **Ferramentas de build e bundling** — minificação, transpilação e compatibilidade
- **Sistema de rotas** — SPAs com navegação suave, sem recarregar a página
- **Integração com APIs** — chamadas assíncronas e sincronização de dados
- **Documentação e comunidade ativas**
- **Padrões de design e acessibilidade**
- **Suporte a testes** — unitários e de integração

---

## 6. Comparação entre Frameworks

A escolha do framework certo impacta diretamente desempenho, escalabilidade, manutenção e experiência do usuário. A decisão deve considerar: complexidade do projeto, curva de aprendizado, desempenho e suporte da comunidade.

> Fonte: [StackShare](https://stackshare.io/stackups)

---

## 7. React

A biblioteca React, criada pelo Facebook em 2013, é uma das ferramentas mais populares para Web Apps. Exige conhecimento prévio em HTML e JavaScript. Sua arquitetura baseada em componentes e o uso do Virtual DOM garantem aplicações rápidas e escaláveis.

### Conceitos fundamentais
- **Hooks:** `useState` (gerencia estado) e `useEffect` (efeitos colaterais, como chamadas de API)
- **JSX:** usa `{}` para expressões JS; atributos em camelCase (`className`); tags sempre fechadas (`<img />`)
- **Gerenciamento de estado:** Context API (estados simples) ou Redux (estados complexos/globais)

### DOM x Virtual DOM
O DOM é a representação em árvore de uma página web. O Virtual DOM (usado no React) é uma cópia mais rápida: o React atualiza a cópia, compara com o DOM real e aplica apenas as diferenças, otimizando a performance.

---

## 8. Angular

### Requisitos
- Node.js instalado
- Conhecimento em Programação Orientada a Objetos (POO)

### Destaques
- Framework completo (roteamento, HTTP client, injeção de dependências)
- TypeScript nativo
- Arquitetura MVC
- CLI poderosa
- Change Detection eficiente

### Conceitos fundamentais
- **Componentes** — `@Component` (HTML + CSS + TypeScript)
- **Módulos** — `@NgModule`
- **Serviços** — `@Injectable`
- **Data Binding** — `[(ngModel)]` (two-way) e `{{ }}` (interpolação)
- **Injeção de dependência** e **roteamento** — `RouterModule`

### Criando um projeto
\`\`\`bash
npm install -g @angular/cli
ng new meu-app-angular
cd meu-app-angular
code .
ng serve
\`\`\`

### Estrutura principal
| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos públicos |
| `src/app/` | Componentes, módulos e serviços |
| `index.html` | Ponto de entrada; renderiza `<app-root>` |
| `main.ts` | Inicializa o módulo raiz e renderiza no DOM |
| `main.server.ts` / `server.ts` | Angular Universal (SSR) |
| `angular.json` | Configuração principal (build, testes, estilos) |
| `tsconfig*.json` | Configurações do TypeScript |

---

## 9. Vue

### Requisitos
- Node.js instalado
- Conhecimento em JavaScript/TypeScript
- Programação reativa e baseada em componentes

### Destaques
- **Progressivo** — adoção gradual, de partes pequenas a SPAs completas
- **Reatividade eficiente**
- **Single-File Components (SFC)** — HTML, CSS e JS em um único arquivo `.vue`
- **Curva de aprendizado suave**
- **Performance otimizada**

### Criando um projeto
\`\`\`bash
npm create vue@latest
cd meu-projeto-vue
npm install
code .
npm run dev
\`\`\`

### Estrutura principal
| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos que não passam pelo build do Vite |
| `src/assets/` | Imagens, fonts, CSS global processados pelo Vite |
| `src/components/` | Componentes reutilizáveis |
| `App.vue` | Componente raiz |
| `main.js` | Ponto de entrada; monta o app no DOM |
| `index.html` | Único HTML da SPA (`div #app`) |
| `vite.config.js` | Configurações do Vite (build, plugins, proxies) |

---

## 10. Next.js

Framework baseado em React para aplicações Web modernas e full-stack. Adiciona recursos que o React puro não possui:

- Roteamento baseado em arquivos
- Renderização no servidor (SSR)
- Server Components
- Otimização de imagens e fontes
- Gerenciamento de páginas e layouts
- APIs e recursos de backend
- Otimizações para desempenho e SEO

### Criando um projeto
\`\`\`bash
npx create-next-app@latest meu-projeto
cd meu-projeto
code .
npm run dev
\`\`\`

### Estrutura principal
| Item | Função |
|---|---|
| `node_modules/` | Dependências instaladas |
| `public/` | Arquivos estáticos (não processados pelo build) |
| `app/` | Diretório principal (App Router) — páginas, layouts, estilos |

> Arquivos `page.js` definem páginas; a organização das pastas determina as rotas.

---

## 11. Importando Projetos

Encontrar projetos-modelo prontos pode acelerar bastante o desenvolvimento — a comunidade open source oferece centenas de opções gratuitas e personalizáveis.

**Ferramentas para buscar projetos:**
- **GitHub** — [Repository Search](https://github.com/search) *(usar `git clone <url>`)*
- **Vercel** — Busca por Templates *(permite baixar apenas parte do repositório)*
- **CodeSandbox** — Template Search

> Fonte: [CodeSandbox](https://codesandbox.io/)

---

## ✅ Atividade

Desenvolver, **em grupo**, quatro projetos Web sobre o mesmo tema, utilizando **React, Vue, Angular e Next.js**. Cada projeto deve ter uma página funcional, responsiva e organizada, utilizando componentes e os recursos básicos da tecnologia escolhida.

Durante o desenvolvimento, os projetos devem ser:
- Versionados com **Git** e publicados no **GitHub**, com histórico de commits que registre a evolução da aplicação
- Organizados cada um em seu respectivo repositório
- Acompanhados de uma **breve comparação** entre as quatro tecnologias, destacando as principais diferenças encontradas

### Entregas
| # | Projeto |
|---|---------|
| 01 | React |
| 02 | Vue |
| 03 | Angular |
| 04 | Next.js |
| 05 | Cópia de um projeto a partir de um repositório |

---

## 📝 Resumo

\`\`\`
Frameworks × Bibliotecas → React, Angular, Vue, Next.js → Criação de projetos → Git/GitHub → Comparação técnica
\`\`\`

Esta aula aprofundou a criação prática de projetos nos principais frameworks/bibliotecas do mercado, reforçando conceitos de estrutura de pastas, ferramentas de CLI e boas práticas de versionamento aplicadas a cada tecnologia.

---

## 📚 Referências

- SOUZA, Natan. *Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.* São Paulo: Casa do Código, 2018.
- MACHADO, Kheronn Khennedy. *Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google.* São Paulo: Casa do Código, 2021.
- EIS, Diego. *Guia Front-end: o caminho das pedras para ser um dev front-end.* São Paulo: Casa do Código, 2015.
- GONÇALVES, Edson. *Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax.* Rio de Janeiro: Ciência Moderna, c2007.
- HARTCOPP, Patrícia Ferreira. *Métrica Web.* São Paulo: Contentus, 2020.
- NIEDERAUER, Juliano. *Desenvolvendo Websites com PHP.* 3. ed. São Paulo: Novatec, 2017.
- PREECE, J.; ROGERS, Y.; SHARP, H. *Design de Interação: além da interação Homem-Computador.* 3. ed. Porto Alegre: Bookman, 2013.
- SOUSA, Roque Fernando Marcos. *Canvas HTML 5: composição gráfica e interatividade na Web.* Rio de Janeiro: Brasport, 2014.

---

**Referência do material:** Frameworks Front-end — Projetos com Frameworks Front-end, Prof. Me. Deivison S. Takatu.
