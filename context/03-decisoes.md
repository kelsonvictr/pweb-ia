# 03 · Decisões estratégicas e pedagógicas

> Registrar aqui toda decisão estrutural nova, com data e justificativa.

## D1 · Flask, não Django nem FastAPI (2026-07-22)

- **Django** entrega admin, ORM e auth prontos — o aluno sairia com sensação de "framework completo, pra que o curso Fullstack?". Django **compete** com o fullstack; Flask **aponta** pra ele. Além disso, a "mágica" do Django esconde conceitos que queremos expor (HTTP, SQL).
- **FastAPI** é API-first, sem telinha — API REST é território do curso Fullstack e fica como gancho final.
- **Flask** é legível linha a linha pra quem só sabe Python básico e conta a história certa: "o Streamlit por dentro".

## D2 · SQL na mão com `sqlite3`, SEM ORM (2026-07-22)

Espaço vazio entre os cursos: bootcamp usa TinyDB (sem SQL), fullstack usa Spring Data JPA (SQL escondido). Ensinar SQL explícito é o diferencial técnico deste curso, não canibaliza ninguém e **melhora** o aluno que seguir pro fullstack. Placeholders `?` obrigatórios desde o primeiro INSERT.

## D3 · Anti-canibalização do curso Fullstack (2026-07-22)

O medo comercial: aluno faz este curso e desiste do Fullstack (React + Java/Spring). Mitigação por design:

1. **Posicionamento de esteira, não de alternativa**: bootcamp ("aprenda a programar") → este curso ("faça seu primeiro sistema de verdade") → fullstack ("programe como o mercado contrata").
2. **Zero JavaScript/React/API** no conteúdo. Frontend vem pronto (Pico.css no starter kit).
3. **Dia 8 termina com ponte explícita**: limites do monólito server-rendered → o que aparece nas vagas → convite com condição especial pra turma.
4. **Tese**: quem compraria só o curso rápido não compraria o fullstack de qualquer jeito; quem faz e gosta converte melhor. É funil, não concorrente.

## D4 · Agentes de IA entram no Dia 6, não antes (2026-07-22 · superada por D15 e D16)

O aluno precisa construir o CRUD na mão primeiro (dias 1–5) para conseguir **avaliar** o que o agente gera. O caso de uso do agente é o **login** (sessão + hash) — feature real, valiosa, e que deixou de ser aula manual (economiza um encontro inteiro). O que se ensina é o fluxo: especificar → gerar → ler o diff → testar. No projeto final, código gerado por agente tem que ser explicado pelo aluno no demo day.

Pragmática de custo: professor demonstra com Claude Code; aluno usa Gemini CLI (free tier) como padrão, Claude Code/Codex para quem tiver assinatura. O fluxo de trabalho ensinado é o mesmo.

## D5 · Fio condutor = Loja/Vendas do desafio final do bootcamp (2026-07-22)

Escolha do professor (vs lanchonete/cinema): reconstruir o `app_loja.py` (Streamlit + TinyDB, 4 abas) como sistema web. Vantagens: o aluno já conhece o domínio (zero tempo explicando requisitos), a comparação antes/depois é visceral, e a narrativa de evolução vende o curso sozinha.

## D6 · Formato 8×2h (2026-07-22)

12h (6 dias) foi considerado apertado; 8 encontros dão aula dedicada de SQL (dia 3) e demo day (dia 8). Encontros são prática guiada; o material HTML auto-contido cobre quem faltar/ficar pra trás.

## D7 · Design system herdado da v2 (2026-07-22)

`shared/` copiado de `../programacao-iniciantes-v2/shared/` (com a correção de ligatures incluída). Mesma identidade visual = aluno se sente em casa. Evoluções de CSS específicas deste curso entram em `shared/components.css` local, marcadas com comentário `/* SWP */`.

## D8 · Capítulo 00 — página de venda (2026-07-22)

