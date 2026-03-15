# Sanseki site — Jekyll + GitHub Pages

Este pacote transforma o seu site em um arquivo pessoal vivo, agora com:

- tema escuro (fundo preto, texto branco e tipografia estilo Times);
- navegação superior em abas;
- notas públicas em Markdown;
- diário dos sonhos com organização cronológica por `dream_date`;
- ensaios em Markdown;
- projetos em páginas próprias;
- datas de início e última atualização;
- status (`seed`, `draft`, `growing`, `stable`, `finished`);
- páginas de índice para notas, diário dos sonhos, ensaios, projetos, temas, changelog e arquivo;
- home com destaques e atualização recente.

## O caminho mais rápido (sem terminal)

1. Entre no repositório `sanseki3.github.io`.
2. Faça um backup simples do estado atual:
   - **Code** → **Download ZIP**, ou
   - crie um branch chamado `backup-single-page`.
3. Extraia este pacote no seu computador.
4. No repositório do GitHub, envie todos estes arquivos para a raiz do repositório.
   - Você pode usar **Add file → Upload files**.
   - Se pedir para sobrescrever arquivos, aceite.
5. Vá em **Settings → Pages**.
6. Em **Build and deployment**, escolha:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main`
   - **Folder:** `/ (root)`
7. Salve.
8. Aguarde a publicação e abra `https://sanseki3.github.io/`.

## O fluxo editorial mais simples

### Para criar uma nota nova

1. Copie o arquivo `_templates/note-template.md`.
2. Cole dentro da pasta `_notes/`.
3. Renomeie com um slug simples. Exemplo:
   - `nier-replicant.md`
   - `angelology-russian-orthodoxy.md`
   - `twin-peaks-notes.md`
4. Edite o bloco YAML do topo.
5. Escreva o corpo em Markdown.
6. Commit.

### Para criar uma entrada no Diário dos Sonhos

1. Copie o arquivo `_templates/dream-template.md`.
2. Cole dentro da pasta `_dreams/`.
3. Renomeie usando data + nome curto. Exemplo:
   - `2026-03-14-sonho-no-mar.md`
   - `2026-03-21-cidade-submersa.md`
4. Preencha o campo `dream_date`.
5. Escreva primeiro do jeito bruto.
6. Commit.

A página `/diario-dos-sonhos/` organiza tudo automaticamente por mês e ano com base em `dream_date`.

## Campos principais de uma nota

- `title`: título publicado.
- `summary`: resumo curto para listas.
- `started`: quando a página começou.
- `updated`: última atualização manual.
- `status`: `seed`, `draft`, `growing`, `stable` ou `finished`.
- `finished`: `true` ou `false`.
- `tags`: lista curta de temas.
- `changelog`: histórico manual de mudanças importantes.

## Campo extra para sonhos

- `dream_date`: data do sonho. É esse campo que organiza a cronologia do Diário dos Sonhos.

## Exemplo mínimo de nota

```md
---
title: "Nier Replicant"
summary: "Notas e reflexões sobre Nier Replicant."
started: 2026-03-09
updated: 2026-03-09
status: growing
finished: false
tags: [jogos, narrativa, arte, melancolia]
---

Primeiro parágrafo.
```

## Exemplo mínimo de sonho

```md
---
title: "Sonho no mar"
summary: "Barcos, uma cidade escura e uma sensação de pressa."
dream_date: 2026-03-14
started: 2026-03-14
updated: 2026-03-14
status: draft
finished: false
tags: [sonhos]
---

Escreva o sonho aqui.
```

## Como criar links entre páginas

Use links normais de Markdown:

```md
Veja também: [Nier Replicant](/notes/nier-replicant/)
```

## Como testar localmente (opcional)

Se você quiser testar localmente no futuro:

1. instale Ruby e Bundler;
2. na pasta do projeto, rode `bundle install`;
3. rode `bundle exec jekyll serve`;
4. abra `http://127.0.0.1:4000/`.
