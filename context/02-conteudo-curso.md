# 02 · Conteúdo do curso — ementa dos 8 encontros (FONTE DA VERDADE)

> Cada encontro tem 2h (~1h30 úteis com iniciantes). A sequência abaixo é a ordem oficial.
> Regra de ouro: **cada dia termina com algo funcionando na tela do aluno.**

---

## Dia 1 · `01-ola-web-ola-flask` — Olá, Web! Olá, Flask!

**Gancho**: "Lembra do `streamlit run`? Hoje você descobre o que ele escondia de você."

1. Como a web funciona: navegador ↔ servidor, request/response (analogia do garçom 🧑‍🍳)
2. O que é uma URL, o que é `localhost:5000`
3. O que o Streamlit fazia por baixo dos panos (desmistificação)
4. Instalação: `pip install flask` (venv já preparado no pré-curso)
5. Primeiro app: `app.py` com `@app.route("/")` retornando string
6. `render_template("index.html")` — primeira página de verdade (template do starter kit)
7. Duas rotas (`/` e `/sobre`) — o aluno "sente" que cada URL é uma página

**Sai com**: site local com duas páginas navegáveis.
**BugZilla do dia**: esquecer de ativar o venv · `TemplateNotFound` (pasta `templates/` errada).

---

## Dia 2 · `02-formularios-jinja` — Telas que falam com Python

1. Jinja: `{{ variavel }}` — Python aparecendo no HTML
2. `{% for %}` — listar uma lista de dicts (produtos fake em memória) numa tabela
3. `{% if %}` — mostrar "estoque vazio" quando não há produtos
4. Formulário: o que é `<form>`, `action`, `method` (starter kit já tem o HTML; aluno entende, não digita)
5. GET vs POST (analogia: pedir o cardápio vs entregar o pedido)
6. `request.form["nome"]` — receber dados no Python
7. Mini-app do dia: formulário que cadastra produto **em lista na memória** + redirect

**Sai com**: tela que cadastra e lista produtos (ainda sem banco — dados somem ao reiniciar, e isso é proposital: cria a dor que o Dia 3 resolve).
**BugZilla do dia**: `Method Not Allowed` (esqueceu `methods=["GET", "POST"]`) · `KeyError` no `request.form`.

---

## Dia 3 · `03-sql-sqlite` — Banco de dados de verdade (adeus, TinyDB)

**Gancho**: "O TinyDB era um caderninho. Hoje você ganha um arquivo de aço com fichário indexado — o mesmo tipo de banco que roda em app de banco e e-commerce."

1. Por que TinyDB não basta (concorrência, volume, busca, mercado)
2. O que é um banco relacional: tabelas, colunas, linhas (analogia: planilha turbinada)
3. SQLite: banco profissional que vive num arquivo (está no seu celular agora!)
4. `CREATE TABLE produtos (id INTEGER PRIMARY KEY AUTOINCREMENT, nome TEXT, preco REAL, quantidade INTEGER)`
5. SQL no shell/DB Browser: `INSERT`, `SELECT`, `SELECT ... WHERE`, `UPDATE`, `DELETE`
6. `sqlite3` no Python: `connect`, `cursor`, `execute`, `fetchall`, `commit`
7. **Placeholders `?` SEMPRE** (mencionar SQL injection de forma leve: "nunca cole texto do usuário dentro do SQL")

**Sai com**: `loja.db` criado, produtos inseridos e consultados via Python (ainda script solto, sem Flask — foco total no SQL).
**BugZilla do dia**: esquecer `commit()` · `no such table` (caminho do .db errado).

---

## Dia 4 · `04-crud-parte-1` — A Loja ganha banco: listar + cadastrar

1. Conectar o Dia 2 com o Dia 3: trocar a lista em memória pelo SQLite
2. `banco.py` com funções: `listar_produtos()`, `cadastrar_produto(nome, preco, qtd)` (reforça funções do bootcamp)
3. Rota `/produtos` → SELECT → tabela Jinja
4. Rota `/produtos/novo` → formulário → INSERT → redirect (padrão POST-redirect-GET, explicado como "recarregou, não duplica")
5. Validação básica: nome vazio → mensagem de erro na tela

