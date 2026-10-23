# Aula 07 — Frameworks CSS

Repositório de anotações da disciplina de **Frameworks Front-end**, com foco nos fundamentos do CSS moderno, Box Model, alinhamentos com Flexbox, design responsivo e introdução ao framework utilitário **Tailwind CSS**.

**Professor:** Prof. Me. Deivison S. Takatu  
**Material de Apoio:** [Aula 07 - Frameworks CSS.pdf](./Aula%2007%20-%20Frameworks%20CSS.pdf)

---

## 📌 Conteúdos da Aula

- Introdução ao CSS (Cascading Style Sheets)
- Sintaxe Básica do CSS
- Formas de Aplicação: In-line, Interno e Externo
- Principais Propriedades do CSS
- Identificadores: Classes e IDs
- O Modelo de Caixas (Box Model)
- Layouts Flexíveis com Flexbox
- Design e Layouts Responsivos
- O que é um Framework CSS e o Desafio do CSS Manual
- Tailwind CSS e a Abordagem *Utility-First*
- Instalação e Uso do Tailwind CSS (Play CDN e Tailwind CLI)
- Extensão Tailwind CSS IntelliSense
- Atividades Práticas

---

## 1. O que é CSS (Cascading Style Sheets)?

O **CSS** é a linguagem de estilização responsável pela camada visual e apresentação de páginas web estruturadas em HTML.
* Não apenas define cores e tipografia, mas controla espaçamentos, margens, alinhamentos, dimensões e posicionamento de elementos;
* Permite criar layouts elegantes que unem estética, usabilidade e funcionalidade.

---

## 2. Sintaxe Básica

Toda regra CSS segue a estrutura:

```css
seletor {
    propriedade: valor;
}
```

* **Seletor:** indica em qual tag HTML a regra será aplicada (ex: `h1`, `.card`, `#menu`).
* **Propriedade:** o atributo de estilo que será alterado (ex: `color`, `background-color`).
* **Valor:** o ajuste que será atribuído à propriedade (ex: `#FF0000`, `16px`).

---

## 3. Formas de Aplicação do CSS

| Tipo | Onde é declarado | Exemplo | Recomendação |
|---|---|---|---|
| **In-line** | Direto no atributo `style` da tag HTML | `<p style="color: red; font-size: 20px;">Texto</p>` | Apenas para testes pontuais ou estilos dinâmicos de exceção. Dificulta manutenção. |
| **Interno** | Na tag `<style>` dentro do `<head>` | `<style> p { color: blue; } </style>` | Indicado para páginas isoladas ou protótipos de página única. |
| **Externo** | Em arquivo `.css` separado via `<link>` | `<link rel="stylesheet" href="estilos.css">` | **Padrão recomendado no mercado**. Centraliza o código e permite reutilização em múltiplas páginas. |

---

## 4. Principais Propriedades do CSS

* **`color`:** cor do texto (ex: `color: #ff0000;` ou `color: red;`).
* **`background-color`:** cor de fundo do elemento (ex: `background-color: #0000ff;`).
* **`font-family`:** família tipográfica utilizada (ex: `font-family: Arial, sans-serif;`).
* **`font-size`:** tamanho da fonte em `px`, `rem`, `em` ou `%` (ex: `font-size: 1.2rem;`).
* **`margin`:** margem externa (afastamento fora das bordas do elemento).
* **`padding`:** preenchimento interno (espaço entre a borda e o conteúdo).
* **`border`:** espessura, estilo e cor da borda (ex: `border: 2px solid black;`).
* **`width` / `height`:** largura e altura do elemento (ex: `width: 300px; height: 200px;`).
* **`display`:** modo de renderização na página (`block`, `inline`, `inline-block`, `flex`, `grid`, `none`).
* **`position`:** método de posicionamento (`static`, `relative`, `absolute`, `fixed`, `sticky`).
* **`top`, `right`, `bottom`, `left`:** coordenadas auxiliares usadas junto com `position`.
* **`text-align`:** alinhamento horizontal do texto (`left`, `center`, `right`, `justify`).

---

## 5. Classes vs IDs

* **Classes (`.nome-da-classe`):**
  * Podem ser aplicadas a **múltiplos elementos** da página;
  * Promovem consistência visual, reuso e manutenção limpa.
  * *Exemplo:* `.botao-primario { background: blue; color: white; padding: 10px; }`
* **IDs (`#nome-do-id`):**
  * Devem ser **únicos** por documento HTML;
  * Utilizados para elementos singulares, âncoras de navegação e manipulação precisa via JavaScript.
  * *Exemplo:* `#cabecalho-principal { height: 80px; background: #333; }`

---

## 6. O Box Model (Modelo de Caixas)

Todos os elementos na web são representados pelo navegador como caixas retangulares compostas por 4 camadas concêntricas:

```
+-----------------------------------+
|              MARGIN               | (Espaço externo entre elementos)
|  +-----------------------------+  |
|  |           BORDER            |  | (Borda visível ao redor)
|  |  +-----------------------+  |  |
|  |  |        PADDING        |  |  | (Espaço interno entre conteúdo e borda)
|  |  |  +-----------------+  |  |  |
|  |  |  |     CONTENT     |  |  |  | (Texto, imagens ou outros nós)
|  |  |  +-----------------+  |  |  |
|  |  +-----------------------+  |  |
|  +-----------------------------+  |
+-----------------------------------+
```

### Por que aplicar o Box Model corretamente?
* Controlar com precisão o tamanho final dos elementos;
* Criar espaçamentos coerentes e eliminar sobreposições visuais indesejadas;
* Facilitar layouts previsíveis que se adaptam a diferentes resoluções.

---

## 7. Flexbox (Flexible Box Layout)

