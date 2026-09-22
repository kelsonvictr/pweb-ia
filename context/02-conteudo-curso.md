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

## Dia 4 · `04-crud-parte-1` — A Loja ganha banco: você comanda o agente

**Virada do curso**: a partir daqui, todo código novo da aplicação é produzido pelo agente a partir
de prompts-spec. O aluno não copia o código completo do material: primeiro define o resultado,
depois envia o prompt, lê o diff e testa cada critério de aceite.

1. **Ponto de sincronização**: preservar o projeto antigo, criar um novo projeto `loja` vazio e
   usar um prompt único para reconstruir o checkpoint dos Dias 1–3 (Flask + templates + CSS +
   cadastro em memória + `criar_banco.py`, ainda sem integração Flask/SQLite)
2. Criar `AGENTS.md`/`CLAUDE.md`: regras permanentes da Loja (Flask + Jinja + `sqlite3`, sem ORM,
   sem JavaScript, sem bibliotecas extras, placeholders `?`, uma operação por vez)
3. Prompt 0 — pedir ao agente que leia o projeto e explique o plano, **sem editar**
4. Prompt 1 — criar `banco.py` com `listar_produtos()` e conectar a Loja ao `loja.db`
5. Prompt 2 — rota `/produtos` → SELECT → tabela Jinja
6. Prompt 3 — rota `/produtos/novo` → formulário → INSERT → redirect
7. Prompt 4 — validação de nome e preço, com mensagem na tela
8. Em cada prompt: especificar → revisar diff → testar no navegador → corrigir → registrar aceite

**Sai com**: Estoque e Cadastrar da Loja funcionando com banco de verdade — reinicia o servidor e os dados CONTINUAM lá (momento WOW).
**BugZilla do dia**: duplicar cadastro no F5 (sem redirect) · esquecer `?` placeholder.

---

## Dia 5 · `05-crud-parte-2` — Editar, excluir e vender com o agente

1. Antes de cada prompt, entender visualmente a regra e prever quais arquivos devem mudar
2. Prompt 1 — editar produto: parâmetro de URL, `SELECT WHERE id`, formulário preenchido e UPDATE
3. Prompt 2 — excluir com POST + página de confirmação
4. Prompt 3 — flash messages (`flash()` + `get_flashed_messages`)
5. Prompt 4 — **tela Vender**: INSERT em `vendas` + UPDATE no estoque como uma operação coerente
6. Prompt 5 — histórico + faturamento (`SELECT SUM(...)`)
7. Ritual obrigatório após cada geração: escopo do diff, regras SQL, teste feliz, teste de erro e explicação oral

**Sai com**: a Loja completa — as 4 "abas" do desafio do bootcamp, agora como sistema web com banco. Comparação lado a lado: `app_loja.py` (Streamlit) vs agora.
**BugZilla do dia**: vender mais do que tem no estoque (validação!) · editar o produto errado (id na URL).

---

## Dia 2½ · `02b-ia-agentes` — IA & Agentes: seu par de programação (leitura em casa, sem encontro)

Capítulo teórico entre o Dia 2 e o Dia 3 (D15), adaptado do cap 09 do fullstack: LLM = próxima palavra · janela de contexto & alucinação · do chat ao agente (loop com ferramentas) · mercado (Claude Code ⭐ / Codex / Antigravity — planos pagos) · instalação no Terminal do PyCharm + primeiro "oi" · prompt = mini-espec (CONTEXTO/TAREFA/RESTRIÇÕES/ACEITE) · ritual de revisão ①–⑤ · escada do curso · BugZilla dos 5 clássicos.

**A progressão revisada (D16)**:
- Dia 3: **tutor** do SQL escrito pelo aluno + primeira tarefa visual (CSS)
- Dia 4: **virada agent-first** — todo o CRUD integrado nasce de prompts-spec; o aluno comanda
- Dia 5: **sequência de entregas** — um prompt por operação, nunca “faça o resto da Loja”
- Dia 6: **feature maior** — login inteiro, ainda dividido em plano, implementação e testes; fecha com o prompt de acabamento visual
- Dias 7–8: projeto e deploy no mesmo fluxo; todo código gerado precisa ser explicado

---

## Dia 6 · `06-agentes-de-ia` — Login com agentes: uma feature maior

**Pré-requisito pedagógico**: o aluno já aprendeu manualmente as peças fundamentais (Flask, Jinja,
formulários e SQL) e construiu o CRUD da Loja por prompts nos Dias 4–5. Hoje ele sobe de várias
operações pequenas para uma feature maior, sem abandonar o ritual de revisão.

1. **Abre no estado do Dia 5**: a Loja está completa e *sem porta* — `/produtos/3/excluir`
   responde pra qualquer um. A dor antes do remédio; o Dia 8 (URL pública) é o prazo