**Sai com**: Estoque e Cadastrar da Loja funcionando com banco de verdade — reinicia o servidor e os dados CONTINUAM lá (momento WOW).
**BugZilla do dia**: duplicar cadastro no F5 (sem redirect) · esquecer `?` placeholder.

---

## Dia 5 · `05-crud-parte-2` — Editar, excluir e vender

1. URL com parâmetro: `/produtos/<int:id>/editar` (analogia: número da ficha)
2. Formulário pré-preenchido (SELECT WHERE id + `value=` no template)
3. UPDATE no submit
4. Excluir com POST + confirmação simples
5. Flash messages (`flash()` + `get_flashed_messages`) — "Produto salvo! ✅"
6. **A tela Vender**: selecionar produto, informar quantidade → INSERT em `vendas` + UPDATE no estoque — a operação mais "de sistema" do curso
7. Tela Vendas: histórico + faturamento (`SELECT SUM(...)`)

**Sai com**: a Loja completa — as 4 "abas" do desafio do bootcamp, agora como sistema web com banco. Comparação lado a lado: `app_loja.py` (Streamlit) vs agora.
**BugZilla do dia**: vender mais do que tem no estoque (validação!) · editar o produto errado (id na URL).

---

## Dia 6 · `06-agentes-de-ia` — Programando com agentes (Claude Code / Codex)

**Pré-requisito pedagógico**: o aluno JÁ construiu o CRUD na mão (dias 1–5). O agente entra como acelerador, não como substituto.

1. O que é um agente de codificação (Claude Code, Codex, Gemini CLI) — terminal + IA que lê e edita seu projeto
2. Demonstração do professor: pedir uma feature pequena e ver o agente trabalhar
3. **O fluxo profissional**: especificar → gerar → LER o diff → testar → ajustar (nunca aceitar às cegas)
4. **Missão do dia: login no sistema** — o aluno escreve a especificação ("tela de login, senha com hash, proteger as rotas de produto, logout"), o agente implementa, o aluno revisa e testa
5. Entender o que o agente fez: sessão, hash de senha, decorator de proteção (explicação guiada do código gerado)
6. Agente errando de propósito: professor mostra uma geração com bug e a turma caça
7. Custos e opções: Claude Code (assinatura), Codex (ChatGPT), Gemini CLI (free tier generoso — opção padrão do aluno)

**Sai com**: Loja com login funcionando + o hábito de revisar código gerado.
**BugZilla do dia**: aceitar código sem ler · pedir "faz um sistema completo" (especificação vaga = resultado ruim).

---

## Dia 7 · `07-projeto-final` — Seu sistema, seu tema

1. Aluno escolhe o próprio tema (barbearia, brechó, petshop, oficina…) — mesmo esqueleto: 2 entidades, CRUD + operação de "movimento" (agendamento, venda, empréstimo…)
2. Checklist do projeto (mínimo: 1 CRUD completo + 1 tela de operação + login)
3. Trabalho guiado em sala: professor circula, agente de IA liberado como par
4. Regra do agente no projeto: **primeiro tenta na mão, agente destrava e acelera** (e todo código gerado tem que ser explicado pelo aluno no demo day)

**Sai com**: projeto próprio ~80% pronto.

---

## Dia 8 · `08-deploy-demo-day` — No ar + Demo Day + e agora?

1. Deploy no PythonAnywhere (ou Render) — free tier, passo a passo visual
2. Cada aluno publica o projeto e testa o link **no celular** (momento WOW final)
3. **Demo Day**: 3–5min por aluno apresentando o sistema pra turma
4. **A ponte**: limites do que construímos — e se precisar de app mobile? e se o front for de outro time? e se forem 10 devs? → separação front/back → API → **o que o mercado usa: React + Java/Spring** → convite para o curso Fullstack (com condição especial pra turma)

**Sai com**: link público do próprio sistema + clareza do próximo passo.

---

## Fora do escopo (decidido — NÃO incluir)

JavaScript · React · API REST/JSON · ORM (SQLAlchemy) · JOIN além do essencial da tela de vendas · upload de arquivos · testes automatizados · Docker · Git aprofundado (só o mínimo pro deploy, se necessário). Vários desses são "ganchos" explícitos para o curso Fullstack.