O **Flexbox** é um módulo de layout unidimensional (linha ou coluna) projetado para distribuir espaços e alinhar itens dentro de um container com facilidade.

### Propriedades do Flex Container
* **`display: flex;`** → ativa o comportamento flexível.
* **`flex-direction`:** define o eixo principal:
  * `row` (padrão): itens dispostos em linha horizontal.
  * `column`: itens empilhados verticalmente.
  * `row-reverse` / `column-reverse`: inverte a ordem de disposição.
* **`justify-content`:** alinhamento ao longo do eixo principal:
  * `flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly`.
* **`align-items`:** alinhamento ao longo do eixo transversal:
  * `flex-start`, `center`, `flex-end`, `stretch`, `baseline`.
* **`flex-wrap`:** controla se os itens quebram linha (`nowrap` ou `wrap`).
* **`gap`:** define o espaçamento uniforme entre os itens flexíveis (ex: `gap: 16px;`).

---

## 8. Layouts Responsivos

Técnica de arquitetura de interface em que o conteúdo visual se adapta dinamicamente a telas de celulares, tablets e computadores desktop.

* **Tag Viewport indispensável no `<head>` do HTML:**
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```
* Melhora a experiência do usuário e elimina a necessidade de construir versões ou domínios separados por dispositivo.

---

## 9. O que é um Framework CSS?

Um **Framework CSS** é um conjunto pré-estruturado de padrões, ferramentas, classes utilitárias e componentes para acelerar a criação e garantir a padronização visual de interfaces web.

### Os Três Pilares de um Framework CSS:
1. **Layout:** sistemas de Grid, Flexbox e regras responsivas pré-configuradas.
2. **Estilos Básicos:** paleta de cores harmoniosa, escala tipográfica e espaçamentos padronizados.
3. **Componentes:** botões, cards, modais, alertas e navbars.

### O Problema do CSS Manual (Vanilla):
No CSS manual, cada pequeno elemento exige escrita de classes personalizadas, seleção minuciosa de propriedades e regras de mídia manual, tornando a escalabilidade em grandes equipes custosa e suscetível a incoerências de design.

---

## 10. Tailwind CSS & o Conceito Utility-First

O **Tailwind CSS** revolucionou a forma de construir interfaces através da abordagem **Utility-First**:
* Em vez de impor componentes fixos (como Bootstrap), fornece classes atômicas de finalidade única (ex: `flex`, `pt-4`, `text-center`, `bg-blue-600`, `rounded-lg`).
* O desenvolvedor compõe componentes personalizados diretamente no HTML sem precisar alternar entre arquivos CSS.

```html
<!-- Exemplo de botão moderno com Tailwind CSS -->
<button class="bg-blue-600 hover:bg-blue-700 text-white font-semibold px-6 py-3 rounded-lg shadow-md transition">
    Enviar
</button>
```

### Principais Benefícios:
* **Velocidade de Desenvolvimento:** estilização rápida diretamente no markup;
* **Flexibilidade Total:** total liberdade para construir interfaces sem o "aspecto genérico" de frameworks tradicionais;
* **Design Tokens Integrados:** escalas harmônicas de espaçamento, cores, sombras e fontes;
* **Abordagem Mobile First Nativa:** prefixos responsivos integrados (`sm:`, `md:`, `lg:`, `xl:`).

---

## 11. Formas de Importação do Tailwind CSS

### 1. Play CDN (para testes rápidos e estudos)
Adicionado no `<head>` do `index.html`:
```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
```

### 2. Tailwind CLI (para projetos profissionais de produção)
1. Instalação:
   ```bash
   npm install tailwindcss @tailwindcss/cli
   ```
2. Importação no arquivo principal de estilo:
   ```css
   @import "tailwindcss";
   ```
3. Suporte via PostCSS para compilação otimizada em frameworks modernos (Next.js, Vite, React).

### Produtividade com Ferramentas
* **Tailwind CSS IntelliSense:** extensão oficial para o VS Code que oferece autocompletar de classes, visualização imediata dos estilos compilados e detecção de erros.

---

## ✅ Atividades Práticas

### Atividade 01 — CSS Tradicional e Flexbox
1. Criar um projeto com `index.html` e `style.css` vinculado de forma externa via `<link>`.
2. Estilizar 20 elementos aplicando propriedades completas do Box Model (`content`, `padding`, `border`, `margin`).
3. Aplicar 20 propriedades de Flexbox para organizar os elementos de maneira responsiva.

### Atividade 02 — Aplicação com Tailwind CSS
1. Criar um projeto utilizando pelo menos **30 classes utilitárias distintas** do Tailwind CSS (abrangendo cores, tipografia, dimensões, bordas, Flexbox, Grid e responsividade).
2. Publicar a entrega em um repositório GitHub e documentar através de um arquivo Markdown contendo:
   * Prints do código-fonte e da aplicação executando;
   * Tabela listando as 30 classes utilizadas e suas respectivas finalidades;
   * Link da aplicação em funcionamento.

---

## 📝 Resumo

```
CSS Básico → Box Model → Flexbox → Layout Responsivo → Frameworks CSS → Tailwind CSS (Utility-First)
```

O domínio do Box Model e do Flexbox constitui a fundação necessária para compreender o layout na web, enquanto o Tailwind CSS potencializa a velocidade, flexibilidade e manutenibilidade do código front-end em escala.

---

**Referências:**
* SOUZA, Natan. *Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.* Casa do Código, 2018.
* EIS, Diego. *Guia Front-end: o caminho das pedras para ser um dev front-end.* Casa do Código, 2015.
* Takatu, Deivison S. *Material de Frameworks CSS*, SENAI.
* [Documentação Oficial do Tailwind CSS](https://tailwindcss.com/docs)