`capitulos/00-apresentacao/` é um **pitch interativo**, não aula: dor (chat "não tem link") → virada (chat com link público) → fluxo request/response animado → antes/depois da Loja → agentes de IA (terminal Claude Code) → timeline dos 8 dias → trilha "você está aqui" → oferta (**R$ 499,99 · até 12x no cartão · 8 dias de 2h**) com escassez ("turma única · vagas limitadas") e CTA presencial (matrícula com o professor ao vivo). Card destacado no hub aponta pra ele. Componentes novos ficaram no `<style>` da própria página com prefixo `swp-` (chat animado, browser mockup, timeline, oferta) — promover pro `shared/components.css` se forem reutilizados em capítulos.

## D9 · Cards de divulgação Instagram/WhatsApp (2026-07-27)

`divulgacao/cards.html` — gerador de cards estáticos no **mesmo estilo aprovado do Java Avançado**
(receita completa em `../java-avancado/.specs/09-divulgacao-cards.md`): P&B + **1 acento = amarelo
Python `#ffd43b`** (no Java era laranja), Nunito 900 gigante, JetBrains Mono nos rótulos (ligatures
OFF), grade fina + vinhetas, foto recortada valorizada, badge "📍 Presencial / aulas ao vivo".

- **Uso**: `cards.html?s=1..8&fmt=feed|story`. Render por headless Chrome 2× (comando na spec do
  Java; `--window-size=1080,1350` feed · `1080,1920` story). Saída versionada em
  `assets/divulgacao/feed-4x5/` e `story-9x16/`.
- **8 slides**: capa (foto colorida `cut-kelson-python.png` — recorte rembg da foto com a plaquinha
  Python) · "Sem link, seu sistema não existe" (`cut-prof3`) · mock navegador da Loja ·
  SQLite/SQL (logo SQLite370 invertido p/ branco — o colorido some no fundo escuro) · agentes de IA
  (mascote `claudecode.png` + fluxo especificar→gerar→revisar→testar) · pra quem é (ponte bootcamp,
  fundo `prof4.png`) · professor (`cut-prof2`) · CTA "turma única · vagas limitadas".
- **Sem preço nos cards** (mesma decisão do Java); a oferta R$ 499,99 vive no cap. 00.
- Assets copiados do java-avancado: `logo-full.svg`, `claude.svg`, `claudecode.png`, `cut-prof2/3.png`,
  `prof4.png`. Novos: `python.svg`, `flask.svg` (mono branco), `sqlite.svg` (SQLite370),
  `sqlite-mono.svg` (glifo simple-icons, usado no chip da capa).

## D10 · Capítulo 01 — fundamentos web no próprio capítulo, sem starter kit (2026-08-14)

Decisão do professor ao escrever o cap 01:

1. **Fundamentos de HTML/CSS/JS entram no Dia 1**, num ato próprio ("As linguagens do navegador"),
   ANTES do Flask: HTML ensinado de verdade (tags, aninhamento, esqueleto — o aluno digita uma
   página na mão), CSS conceitual + Pico.css via CDN (uma linha de `<link>`), e JavaScript apenas
   APRESENTADO como "a terceira linguagem, território do curso Fullstack" — sem uma linha de código
   JS, preservando a D3 (anti-canibalização).
2. **Sem starter kit no Dia 1**: o aluno cria `loja/`, `app.py` e `templates/*.html` do zero.
   Entender cada linha que digita vale mais que ganhar telas prontas — e casa com o ato de HTML.
   O starter kit (base.html + Pico) fica para quando as telas crescerem (dia 2+).
3. **Reuso de componentes**: em vez de promover o `.swp-browser` do cap 00, o cap 01 usa o
   **mini-browser portado do fullstack** (`.mini-browser`/`.mb-chrome` em `shared/components.css`
   + motor `buildMiniPreview` em `shared/scripts.js`, ambos marcados `/* SWP */`). Também entraram
   no shared: `motion-fx.js` (cópia do fullstack), badges `lang-badge.html/.css/.bash`, tokens de
   syntax HTML/CSS (`.tag .atr .sel .prop .val .unit .punc`), `.fp-paint` da forja e
   `.next-chapter`/`.btn-next`.
