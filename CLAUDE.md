# 🌶️ Sistemas Web com Python — Flask + SQLite + Agentes de IA

> **Para IAs (Claude, Copilot, ChatGPT…)**: este arquivo é o ponto de entrada de contexto deste projeto. Antes de qualquer mudança, **leia também `context/README.md`** para descobrir os outros documentos de contexto. Sempre que o projeto evoluir, atualize estes arquivos.

---

## 🎯 O que é este projeto

Material didático do curso rápido **Sistemas Web com Python** (programa AI, prof. Kelson Almeida): **8 encontros de 2h (16h)**, um curso **independente** que leva quem sabe o básico de Python a um **sistema web de verdade**: Flask + Jinja + SQLite (SQL aprendido na mão) + desenvolvimento orientado por agentes de codificação (Claude Code/Codex/Antigravity) a partir do Dia 4 + deploy público.

**Fio condutor**: o aluno constrói do zero uma **Loja** com quatro áreas (Estoque, Cadastrar, Vender, Vendas), com URL própria, telas em HTML/Jinja e banco relacional. No Dia 7 cria a **Estante**, um sistema novo, e no Dia 8 a publica.

**Público**: quem sabe Python básico (variáveis, if, loops, funções, listas, dicts), venha de onde vier. **Não assumir** nenhum curso anterior, nem citar bootcamp, Streamlit ou TinyDB no material do aluno. **Nunca viram**: HTTP, HTML/CSS, SQL, terminal além do básico. Continuam iniciantes — clareza sobre estética.

**Orçamento de aulas (D24)**: são 8 aulas e cada dia precisa caber em 1. A T01 usou 10. Conteúdo novo em sala exige dizer o que sai ou vai pra casa. Dias 1 a 3 são sem IA em sala.

---

## 🧭 Posicionamento estratégico (IMPORTANTE ao criar conteúdo)

Este curso se sustenta sozinho e termina com um convite ao curso **Fullstack** (React + Java/Spring, `../novo-material-fullstack/`). Ele **não pode canibalizar** o fullstack:

- ❌ **NUNCA ensinar**: JavaScript, React, API REST separada, JSON como resposta de API, arquitetura em camadas formal, JWT. Isso é território do fullstack.
- ✅ **Território deste curso**: server-rendered (Flask + Jinja), SQL explícito na mão (`sqlite3`, SEM ORM), sessões simples, deploy free-tier, agentes de IA.
- ✅ O **capítulo 08 termina com ponte explícita** para o fullstack: limites do monólito ("e se precisar de app mobile? e se o front for de outra equipe?") → "o que o mercado usa" → convite.
- ✅ HTML/CSS das telas: o aluno digita o HTML (D10) com Pico.css de ponto de partida; no Dia 3½, em casa, o **agente gera o CSS** a partir de uma espec do aluno (D24). Frontend não é *ensinado* aqui — é argumento de matrícula no fullstack.

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
│   ├── 00-apresentacao/             ← ✅ pitch/venda do curso (contém preço e oferta)
│   ├── 01-ola-web-ola-flask/        ← Dia 1 · como a web funciona + primeira rota
│   ├── 02-formularios-jinja/        ← Dia 2 · Jinja + GET/POST
│   ├── 03-sql-sqlite/               ← Dia 3 · SQL na mão, sem IA
│   ├── 03b-ia-agentes/              ← Dia 3½ · teoria de IA + instalação + primeira tarefa (em casa)
│   ├── 04-crud-parte-1/             ← Dia 4 · virada agent-first: listar + cadastrar por prompts
│   ├── 05-crud-parte-2/             ← Dia 5 · editar + excluir + vender por prompts
│   ├── 06-agentes-de-ia/            ← Dia 6 · login em prompts + checkpoints
│   ├── 07-projeto-final/            ← Dia 7 · a Estante: sistema novo do zero, 100% por prompts
│   └── 08-deploy-demo-day/          ← Dia 8 · Estante em Docker no Render + Demo Day
├── sobre/                           ← página do professor (copiada da v2)
└── assets/images/
```

---

## 🧑‍🏫 Filosofia didática (padrões da programa AI — detalhes em `../programacao-iniciantes-v2/context/03-padroes-didaticos.md`)

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

- **Registro das aulas dadas**: inventário da ClassContent em `../../../programaai-full-site/programaai-agent-helper/carrosseis/_serie-conteudo/pesquisa/classcontent-inventario.md`
- **Curso fullstack (NÃO invadir o território dele)**: `../novo-material-fullstack/`
- **Padrão olhinho de referência**: `../backend-fullstack/index.html` (`try-first`)
- **Contexto global do workspace**: `../AGENTS.md` e `../CLAUDE.md`
