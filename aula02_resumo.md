# Aula 02 — Configuração do Ambiente de Desenvolvimento

Repositório de anotações da disciplina de **Frameworks Front-end**, com foco na configuração do ambiente de desenvolvimento, versionamento de código, Git, Node.js, React e deploy de aplicações.

**Professor:** Prof. Me. Deivison S. Takatu

---

## 📌 Conteúdos da Aula

- Introdução ao Versionamento
- Versionamento Semântico (SemVer)
- Git e Controle de Versão
- Tags, Branches e Boas Práticas no Git
- IDE e Visual Studio Code
- Node.js e NPM
- Criação de Projetos React
- Deploy e Hospedagem com Vercel
- Atividade Prática

---

## 1. Versionamento

Processo de atribuir um identificador único a cada versão de um projeto, registrando **o que** foi alterado, **quem** alterou, **quando** e permitindo recuperar versões anteriores.

### Versionamento x Backup

| Versionamento | Backup |
|---|---|
| Mantém o histórico das alterações | Mantém uma cópia do estado atual |
| Registra quem, quando e por que mudou | Não possui rastreabilidade detalhada |
| Permite colaboração simultânea | Normalmente trabalha com cópias |
| Permite reversão granular | Geralmente restaura o estado completo |

### Benefícios
- Trabalho simultâneo entre desenvolvedores
- Redução de retrabalho e conflitos
- Auditoria, rastreabilidade e recuperação de versões
- Maior controle de qualidade do software

---

## 2. SemVer (Versionamento Semântico)

Padrão: **MAJOR.MINOR.PATCH**

\`\`\`
2.1.3
\`\`\`

- **MAJOR** → mudança incompatível (ex: `2.0.0`)
- **MINOR** → nova funcionalidade compatível (ex: `1.1.0`)
- **PATCH** → correção de bug (ex: `1.0.1`)

**Exemplo de evolução:**
\`\`\`
1.0.0 → Primeira versão estável
1.1.0 → Nova funcionalidade compatível
1.1.1 → Correção de bug
2.0.0 → Mudança incompatível
\`\`\`

**Tipos de alterações:** Bug Fix, New Feature, Feature Enhancement, Refactoring, Performance, Security Patch, Dependency Update, Adding Tests.

---

## 3. Git

Sistema de controle de versão para registrar e gerenciar alterações nos arquivos do projeto.

**Verificar instalação:**
\`\`\`bash
git --version
\`\`\`

**Configuração inicial:**
\`\`\`bash
git config --global user.name "<Nome>"
git config --global user.email "<Email>"
\`\`\`

---

## 4. Tags no Git

Marcadores utilizados para identificar pontos específicos do histórico, geralmente releases (ex: `v1.0.0`).

- **Lightweight** → apenas identifica um commit
- **Annotated** → armazena autor, data e mensagem

**Comandos:**
\`\`\`bash
git tag                # listar tags
git tag 1.0.0           # criar tag
git push origin 1.0.0   # enviar tag ao remoto
\`\`\`

---

## 5. Boas Práticas com Git

- Commits **pequenos e frequentes**
- Mensagens **claras**, indicando o que e por que mudou
- Uso de **branches** para novas funcionalidades sem afetar a branch principal
- **Testar** antes de fazer merge

---

## 6. VS Code

IDE que reúne ferramentas para desenvolver, testar, executar e depurar software. Oferece diversos recursos por meio de extensões.

---

## 7. Node.js

Ambiente de execução JavaScript no lado do servidor, permitindo usar JS tanto no Front-end quanto no Back-end.

\`\`\`bash
node --version
\`\`\`

---

## 8. NPM

Gerenciador de pacotes do Node.js — instala, atualiza e remove dependências.

Principal arquivo: **`package.json`**

\`\`\`bash
npm install
\`\`\`

---

## 9. Criando um Projeto React

\`\`\`bash
npx create-react-app meu-projeto-react
cd meu-projeto-react
code .
npm start
\`\`\`

> `npx` executa pacotes sem instalá-los globalmente. `create-react-app` gera a estrutura inicial (build, Babel, servidor local, scripts, etc.).

---

## 10. Estrutura do Projeto React

| Item | Função |
|---|---|
| `node_modules/` | Pacotes e dependências instaladas |
| `public/` | Arquivos públicos (HTML, JSON, imagens) |
| `src/` | Código JavaScript e React da aplicação |
| `.gitignore` | Define o que o Git deve ignorar |
| `package.json` | Dependências e informações do projeto |
| `package-lock.json` | Registro exato das dependências instaladas |

### Principais arquivos
- **`index.js`** → ponto de entrada; renderiza `App` no DOM
- **`App.js`** → componente raiz da aplicação
- **`App.css`** → estilos do componente App
- **`index.css`** → estilos globais

---

## 11. Deploy

Processo de colocar a aplicação em produção: compilação, configuração do ambiente, testes finais e publicação.

---

## 12. Vercel

Plataforma de deploy e hospedagem de aplicações modernas.

**Principais recursos:**
- Integração com GitHub
- Deploy automático após push
- CDN global e escalabilidade automática
- Rollback e Serverless Functions

---

## 13. Fluxo Completo

\`\`\`
VS Code → Desenvolvimento React → Git → Commit → Push → GitHub → Vercel → Deploy → Aplicação Online
\`\`\`

---

## ✅ Atividade Prática

1. Desenvolver uma aplicação React
2. Versionar o projeto com Git
3. Realizar commit e push para o GitHub
4. Conectar o repositório à Vercel
5. Fazer o deploy e disponibilizar a URL pública

## 👥 Atividade em Grupo

Elaborar relatório técnico em PDF (mín. 5 páginas) sobre um framework Front-end, contendo: características, vantagens, aplicações no mercado e exemplo de uso.

---

## 📝 Resumo

\`\`\`
Versionamento → Git → GitHub → Node.js + NPM → React → Vercel → Deploy
\`\`\`

Esses conceitos formam a base para organizar projetos, trabalhar em equipe, controlar alterações e publicar aplicações Web.

---

**Referência:** Material da disciplina Frameworks Front-end — Configuração do Ambiente de Desenvolvimento, Prof. Me. Deivison S. Takatu.