4. **Máquinas didáticas do cap 01** (todas vanilla, autoplay via IntersectionObserver, respeitam
   `prefers-reduced-motion`): Pedido ao Vivo (request/response com botão de desligar o servidor →
   ERR_CONNECTION_REFUSED), Anatomia da URL (2 instâncias clicáveis), Raio-X do Streamlit
   (data-seq), Forja de Tags (tag-forge.js), rastreador do app.py linha a linha (data-seq) e
   roteador "Cada URL é uma página" (com 404 do /contato que vira exercício solo).

## D11 · Capítulos 02–04 — ajustes de ementa ao escrever (2026-08-14)

1. **Aluno digita o HTML novo do Dia 2 na mão** (form ~8 linhas, tabela ~10): a ementa previa
   "starter kit já tem o HTML; aluno entende, não digita" — mas pela D10 não há starter kit e o
   aluno aprendeu HTML no cap 01. Digitar reforça.
2. **`{% extends %}`/base.html entrou no cap 02** (seção compacta "o remédio prometido"): cumpre
   o spoiler plantado na arena do cap 01 (menu duplicado 4×) e prepara as telas do CRUD. A ementa
   oficial do Dia 2 não listava extends; custo ~15min de aula.
3. **Dia 3 é Python-first**: o caminho principal do SQL é o `sqlite3` em scripts; o DB Browser
   for SQLite entrou como "espião" opcional (ver o arquivo por dentro), não como ferramenta de aula.
4. **Jinja com `p["chave"]` no dia 2 e `p[0]`/`p[1]` no dia 4**: dicts em memória usam a sintaxe
   de chave igual ao Python do bootcamp; quando o fetchall chega (dia 4), o material explica a
   virada dict→tupla explicitamente (é pergunta de quiz nos dois capítulos).
5. **Máquinas dos caps 02–04** (todas vanilla, IntersectionObserver, prefers-reduced-motion):
   - Cap 02: Fábrica de Páginas ({{ }} preenchidas ao vivo, troca de dados), linha de produção
     do {% for %}, GET vs POST (cartão-postal/envelope lacrado), A Volta Completa (form real →
     POST → append → redirect → tabela) e O Apagão (CTRL+C evapora a lista — gancho do dia 3).
   - Cap 03: anatomia clicável do CREATE TABLE, Simulador SQL (5 verbos animando a tabela),
     Rascunho e Carimbo (execute vs commit, com final 😈 sem commit), demo de SQL injection.
   - Cap 04: A Loja por dentro (request pelas 4 camadas, caminhos listar/cadastrar), O Apagão
     parte 2 (dados sobrevivem — espelho proposital do cap 02) e O F5 duplicador (PRG, com o
     diálogo de reenvio do navegador simulado).
6. **`shared/` ganhou** (blocos `/* SWP */`): badges `lang-badge.jinja/.sql`, tokens `.jvar`/
   `.jtag`, e `.swp-data-table` com estados animados (row-new/row-del/cell-hot/row-match/row-dim)
   usados pelos três capítulos.

## D12 · PyCharm-first em todo o material (2026-08-14)

A turma vem do bootcamp **Programação para Iniciantes feito 100% no PyCharm** — eles já têm o
hábito de New Project (que cria o venv sozinho), ▶ Run e Terminal embutido. O material foi
convertido para esse fluxo, eliminando o atrito de aprender ferramenta nova junto com Flask/SQL:

- **Ambiente**: nada de `python -m venv` / `source venv/bin/activate`. O aluno faz
  `File → New Project…` (nome `loja` no dia 1, `treino-sql` no dia 3) e o PyCharm entrega o venv
  pronto e ativado. O único comando de terminal do curso é `pip install flask`, no
  **Terminal do PyCharm** (`Alt+F12`), onde o `(venv)` já aparece sozinho.
- **Rodar/parar**: ▶ Run (botão direito → `Run '…'`) e ⏹ Stop, em vez de `python app.py` + CTRL+C.
  Vale também pros scripts SQL do dia 3 (▶ em cada arquivo), igual ao bootcamp. A saída é a
  **janela Run** — e o material aproveita que o PyCharm transforma `http://127.0.0.1:5000` em
  link clicável.
- **Impacto nas encenações**: o apagão (dia 2) e o teste de persistência (dia 4) agora são
  "⏹ e depois ▶"; os widgets e o texto foram ajustados (`^C` virou `⏹ Process finished`).
