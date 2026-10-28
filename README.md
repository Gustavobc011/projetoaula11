# Biblioteca da Bola

Atividade prática da **Aula 11 – Desenvolvimento para Internet (Uninove)**: duas páginas com Flexbox.
Prof. Felipe Santos de Jesus · Aluno: Gustavo

> Todos os dados do site (endereço, horários e oficina) são **fictícios**, criados para fins acadêmicos.

## Descrição do projeto

A **Biblioteca da Bola** é um espaço fictício de leitura e convivência sobre futebol.
O site tem duas páginas que funcionam como um único site:

- **Início** (`index.html`): apresenta o espaço, com título, imagem, dois parágrafos e um convite para a página Visita.
- **Visita** (`visita.html`): mostra como visitar, com três blocos: horários, como chegar e a oficina *Narração esportiva para iniciantes* (a partir de 14 anos).

As duas páginas têm o mesmo cabeçalho, menu e rodapé, e usam a mesma folha de estilos.

**Tecnologias:** somente HTML e CSS, sem JavaScript e sem frameworks.

### Estrutura de pastas

```
projetoaula11/
├── index.html           página Início
├── visita.html          página Visita
├── css/
│   └── estilo.css       CSS compartilhado pelas duas páginas
├── imagens/
│   └── aula11biblioteca.jpeg
└── README.md
```

### Como abrir

Abra o `index.html` no navegador e use o menu para ir até Visita e voltar.
Todos os caminhos são relativos (`css/estilo.css`, `imagens/...`, `visita.html`), então a pasta funciona em qualquer computador.

Versão publicada: `https://gustavobc011.github.io/projetoaula11/` *(endereço a confirmar depois da publicação)*

## Tamanhos de tela escolhidos (viewport)

Medidas em pixels CSS (área do navegador), não na resolução física do aparelho.

| Tela | Largura × altura | Justificativa |
|---|---|---|
| Celular | **375 × 812** | É a largura de celular mais comum (iPhone e Android de tamanho médio) e fica bem abaixo do breakpoint de 480px. |
| Tablet | **768 × 1024** | É o tablet em pé mais usado (iPad) e fica no meio da faixa de tablet, longe dos dois limites. |
| Desktop | **1366 × 768** | É a resolução de notebook mais comum no Brasil e fica acima do breakpoint de 1280px. |

## Breakpoints (pontos de mudança)

Os tamanhos de teste acima e os breakpoints abaixo são coisas diferentes. Os breakpoints são **faixas**: a página se adapta a qualquer largura dentro delas, não só às três medidas testadas.

| Faixa | Media query | O que muda |
|---|---|---|
| **Celular** – até 480px | `(max-width: 480px)` | Cabeçalho em **coluna** (nome em cima, menu embaixo). Imagem entre o título e os textos. Botão "Planeje sua visita" com a largura toda. Blocos da Visita **empilhados**. Título com 1,7rem. |
| **Tablet** – acima de 480px e abaixo de 1280px | `(min-width: 480.02px) and (max-width: 1279.98px)` | Cabeçalho em **linha** (nome à esquerda, menu à direita). A imagem continua acima dos textos. Blocos da Visita em **2 colunas**, e o 3º desce para a linha de baixo. Título com 2rem e margens laterais de 40px. |
| **Desktop** – 1280px ou mais | `(min-width: 1280px)` | Imagem e textos **lado a lado** (a `section` vira flex em linha). Os **3 blocos** da Visita ficam na mesma linha. Título com 2,2rem. O conteúdo fica centralizado com no máximo 1200px. |

**Por que esses limites?**
- **480px:** abaixo dessa largura, o nome do espaço e o menu ficam apertados na mesma linha. Por isso o cabeçalho passa para coluna, e os blocos da Visita não cabem lado a lado com texto legível.
- **1280px:** a partir daqui, cada metade da tela (imagem | textos) tem cerca de 560px. Isso deixa a imagem com bom tamanho e as linhas de texto com um comprimento confortável. Abaixo disso, colocar lado a lado deixaria a imagem pequena e o texto espremido.
- **Tablet compartilhando a organização do celular na página Início:** a imagem continua acima dos textos, como no modelo do enunciado, porque ainda não há largura suficiente para os dois lado a lado.

**O que acontece entre os tamanhos testados?** Por exemplo, a 1024px (notebook pequeno) a página usa o layout de tablet. O conteúdo estica para ocupar a largura, porque nada tem largura fixa (`max-width: 100%` na imagem e `flex` nos blocos).

### Onde está o Flexbox

| Contêiner flex | Filhos diretos | Para que serve |
|---|---|---|
| `header` | `.logo` e `nav` | Nome e menu separados (`space-between`). No celular, `flex-direction: column`. |
| `section` (Início, no desktop) | `#div1` (imagem) e `#div2` (textos) | Imagem e textos lado a lado, dividindo o espaço igualmente (`flex: 1`). |
| `#div2` (Início, no desktop) | `h1`, `p`, `p`, `a.convite` | Textos em coluna, distribuídos na altura da imagem. |
| `#blocos` (Visita) | os 3 `.bloco` | 1, 2 ou 3 por linha, conforme o `flex-basis` de cada faixa. |
| `nav ul` | os itens do menu | Início e Visita lado a lado. |
| `body` | `header`, `main`, `footer` | Mantém o rodapé no fim da tela. |

