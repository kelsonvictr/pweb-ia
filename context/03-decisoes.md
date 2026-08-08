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