- **Arquivos e pastas**: `New → File` / `New → Python File` / `New → Directory` pelo botão direito;
  HTML aberto pelos ícones de navegador no canto do editor (não mais "duplo clique no arquivo").
- **BugZillas reescritos para causas de PyCharm**:
  - `ModuleNotFoundError: No module named 'flask'` → instalou num terminal do sistema (sem
    `(venv)`) ou o interpretador do projeto está errado (`Settings → Project → Python Interpreter`).
  - `Address already in use` → aba antiga da janela Run ainda rodando.
  - `no such table` → script rodando de outra pasta criou um segundo `.db`; diagnóstico agora é
    "procure `.db` duplicado na árvore de arquivos" (o caminho completo sai no topo da janela Run).
- O terminal cru **permanece** só onde é historicamente fiel: o raio-X do `streamlit run` no cap 01.
- O **guia do professor** (`guia-professor/`, fora do git) foi convertido junto e ganhou uma seção
  "Cola do PyCharm" com os atalhos e os dois tropeços mais comuns da turma.

## D13 · Capítulos 05–08 — decisões dos capítulos finais (2026-08-25)

**Cap 05 (CRUD parte 2 + Vender):**
- Exclusão SEMPRE por **página de confirmação + POST** (a "história do robô que clicou em
  todos os links"); nada de `onclick="confirm()"` — JS continua fora (D3).
- `app.secret_key` é introduzido junto do `flash()` ("a assinatura dos bilhetes"), plantando
  a palavra *sessão* que o login do dia 6 colhe.
- **JOIN essencial sem alias** (`FROM vendas JOIN produtos ON produtos.id = vendas.produto_id`)
  — nomes completos para leitura de iniciante; a única dose de JOIN do curso.
- Total da venda calculado NO SERVIDOR (`qtd * produto[2]`) — regra "o cliente escolhe, o
  servidor calcula e confere".
- GROUP BY aparece só como desafio lv3 da arena (aperitivo, não conteúdo).

**Cap 06 (agentes):**
- **Pré-encontro obrigatório** no topo do capítulo (Node LTS + `npm install -g
  @google/gemini-cli` + login Google, no Terminal do PyCharm) — avisado também no resumo do
  cap 05. Fallback: dupla em sala.
- O bug plantado da "caça ao bug no diff" é `senha == usuario[2]` (comparação com hash sem
  `check_password_hash`) — código que roda sem erro e falha funcionalmente, o arquétipo do
  bug de agente.
- A "espec boa" do login é o texto literal que o aluno cola; ela vira o checklist de
  aceitação interativo da missão.
- Decorators ganham dose mínima ("etiqueta que envolve a função, prima do @app.route") —
  ler, não escrever.

**Cap 07 (projeto final):** formato workshop (~60% do tamanho), SEM arena (o projeto é a
arena). Fórmula pública: **2 entidades + 1 operação de movimento**. Checklist de 8 itens com
localStorage. Regra do agente reafirmada: na mão primeiro; código gerado é explicado no
demo day.

**Cap 08 (deploy):**
- Plataforma: **PythonAnywhere free** (já era a URL da narrativa do cap 00); Render citado
  como alternativa com Git. **Manual configuration** de propósito (o atalho Flask esconderia
  o que o aluno entende).
- `if __name__ == "__main__":` é ensinado AQUI (dose: "um if, dois mundos" — ▶ local roda
  app.run; o WSGI importa e a plataforma liga).
- **Working directory** apresentado como o remédio do `no such table` em produção (callback
  do bug do Dia 3). Zip SEM venv e sem .db; criar_banco.py roda no console Bash da nuvem.
- REST/JSON são NOMEADOS apenas na máquina "A evolução" (monólito → front/back), como
  território do fullstack (D3 cumprida até o fim).
- Chat do cap 00 refeito com final feliz no "momento do celular".

## D14 · Cap 02 realinhado ao código que a turma digitou em sala (2026-09-01)

O professor deu o Dia 2 com um desenho de rotas diferente do material original (que fazia tudo
na `/` com `methods=["GET","POST"]` + `if request.method`). O material foi reescrito para
bater com o que a turma viu, porque o aluno não pode achar que digitou errado:

- **Rotas com papéis separados**: `/produtos` (lista), `/cadastro_produto` (mostra o form) e
  `/cadastro` (só `methods=["POST"]`, recebe e faz `redirect("/produtos")`). A home volta a
  ser cartão de visita (o `<ul>` fixo do Dia 1 sai; entra link pra `/produtos`).
- **`lista_de_produtos` global no topo do `app.py`**, com `append` na rota `/cadastro`. Em
  sala a lista era local e o cadastro só fazia `print` — isso matava "A Volta Completa", o
  "Apagão" e o gancho do cap 04 ("Apagão parte 2"). O `print` ficou como passo intermediário
  didático ("prove que chegou, depois guarde"). Nome `lista_de_produtos` ≠ função
  `produtos()` — o box explica o porquê (mesma lição do `ver_promocoes` da arena).
- **`request.method` sai do cap 02** e passa a ser apresentado no cap 04, quando
  `/cadastro_produto` + `/cadastro` viram `/produtos/novo` (GET+POST). Cap 02 deixa o
  spoiler; cap 04 ("A página /produtos/novo" e "Compare com o Dia 2") explica a fusão.
- **`url_for` não entra no código do material** (caps 02–05 usam `redirect("/produtos")`);
  há um box no cap 02 dizendo que `redirect(url_for("produtos"))` é equivalente, para quem
  viu na aula.
- BugZilla ganhou o 405 "ao contrário" (abrir `/cadastro` na barra = GET numa rota só-POST),
  que é o erro mais provável nesse desenho. Corrigida também a afirmação de que chave
  ausente no dict dá `UndefinedError` — no Flask padrão a célula fica vazia, sem erro.
- Guia do professor (dia 2) e gabarito `guia-professor/codigo/dia-02` sincronizados
  (gabarito = versão 2, arena inteira). Produtos de exemplo continuam Fone/Teclado/Mouse
  (em sala eram Logitech) — box "seus produtos podem ser outros; o que bate é a estrutura".

## D15 · Agentes de IA desde o Dia 3, em escada — e capítulo 02½ de teoria (2026-09-01 · progressão superada por D16)

Revisão da D4 a pedido do professor, com a turma em andamento: os agentes deixam de ser
"só no Dia 6" e entram **um degrau por dia**, sempre DEPOIS da versão na mão do que o agente
vai tocar (o aluno precisa do gabarito mental pra revisar — o argumento da D4 continua valendo,
só muda a dose):

| Dia | Papel do agente | Onde |
|---|---|---|
| 02½ | instalar + entender (leitura em casa) | `capitulos/02b-ia-agentes/` (NOVO) |
| 3 | **tutor** do SQL que o aluno escreveu + **1ª tarefa gerada: CSS moderno da Loja** (`static/style.css`) | cap 03, Parte 5 (`#agente-tutor`, `#agente-css`) + missão bônus na arena (popular.py) |
| 4 | **revisor** do app.py/banco.py, com triagem em 3 gavetas | cap 04, Parte 3 (`#agente-revisor`) |
| 5 | **par**: editar na mão, **excluir gerado** a partir de espec + checklist | cap 05, seção `#excluir` reescrita |
| 6 | **você comanda**: login inteiro (como já era) | cap 06 (pré-encontro vira checagem; aquecimento reescrito) |
| 7–8 | projeto + CLAUDE.md/AGENTS.md + Demo Day explicando o gerado | inalterados |

Decisões travadas:
- **Cap 02½ (`02b-ia-agentes`)** é a "super aula" teórica do fullstack (cap 09) adaptada a Flask:
  5 máquinas portadas (🔮 Próxima Palavra com `@login_required` como pegadinha, 📦 Mesa de
  Contexto com a regra "sem JavaScript", 🔁 Loop do Agente com o link Cancelar em
  `cadastro_produto.html`, ⚖️ Vago×Espec com o rodapé no base.html, 🕵️ Caça ao Intruso com
  `pip` clandestino + `<script>` + bloco renomeado `conteudo→content`), mercado, instalação,
  prompt = mini-espec (4 ingredientes), ritual ①–⑤, escada do curso, BugZilla dos 5 clássicos.
  **Não ganha encontro próprio**: é leitura + instalação em casa entre o Dia 2 e o Dia 3
  (o curso continua 8×2h). Hub: card "DIA · 02½ · leitura em casa" (classe `c09`).
- **Ferramentas: só planos pagos** — Claude Code (Claude Pro, o do professor, no Terminal do
  PyCharm), Codex (ChatGPT Plus) e Antigravity CLI `agy` (Google AI Pro). Gemini CLI saiu
  (substituído pelo Antigravity, conforme o material fullstack). Sem opção gratuita.
- **CSS via agente no Dia 3** é a primeira tarefa gerada por ser visual (fácil de revisar, sem
  risco pros dados). A espec do material traz o conceito `static/` do Flask e a lista explícita
  de "cara de IA" a evitar (gradiente roxo, sombra gigante, emoji, borda exagerada). Isso
  atualiza a premissa "HTML/CSS vem pronto no Pico" do CLAUDE.md: o Pico é o ponto de partida;
  o visual final é gerado pelo agente a partir da espec do aluno — continua sem JS/React (D3).
- Cap 06 mantém as máquinas e a missão do login; muda só o enquadramento (degrau 4), o
  pré-encontro (checagem) e a tabela de ferramentas.

## D16 · Do Dia 4 em diante, desenvolvimento agent-first (2026-09-04)

Decisão do professor: a Loja continua sendo o fio condutor — **GestorPRO não entra neste curso**.
O Cap. 10 de `novo-material-fullstack` é referência apenas para o modo de trabalho usado na fase
“Produtos: você comanda”. A partir da integração Flask + SQLite do Dia 4, todo código novo da
aplicação é solicitado ao agente por prompts-spec.

### D17 · Dia 4 vira checkpoint comum com projeto novo (2026-09-04)

Decisão do professor: o Dia 4 não depende mais da qualidade ou da versão do projeto que cada aluno
traz dos encontros anteriores. A primeira atividade preserva o projeto antigo, cria uma pasta
`loja` nova e vazia e entrega ao agente um prompt completo para reconstruir o estado final dos
Dias 1–3. Esse estado inclui Flask, cinco páginas, cadastro/listagem em memória, herança Jinja,
CSS local e `criar_banco.py`, mas **proíbe integrar o Flask ao SQLite**. A perda dos produtos após
reiniciar continua intencional e comprova que o aluno parou no checkpoint correto. Só depois da
homologação desse ponto comum começam os prompts pequenos de integração e CRUD do próprio Dia 4.

Isso substitui a escada antiga “revisor no Dia 4 → par no Dia 5 → comanda no Dia 6”. O aluno já
construiu manualmente, nos Dias 1–3, o repertório mínimo para especificar e revisar: rotas,
templates, formulários, GET/POST, SQL, placeholders, `commit` e `fetchall`. O novo contrato é:

1. entender a operação e prever entrada, mudança no banco e saída;
2. escrever/enviar um prompt com contexto, tarefa, restrições e aceite;
3. deixar o agente editar os arquivos;
4. ler o diff antes de aceitar;
5. testar caminho feliz e erro esperado;
6. pedir uma correção específica quando necessário;
7. explicar oralmente o que entrou.

Regras de produção dos capítulos:

- código completo continua visível, mas como **mapa de revisão/gabarito**, nunca como primeira ação;
- cada operação recebe seu próprio prompt; proibir pedidos vagos como “faça o CRUD completo”;
- `AGENTS.md` e/ou `CLAUDE.md` da Loja são escritos no começo do Dia 4;
- a teoria vem antes do prompt, para o aluno saber o que exigir;
- checklists de aceite são executáveis no navegador e incluem pelo menos um caso de erro;
- o agente pode variar nomes e organização superficial; as regras técnicas e o comportamento são
  inegociáveis;
- Dias 7–8 mantêm a exigência do Demo Day: todo trecho gerado deve ser explicado pelo aluno.
