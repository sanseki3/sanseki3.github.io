# Site pessoal do Pedro

> Caderno público de processo, ensaios e projetos.
> Construído com **Jekyll + GitHub Pages**. Trilíngue (PT · EN · 日本語).

---

## Como funciona, em uma frase

Você escreve cada post como um arquivo `.md` (Markdown — o mesmo do Obsidian) e empurra pro GitHub. O GitHub publica o site automaticamente em **alguns minutos**.

---

## 1. Atualizando o site existente

Como o site já está no ar, esta é a parte que importa pro dia a dia. Você tem duas formas de subir mudanças:

**Pelo GitHub Web (mais fácil):** abra o repositório, navegue até o arquivo, clique no lápis pra editar, e em "Commit changes" salve. Pra **arquivos novos**, use **Add file → Create new file** ou **Upload files**.

**Pelo Cowork:** já é o caminho que você usou pra publicar. Continue usando.

---

## 2. Como escrever um novo post

### 2.1. Decidir os idiomas

Cada post pode existir em 1, 2 ou 3 idiomas. Você decide. **Recomendação:** escreva primeiro em português (idioma principal), depois adicione inglês quando achar que vale, e japonês só se tiver revisão de falante nativo.

### 2.2. Criar os arquivos

Cada idioma tem sua pasta:

| Idioma | Pasta |
|--------|-------|
| Português | `_posts/` |
| Inglês | `_posts_en/` |
| Japonês | `_posts_ja/` |

**Convenção de nome de arquivo:** `AAAA-MM-DD-slug-com-tracos.md`. O **slug** pode ser diferente em cada idioma — ele vira o endereço da página.

Exemplo, um post sobre o making-of de Predadores nos três idiomas:
- `_posts/2026-04-30-predadores-making-of.md` → `/posts/predadores-making-of/`
- `_posts_en/2026-04-30-predators-making-of.md` → `/en/posts/predators-making-of/`
- `_posts_ja/2026-04-30-puredata-zu-meiking.md` → `/ja/posts/puredata-zu-meiking/`

### 2.3. Front matter (cabeçalho do arquivo)

Todo post começa com este bloco. **A chave `translations` é o que conecta as versões** entre si:

**Em `_posts/2026-04-30-predadores-making-of.md`:**

```yaml
---
layout: post
title: "Predadores: making-of"
subtitle: "Linha curta de descrição."
date: 2026-04-30
kicker: "Making-of · Predadores"
tags: [predadores, making-of]
lang: pt-br
translations:
  en: /en/posts/predators-making-of/
  ja: /ja/posts/puredata-zu-meiking/
---
```

**Em `_posts_en/2026-04-30-predators-making-of.md`:**

```yaml
---
layout: post
title: "Predators: making-of"
subtitle: "Short description line."
date: 2026-04-30
kicker: "Making-of · Predators"
tags: [predators, making-of]
lang: en
translations:
  pt-br: /posts/predadores-making-of/
  ja: /ja/posts/puredata-zu-meiking/
---
```

**Em `_posts_ja/2026-04-30-puredata-zu-meiking.md`:**

```yaml
---
layout: post
title: "プレデターズ：メイキング"
subtitle: "短い説明文。"
date: 2026-04-30
kicker: "メイキング・プレデターズ"
tags: [プレデターズ, メイキング]
lang: ja
translations:
  pt-br: /posts/predadores-making-of/
  en: /en/posts/predators-making-of/
---
```

**Importante:** os caminhos em `translations:` precisam bater **exatamente** com o `permalink` do outro arquivo. Errou um caractere, o switcher mostra como "indisponível".

### 2.4. Se o post existe só em um idioma

Apague a chave `translations:` ou deixe vazia. O switcher vai mostrar PT em vermelho (ativo) e EN/日本語 esmaecidos — exatamente o comportamento desejado, indicando ao leitor que aquele conteúdo só existe em português.

---

## 3. Adicionando imagens

1. Coloque a imagem em `assets/images/nome-da-imagem.jpg`.
2. No post: `![descrição](/assets/images/nome-da-imagem.jpg)`
3. Pra legenda:

```html
<figure>
  <img src="/assets/images/nome-da-imagem.jpg" alt="descrição">
  <figcaption>Legenda da imagem</figcaption>
</figure>
```

---

## 4. Markdown rápido

```markdown
## Título de seção

**negrito**, *itálico*, [link](https://exemplo.com)

> Citação em bloco — boa pra epígrafes.

- Lista
- Com itens

---  (linha horizontal)
```