## Acessibilidade

- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` nas duas páginas.
- Imagem com `alt` descritivo.
- **Página atual no menu**: `aria-current="page"`, com **negrito e linha embaixo** (não depende só da cor).
- **Foco visível**: contorno laranja de 3px em todos os links ao navegar com Tab.
- Contraste: texto `#1e2b24` sobre `#fbfaf5` e texto branco sobre o verde `#1f4d36`, ambos acima de 4,5:1.
- Hierarquia de títulos: um `h1` por página e `h2` nos blocos da Visita.
- Convite feito com `<a>` (link), não com `<button>`.

## Imagem

- **Arquivo:** `imagens/aula11biblioteca.jpeg` (1280 × 960)
- **Conteúdo:** sala de leitura com estantes de livros, pufes coloridos e mesinhas.
- **Autoria e origem:** **[PREENCHER: autor da foto e de onde ela veio]**

## Esboços

<!-- Coloque as imagens dos esboços em uma pasta "esbocos/" e troque os nomes abaixo -->

| Página | Versão estreita (celular) | Versão ampla (desktop) |
|---|---|---|
| Início | ![Esboço Início estreito](esbocos/inicio-estreito.jpg) | ![Esboço Início amplo](esbocos/inicio-amplo.jpg) |
| Visita | ![Esboço Visita estreito](esbocos/visita-estreito.jpg) | ![Esboço Visita amplo](esbocos/visita-amplo.jpg) |

## Capturas de tela (6 prints)

<!-- Coloque os prints em uma pasta "prints/" e troque os nomes abaixo -->

| Página | Celular 375 × 812 | Tablet 768 × 1024 | Desktop 1366 × 768 |
|---|---|---|---|
| Início | ![Início 375x812](prints/inicio-375x812.png) | ![Início 768x1024](prints/inicio-768x1024.png) | ![Início 1366x768](prints/inicio-1366x768.png) |
| Visita | ![Visita 375x812](prints/visita-375x812.png) | ![Visita 768x1024](prints/visita-768x1024.png) | ![Visita 1366x768](prints/visita-1366x768.png) |

## Tabela de testes

| Página | Tamanho | Organização observada | Problema encontrado | Correção realizada |
|---|---|---|---|---|
| Início | 375 × 812 | Cabeçalho em coluna; título, imagem, 2 parágrafos e botão empilhados | Nenhum | Passou |
| Visita | 375 × 812 | Cabeçalho em coluna; 3 blocos empilhados; link de voltar no fim | Nenhum | Passou |
| Início | 768 × 1024 | Cabeçalho em linha; imagem acima dos textos | Nome e menu colados na borda da janela, desalinhados do conteúdo | Margem lateral de 40px no `header` e no `footer` (igual à do `main`) |
| Visita | 768 × 1024 | Blocos em 2 colunas, 3º na linha de baixo | Mesmo desalinhamento do cabeçalho | Mesma correção |
| Início | 1366 × 768 | Imagem e textos lado a lado | Cabeçalho desalinhado do conteúdo centralizado | Margem lateral calculada com `max(40px, calc((100% - 1120px) / 2))` |
| Visita | 1366 × 768 | 3 blocos na mesma linha | `section { display: flex }` deixaria título e blocos lado a lado | Removido o `<section>` da Visita (conteúdo direto no `main`) |
| Ambas | 480px (no limite) | Layout de celular | Nenhum | Passou |
| Ambas | 481px (logo acima) | Layout de tablet | Com a escala do Windows em 125%, a largura real era 480,8px: nenhuma media query valia, as 2 imagens apareciam juntas e os blocos voltavam a empilhar | Faixa do tablet trocada de `481px–1279px` para `480.02px–1279.98px` |
| Ambas | 1279px (logo abaixo) | Layout de tablet | Mesmo buraco entre 1279 e 1280px | Mesma correção |
| Ambas | 1280px (no limite) / 1281px | Layout de desktop | Nenhum | Passou |
| Ambas | 320px (celular pequeno) | Layout de celular | Nenhum; sem rolagem horizontal | Passou |
| Ambas | Zoom 200% em 1366 × 768 (≈ 683px) | Layout de tablet; menu sem sobrepor o nome | Nenhum | Passou |
| Ambas | Navegação com Tab | Ordem: nome → Início → Visita → convite/blocos → voltar | Nenhum; contorno laranja visível | Passou |
| Ambas | Links internos | Início ↔ Visita pelo menu, convite e "Voltar" | Nenhum; caminhos relativos, sem `C:\` | Passou |

## Problemas encontrados no código feito em aula (e corrigidos com autorização)

1. A tag `<link>` do CSS estava sem o `>` final, o que "engolia" o `<title>`.
2. O `<title>` era o genérico "Document".
3. As imagens estavam sem `alt`.
4. "Planeje sua visita" era um `<button>`, que não navega sem JavaScript. Foi trocado por `<a href="visita.html">`.
5. Cores de fundo de teste (azul, vermelho, amarelo) nas media queries. Ficaram comentadas no CSS.
6. O buraco entre os breakpoints (480–481px e 1279–1280px), descrito na tabela de testes.
