# 01 · Visão geral do projeto

## O curso

**Sistemas Web com Python** — curso rápido da **programa AI**, prof. Kelson Almeida.

- **Formato**: 8 encontros presenciais/ao vivo de 2h = **16h**
- **Público**: egressos do bootcamp **Programação para Iniciantes** (`../../programacao-iniciantes-v2/`)
- **Promessa**: "o mesmo sistema de loja que você fez no bootcamp — agora de verdade: com endereço na web, telas próprias e banco de dados profissional. E você ainda aprende a programar com agentes de IA."
- **Stack**: Python 3 · Flask · Jinja2 · SQLite (`sqlite3`, sem ORM) · Pico.css (pronto no starter kit) · Claude Code / Codex / Gemini CLI · deploy free-tier (PythonAnywhere ou Render)

## O que o aluno já sabe (e o que não sabe)

| ✅ Já viu no bootcamp | ❌ Nunca viu |
|---|---|
| variáveis, tipos, f-strings | HTTP, request/response, URLs por dentro |
| if/elif/else, loops, listas | HTML e CSS (Streamlit escondia tudo) |
| funções, dicts, JSON | SQL e bancos relacionais |
| TinyDB (CRUD em arquivo) | templates, formulários web |
| Streamlit (UI sem HTML) | terminal além de `streamlit run` |
| — | agentes de codificação |

**Implicação**: todo conceito web entra do zero, com analogia primeiro. Mas Python básico pode ser usado livremente sem re-explicar.

## Fio condutor: a Loja, versão web

No desafio final do bootcamp (cap 10, seção `#desafio-final`), o aluno construiu `app_loja.py` em Streamlit + TinyDB com 4 abas:

1. 📦 **Estoque** — listar produtos
2. ➕ **Cadastrar** — inserir produto (nome, preço, quantidade)
3. 🛒 **Vender** — escolher produto, calcular total, registrar venda e baixar estoque
4. 📊 **Vendas** — histórico + faturamento total

Este curso **reconstrói exatamente esse sistema** como app web de verdade: cada aba vira uma **página com URL própria**, TinyDB vira **SQLite** (tabelas `produtos` e `vendas`), e no fim o sistema vai pro ar com link público. No dia 7 o aluno cria um sistema com **tema próprio** usando a mesma receita.

## Artefatos do curso (além do material HTML)

- **Starter kit** (repositório à parte, a criar): projeto Flask com `templates/base.html` + Pico.css prontos, pasta `static/`, `banco.py` vazio. O aluno **não digita HTML estrutural** — só Python, Jinja e SQL.
- **Guia de instalação** (pré-curso): Python + venv + Flask + editor. Deve ser feito ANTES do dia 1 ou nos primeiros 20min.

## Resultado por encontro (contrato com o aluno)

Cada dia termina com algo **funcionando e demonstrável** — ver `02-conteudo-curso.md`.
