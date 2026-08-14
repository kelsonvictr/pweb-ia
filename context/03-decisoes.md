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

## D4 · Agentes de IA entram no Dia 6, não antes (2026-07-22)

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
