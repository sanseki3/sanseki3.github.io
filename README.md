# Sanseki site — Jekyll + GitHub Pages

Este pacote transforma o seu site em um arquivo pessoal vivo, com:

- notas públicas em Markdown;
- ensaios em Markdown;
- projetos em páginas próprias;
- datas de início e última atualização;
- status (`seed`, `draft`, `growing`, `stable`, `finished`);
- páginas de índice para notas, ensaios, projetos, temas, changelog e arquivo;
- home com destaques e atualização recente.

## O caminho mais rápido (sem terminal)

1. Entre no repositório `sanseki3.github.io`.
2. Faça um backup simples do estado atual:
   - **Code** → **Download ZIP**, ou
   - crie um branch chamado `backup-single-page`.
3. Extraia este pacote no seu computador.
4. No repositório do GitHub, envie todos estes arquivos para a raiz do repositório.
   - Você pode usar **Add file → Upload files**.
   - Se pedir para sobrescrever `index.html`, aceite.
5. Vá em **Settings → Pages**.
6. Em **Build and deployment**, escolha:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main`
   - **Folder:** `/ (root)`
7. Salve.
8. Aguarde a publicação e abra `https://sanseki3.github.io/`.

## O fluxo editorial que você deve seguir

### Para criar uma nota nova

1. Copie o arquivo `_templates/note-template.md`.
2. Cole dentro da pasta `_notes/`.
3. Renomeie o arquivo com um slug simples. Exemplo:
   - `nier-replicant.md`
   - `angelology-russian-orthodoxy.md`
   - `twin-peaks-notes.md`
4. Edite o bloco YAML do topo.
5. Escreva o corpo em Markdown.
6. Commit.

### Campos principais de uma nota

- `title`: título publicado.
- `summary`: resumo curto para listas.
- `started`: quando a nota começou.
- `updated`: última atualização manual.
- `status`: `seed`, `draft`, `growing`, `stable` ou `finished`.
- `finished`: `true` ou `false`.
- `tags`: lista curta de temas.
- `changelog`: histórico manual de mudanças importantes.

### Exemplo mínimo

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

## Para atualizar uma nota existente

1. Abra o arquivo em `_notes/`.
2. Altere o campo `updated` para a data nova.
3. Se o estágio mudou, altere `status`.
4. Acrescente um item em `changelog`.
5. Commit.

## Como criar links entre páginas

Use links normais de Markdown:

```md
Veja também: [Nier Replicant](/notes/nier-replicant/)
```

Esse é o jeito mais simples e robusto de criar relações no site sem depender de plugin.

## Como testar localmente (opcional)

Se você quiser testar localmente no futuro:

1. instale Ruby e Bundler;
2. na pasta do projeto, rode `bundle install`;
3. rode `bundle exec jekyll serve`;
4. abra `http://127.0.0.1:4000/`.

## O que já vem pronto

- layout principal minimalista inspirado no espírito de site pessoal durável;
- sistema de notas públicas;
- nota inicial de `Nier Replicant`;
- página de temas com filtragem por seções;
- changelog manual por nota;
- arquivo geral.
