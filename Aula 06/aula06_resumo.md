# Aula 06 — Gestão de Projetos Front-End

**Disciplina:** Frameworks Front-end  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@edu.senai.br`)  
**Material de Apoio:** [Aula 06 - Projetos Front-End.pdf](./Aula%2006%20-%20Projetos%20Front-End.pdf)

---

## 📌 Sumário

1. [Por que Gerenciar um Projeto Front-End?](#1-por-que-gerenciar-um-projeto-front-end)
2. [O que é Gestão de Projetos Front-End](#2-o-que-é-gestão-de-projetos-front-end)
3. [Gestão de Requisitos (Requisitos, User Stories e Tarefas)](#3-gestão-de-requisitos)
4. [Gestão de Backlog](#4-gestão-de-backlog)
5. [Priorização e Estimativas](#5-priorização-e-estimativas)
6. [Definition of Done (DoD)](#6-definition-of-done-dod)
7. [Framework Ágil Scrum no Front-End](#7-framework-ágil-scrum-no-front-end)
8. [Repositórios Complementares](#8-repositórios-complementares)
9. [Atividade Prática](#9-atividade-prática)

---

## 1. Por que Gerenciar um Projeto Front-End?

Aplicações front-end modernas crescem rapidamente em complexidade (múltiplas telas, estados globais, componentes reutilizáveis, consumo de rotas de API e integrações).

### Riscos da Ausência de Gestão
* Tarefas esquecidas ou abandonadas;
* Requisitos confusos ou mal interpretados;
* Retrabalho contínuo na construção de interfaces;
* Conflitos frequentes de código no Git (*merge conflicts*);
* Atrasos nas entregas e dificuldade em medir o progresso da equipe;
* Falhas e retrabalho na integração entre o front-end e o backend.

### Benefícios ao Adicionar Processos de Gestão
* **Responsabilidades claras:** cada membro sabe exatamente o que implementar;
* **Prioridades definidas:** foco no que traz valor real ao usuário final primeiro;
* **Entregas incrementais:** interfaces entregues e validadas continuamente;
* **Visibilidade e previsibilidade:** facilidade no acompanhamento do progresso;
* **Redução drástica de retrabalho.**

---

## 2. O que é Gestão de Projetos Front-End

Gerenciar projetos front-end significa organizar pessoas, tarefas, tecnologias, design systems e prazos para transformar uma ideia ou protótipo em uma aplicação web funcional e escalável.

O processo exige planejamento prévio, acompanhamento contínuo e flexibilidade para adaptações ao longo do ciclo de desenvolvimento.

---

## 3. Gestão de Requisitos

Todo projeto de software nasce de uma ideia ou necessidade que precisa ser decomposta em três níveis hierárquicos:

1. **Requisito (Visão de Negócio/Sistema):**  
   * *Exemplo:* O sistema deve permitir o gerenciamento completo de tarefas.
2. **User Story (História de Usuário):**  
   * Estruturada sob a perspectiva de quem utiliza o sistema: `"Como [usuário], quero [ação] para que [benefício]"`.  
   * *Exemplo:* "Como usuário cadastrado, quero criar uma nova tarefa para organizar minhas entregas diárias."
3. **Tarefas Técnicas (*Tasks*):**  
   * Desdobramento técnico para o time de front-end implementar:
     * Criar formulário de cadastro com validações de campos;
     * Desenvolver o componente visual do botão e do card de tarefa;
     * Integrar chamada HTTP `POST` com a API backend;
     * Desenvolver testes unitários de interface e acessibilidade.

---

## 4. Gestão de Backlog

O **Product Backlog** é a lista viva e dinâmica contendo todas as funcionalidades, melhorias de UX/UI, manutenções, débitos técnicos e correções de bugs necessários para evoluir o produto.

* Os itens recebem prioridades explícitas;
* Permite que a equipe concentre energia nas entregas mais estratégicas de cada ciclo.

---

## 5. Priorização e Estimativas

* **Priorização:** Avalia restrições técnicas, dependências de APIs e impacto no negócio para decidir quais componentes e páginas devem ser desenvolvidos primeiro.
* **Estimativas:** Ajudam a equipe a entender a complexidade relativa de cada funcionalidade antes de assumir o compromisso da iteração (Sprint).

---

## 6. Definition of Done (DoD)

A **Definição de Concluído (*Definition of Done*)** define uma lista de critérios objetivos de qualidade que uma tarefa ou componente deve atender antes de ser considerado finalizado e aprovado para produção.

### Exemplos de critérios de DoD no Front-End:
* [x] Código implementado seguindo o padrão de arquitetura de pastas;
* [x] Responsividade verificada em múltiplos tamanhos de tela (mobile, tablet, desktop);
* [x] Integração completa com os endpoints da API (tratamento de loading e erro);
* [x] Testes de interface executados e aprovados;
* [x] Code Review (revisão de Pull Request) realizada por outro desenvolvedor;
* [x] Merge realizado na branch principal sem quebras no build de produção.

---

## 7. Framework Ágil Scrum no Front-End

O **Scrum** é uma estrutura ágil para gerenciar projetos complexos através de ciclos curtos e iterativos chamados **Sprints**:
* **Planejamento de Sprint:** seleção das User Stories mais prioritárias do backlog;
* **Kanban / Board Visual:** organização do fluxo de trabalho em colunas (*To Do*, *In Progress*, *Review*, *Done*);
* **Inspeção e Adaptação:** reuniões rápidas e retrospectivas para melhoria contínua do time.

---

## 8. Repositórios Complementares

* [deivisontakatu/aula-gestao](https://github.com/deivisontakatu/aula-gestao)
* [deivisontakatu/aula-gestao-produto](https://github.com/deivisontakatu/aula-gestao-produto)
* [deivisontakatu/aula-scrum](https://github.com/deivisontakatu/aula-scrum)

---

## 9. Atividade Prática

1. **Planejamento:** Elaborar a gestão completa das tarefas do Projeto Integrador Interdisciplinar utilizando os conceitos aprendidos.
2. **Estruturação:** Cada grupo deve definir backlog, critérios de priorização, divisão em tarefas técnicas, estimativas, planejamento de Sprint, fluxo em Kanban, estratégia de branches no Git e Definition of Done (DoD).
3. **Documentação:** Registrar todo o planejamento em um arquivo Markdown e manter o quadro Kanban ativo durante o ciclo de desenvolvimento.
