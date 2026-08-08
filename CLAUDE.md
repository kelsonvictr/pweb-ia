# 🌶️ Sistemas Web com Python — Flask + SQLite + Agentes de IA

> **Para IAs (Claude, Copilot, ChatGPT…)**: este arquivo é o ponto de entrada de contexto deste projeto. Antes de qualquer mudança, **leia também `context/README.md`** para descobrir os outros documentos de contexto. Sempre que o projeto evoluir, atualize estes arquivos.

---

## 🎯 O que é este projeto

Material didático do curso rápido **Sistemas Web com Python** (programa AI, prof. Kelson Almeida): **8 encontros de 2h (16h)** que pegam o aluno formado no bootcamp **Programação para Iniciantes** (`../programacao-iniciantes-v2/`) e o levam do Streamlit para um **sistema web de verdade**: Flask + Jinja + SQLite (SQL na mão) + agentes de codificação (Claude Code/Codex) + deploy público.

**Fio condutor**: o aluno reconstrói o **Sistema de Loja/Vendas** que fez como desafio final do bootcamp (`app_loja.py`, Streamlit + TinyDB, 4 abas: Estoque/Cadastrar/Vender/Vendas) — agora com URL própria, telas em HTML/Jinja e banco relacional. A narrativa é "o mesmo sistema, agora profissional".

**Público**: alunos egressos do bootcamp. Sabem Python básico (variáveis, if, loops, funções, dicts, JSON, TinyDB, Streamlit). **Nunca viram**: HTTP, HTML/CSS, SQL, terminal além do básico. Continuam iniciantes — clareza sobre estética.

---

## 🧭 Posicionamento estratégico (IMPORTANTE ao criar conteúdo)

Este curso é a **ponte** entre o bootcamp e o curso **Fullstack** (React + Java/Spring, `../novo-material-fullstack/`). Ele **não pode canibalizar** o fullstack:

- ❌ **NUNCA ensinar**: JavaScript, React, API REST separada, JSON como resposta de API, arquitetura em camadas formal, JWT. Isso é território do fullstack.
- ✅ **Território deste curso**: server-rendered (Flask + Jinja), SQL explícito na mão (`sqlite3`, SEM ORM), sessões simples, deploy free-tier, agentes de IA.
- ✅ O **capítulo 08 termina com ponte explícita** para o fullstack: limites do monólito ("e se precisar de app mobile? e se o front for de outra equipe?") → "o que o mercado usa" → convite.
- ✅ HTML/CSS das telas vem **pronto no starter kit** (Pico.css) — aluno só escreve Python e Jinja. Frontend caprichado é argumento de matrícula no fullstack, não conteúdo daqui.

Detalhes em `context/03-decisoes.md`.

---

## 🗂️ Arquitetura

```
sistemas-web-python/
├── CLAUDE.md                        ← este arquivo
├── index.html                       ← hub (landing) com cards dos 8 encontros
├── context/                         ← documentação persistente para IAs
│   ├── README.md
│   ├── 01-projeto-overview.md
│   ├── 02-conteudo-curso.md         ← ementa dos 8 dias — fonte da verdade
│   └── 03-decisoes.md               ← decisões estratégicas e pedagógicas
├── shared/                          ← design system copiado da v2 (mesma identidade)
│   ├── styles.css · components.css · animations.css · scripts.js
├── capitulos/
│   ├── 00-apresentacao/             ← ✅ pitch/venda do curso (mostrado à turma do bootcamp; contém preço e oferta)
│   ├── 01-ola-web-ola-flask/        ← Dia 1 · como a web funciona + primeira rota
│   ├── 02-formularios-jinja/        ← Dia 2 · Jinja + GET/POST
│   ├── 03-sql-sqlite/               ← Dia 3 · SQL na mão, adeus TinyDB
│   ├── 04-crud-parte-1/             ← Dia 4 · listar + cadastrar produtos
│   ├── 05-crud-parte-2/             ← Dia 5 · editar + excluir + flash
│   ├── 06-agentes-de-ia/            ← Dia 6 · Claude Code/Codex geram o login
│   ├── 07-projeto-final/            ← Dia 7 · CRUD próprio do aluno, com agente
│   └── 08-deploy-demo-day/          ← Dia 8 · deploy + apresentação + ponte fullstack
├── sobre/                           ← página do professor (copiada da v2)
└── assets/images/
```

---

## 🧑‍🏫 Filosofia didática (herdada da v2 — detalhes em `../programacao-iniciantes-v2/context/03-padroes-didaticos.md`)

1. **Analogia primeiro, código depois** — garçom (request/response), arquivo de fichas (SQL), estagiário genial (agente de IA)
2. **Visual > texto** — fluxos animados, diagramas request→response, ícones grandes
3. **WOW factor** — cada capítulo com ao menos uma animação memorável
4. **Padrão olhinho 👀** — dica + "tente sozinho" + spoiler escondido
5. **BugZilla 🐛** — vilão amigável nos erros comuns (TemplateNotFound, sqlite3.OperationalError, indentação em Jinja…)
6. **Uma operação de ponta a ponta por vez** — rota → template → SQL → tela funcionando; nunca "todas as rotas primeiro"

---

## ⚠️ Regras obrigatórias de HTML (mesmas do workspace)

- **Ligatures desativadas**: `shared/components.css` já contém `font-variant-ligatures:none` para `pre, code, .code-block`. **Nunca remover** — JetBrains Mono desenha `->` como `→` e o aluno copia errado.
- **Escapar `<` `>` `&` dentro de `<pre>`** sempre: `{% raw %}` não existe aqui — é HTML puro, então `<form>` vira `&lt;form&gt;`, `>=` vira `&gt;=`, etc.
- **Sempre** importar de `shared/` com paths relativos (`../../shared/styles.css`), nunca duplicar CSS.
- **Português brasileiro**, tom leve e acolhedor, emojis com moderação.

---

## 🔗 Referências cruzadas

- **Bootcamp de origem**: `../programacao-iniciantes-v2/` — em especial `capitulos/09-tinydb/` e `capitulos/10-streamlit/` (o desafio final `app_loja.py` está na seção `#desafio-final` do cap 10)
- **Curso fullstack (NÃO invadir o território dele)**: `../novo-material-fullstack/`
- **Padrão olhinho de referência**: `../backend-fullstack/index.html` (`try-first`)
- **Contexto global do workspace**: `../AGENTS.md` e `../CLAUDE.md`