2. ⭐ **Simulador do bolso da sessão**: mesma `session` do `flash()` do Dia 5, agora guardando
   o usuário — liga/desliga o cadeado, entra, sai, e vê o 302 do `@login_required`
3. Retomada de 1 minuto do contrato dos Dias 4–5 (fluxo + regra de ouro) — **sem reapresentar
   agentes como novidade** — e o bloco do `CLAUDE.md`: restrição repetida vira regra permanente
4. Prompt 0 — ler o projeto e dividir o login em três entregas, **sem editar**
5. Prompt 1 — tabela `usuarios`, hash e função de busca; homologar o banco isoladamente
6. Prompt 2 — `/login`, `/logout` e sessão; homologar entrar, falhar e sair
7. ⭐ **Caça ao bug no diff, DEPOIS do Prompt 2** (não antes: seria spoiler do aceite) — diff que
   roda sem erro e impede qualquer login; o aluno treina e volta pro diff dele
8. Prompt 3 — `login_required` e menu por estado; homologar todas as rotas protegidas
9. Prompt 4 — auditoria final sem edição, procurando senha pura, SQL inseguro e decorator fora de ordem
10. Entender o código gerado: sessão, hash e a ordem `@app.route` acima de `@login_required`
11. 🎨 **A dívida visual** (Parte 4) — o `static/style.css` nasceu no Dia 3, quando a Loja tinha
    duas telas; editar/excluir/vender/vendas/login vieram depois e estão cruas. ⭐ simulador
    antes/depois + **Prompt 5**, cujo aceite é conferível sem entender CSS: *"no diff, nenhum
    arquivo .py e nenhum .html foi tocado"*

12. **Lição de casa única** (substituiu a Arena, removida do Dia 6 em diante): escrever por
    escrito a espec do projeto do Dia 7 — 2 entidades com colunas e tipos, a operação de
    movimento e **três linhas sobre o visual** (item novo, consequência da Parte 4). O Dia 7
    depende disso e referencia explicitamente

**Sai com**: Loja com login funcionando, visualmente coerente + o hábito de revisar código gerado.
**BugZilla do dia**: aceitar código sem ler · espec vaga · **o que o agente RODA não aparece no
diff** (caso real da turma: scripts de teste do agente apagando e repovoando a tabela `produtos`
no `loja.db` ao vivo → a restrição virou linha no `CLAUDE.md`).

---

## Dia 7 · `07-projeto-final` — Seu sistema, seu tema

1. Aluno escolhe o próprio tema (barbearia, brechó, petshop, oficina…) — mesmo esqueleto: 2 entidades, CRUD + operação de "movimento" (agendamento, venda, empréstimo…)
2. Checklist do projeto (mínimo: 1 CRUD completo + 1 tela de operação + login)
3. Novo projeto vazio; Prompt 0 transforma a folha aprovada em plano sem editar
4. Prompt 1 cria somente fundação, instruções persistentes, tabelas, home e CSS
5. Esteira explícita: listar → cadastrar → editar → excluir → segunda entidade → movimento → histórico → login
6. Uma catraca entre prompts exige diff restrito, teste feliz, teste de erro, persistência e explicação oral
7. Regra do projeto: **primeiro especifique; o agente implementa; você revisa, testa e explica**

**Sai com**: projeto próprio ~80% pronto.

---

## Dia 8 · `08-deploy-demo-day` — No ar + Demo Day + e agora?

1. Prompt 0 — auditoria de prontidão sem edição: `__main__`, secret key, requirements, caminhos, banco e sintaxe
2. Prompt 1 — corrigir somente bloqueadores aprovados; diff pequeno + homologação local
3. Pacote completo: Python, `requirements.txt`, `templates/` e `static/`; sem venv, cache ou `.db` local
4. Deploy no PythonAnywhere (ou Render) — free tier, passo a passo visual
5. Prompt 2 — diagnóstico por evidência quando a nuvem falhar: log + caminhos + WSGI, sem editar primeiro
6. Cada aluno publica o projeto e testa o link **no celular** (momento WOW final)
7. **Demo Day**: 3–5min por aluno mostrando critério de aceite, diff e código explicado
8. **A ponte**: limites do que construímos — e se precisar de app mobile? e se o front for de outro time? e se forem 10 devs? → separação front/back → API → **o que o mercado usa: React + Java/Spring** → convite para o curso Fullstack (com condição especial pra turma)

**Sai com**: link público do próprio sistema + clareza do próximo passo.

---

## Fora do escopo (decidido — NÃO incluir)

JavaScript · React · API REST/JSON · ORM (SQLAlchemy) · JOIN além do essencial da tela de vendas · upload de arquivos · testes automatizados · Docker · Git aprofundado (só o mínimo pro deploy, se necessário). Vários desses são "ganchos" explícitos para o curso Fullstack.