---

## 5. Mudando textos da interface e da home

**Texto da página inicial** (kicker, headline, intro): edite `_data/i18n.yml`, na seção "TEXTO DA HOME". Ali ficam as três traduções (PT, EN, JA) lado a lado. Você pode usar HTML inline:

- `<em>palavra</em>` → palavra em italic colorido (no tema noite vira prata destacada; no dia vira rosa-velho)
- `<br>` → quebra de linha

Os textos dos menus, "Voltar ao índice", etc. estão na mesma `_data/i18n.yml`, mais abaixo. Pra mudar qualquer coisa em qualquer idioma, edite esse arquivo.

## 6. Os dois temas (noite e dia)

O site abre por padrão no **tema noite** (índigo profundo, estrelas, lua cheia). Quem visita pode trocar pro **tema dia** (papel quente, azul-céu) clicando no ícone do sol/lua no canto superior direito. A escolha fica salva no navegador da pessoa — quando ela voltar, o tema fica como deixou.

Pra mudar a paleta de cores de qualquer tema, abra `assets/css/main.css` e edite as variáveis no topo do arquivo (seções `:root[data-theme="night"]` e `:root[data-theme="day"]`).

---

## 7. Estrutura do site

```
.
├── _config.yml              # configuração geral
├── _data/i18n.yml           # textos da interface nos 3 idiomas
├── _layouts/                # templates HTML (não mexer)
├── _includes/               # cabeçalho, rodapé, switcher (não mexer)
├── _posts/                  # POSTS EM PORTUGUÊS
├── _posts_en/               # POSTS EM INGLÊS
├── _posts_ja/               # POSTS EM JAPONÊS
├── _ensaios/                # ENSAIOS LONGOS EM PORTUGUÊS (criar se quiser)
├── assets/
│   ├── css/main.css         # estilos visuais
│   └── images/              # IMAGENS DOS POSTS
├── index.html               # home em português (raiz: /)
├── sobre.md                 # /sobre/
├── projetos.md              # /projetos/
├── ensaios.html             # /ensaios/
├── en/                      # versão inglesa
│   ├── index.html           # /en/
│   ├── about.md             # /en/about/
│   ├── projects.md          # /en/projects/
│   └── essays.html          # /en/essays/
├── ja/                      # versão japonesa
│   ├── index.html           # /ja/
│   ├── about.md             # /ja/about/
│   ├── projects.md          # /ja/projects/
│   └── essays.html          # /ja/essays/
├── 404.html
├── Gemfile
└── README.md
```

---

## 8. Cuidados especiais com cada idioma

**Português** — idioma principal. Sempre publique aqui primeiro.

**Inglês** — IA + sua revisão funcionam bem. Mas leia em voz alta antes de publicar — IA tende a produzir prosa correta mas sem sangue.

**Japonês** — **antes de divulgar publicamente que tem versão japonesa, peça pra um falante nativo revisar tudo.** Tradução automática de português → japonês ainda erra registro, ordem natural de informação e nuance de um jeito que um leitor japonês percebe imediatamente como "tradução de gaijin". As versões iniciais que estão no site são razoáveis mas não foram revisadas — trate como rascunho até passar pelos olhos de alguém.

---

## 9. Problemas comuns

**Mudei algo e não atualiza.** Aguarde 2-3 minutos. Se persistir, vá em **Actions** no repositório e veja se o build deu erro (vermelho). Clique pra ver o motivo.

**Switcher mostra EN ou 日本語 esmaecido quando devia estar ativo.** O caminho em `translations:` está errado. Vai no arquivo, confere se o caminho bate exatamente com o `permalink` do outro arquivo. Barras finais importam (`/en/posts/foo/` é diferente de `/en/posts/foo`).

**Quebrou tudo, não sei o que fiz.** Volte uma versão. No GitHub, abra o arquivo, clique em **History** → escolha versão antiga → "Revert".

**Quero domínio próprio.** Compre em qualquer registro, configure DNS apontando pro GitHub Pages ([instruções aqui](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site)). Em **Settings → Pages**, em "Custom domain", coloque o domínio.

---

## 10. Personalização visual avançada

Quase tudo está em `assets/css/main.css`, no topo, na seção `:root` (variáveis CSS):

```css
--color-bg: #F4F1EA;       /* cor de fundo */
--color-ink: #1C1B19;      /* cor do texto */
--color-accent: #8B3A3A;   /* cor de destaque (links, marcações) */
```

Mude essas três e o tom do site inteiro muda.

---

Boa escrita.
