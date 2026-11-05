# 01 · Visão geral do projeto

## O curso

**Sistemas Web com Python** — curso rápido da **programa AI**, prof. Kelson Almeida.

- **Formato**: 8 encontros presenciais/ao vivo de 2h = **16h**
- **Público**: quem sabe o básico de Python, de qualquer origem (curso independente, D24)
- **Promessa**: "saia dos scripts e construa um sistema web de verdade: com endereço na web, telas próprias e banco de dados profissional. Até o Dia 3 você aprende as peças na mão, sem IA; a partir do Dia 4, constrói dirigindo agentes de IA como um desenvolvedor."
- **Stack**: Python 3 · Flask · Jinja2 · SQLite (`sqlite3`, sem ORM) · Pico.css de partida + CSS gerado pelo agente (D15) · Claude Code / Codex / Antigravity (planos pagos) · deploy free-tier no Render, em container Docker a partir do GitHub (D21)

## O que o aluno já sabe (e o que não sabe)

| ✅ Pré-requisito | ❌ Nunca viu |
|---|---|
| variáveis, tipos, f-strings | HTTP, request/response, URLs por dentro |
| if/elif/else, loops, listas | HTML e CSS |
| funções, dicts | SQL e bancos relacionais |
| — | templates, formulários web |
| — | terminal além do básico |
| — | agentes de codificação |

**Implicação**: todo conceito web entra do zero, com analogia primeiro. Mas Python básico pode ser usado livremente sem re-explicar.

## Fio condutor: a Loja

O aluno constrói do zero uma Loja com quatro áreas:

1. 📦 **Estoque** — listar produtos
2. ➕ **Cadastrar** — inserir produto (nome, preço, quantidade)
3. 🛒 **Vender** — escolher produto, calcular total, registrar venda e baixar estoque
4. 📊 **Vendas** — histórico + faturamento total

Cada área vira uma **página com URL própria**, com **SQLite** (tabelas `produtos` e `vendas`). No Dia 7 o aluno cria a Estante do zero, por prompts, e no Dia 8 a publica.

## Virada metodológica no Dia 4

Os Dias 1–3 constroem o vocabulário necessário na mão, sem IA em sala (D24): rota Flask, template Jinja, formulário,
GET/POST e SQL com `sqlite3`. No Dia 4, quando essas peças precisam ser integradas, o curso passa
ao modo **agent-first**: o aluno escreve prompts-spec, o agente edita o projeto e o aluno lê o diff,
testa no navegador e pede correções específicas. Os códigos completos do material viram mapas de
revisão e gabaritos, não trechos para copiar.

A referência pedagógica é a fase **“Produtos: você comanda”** do Cap. 10 de
`../novo-material-fullstack/`, adaptada à Loja Flask. Não se cria o GestorPRO neste curso.

## Artefatos do curso (além do material HTML)

- **Preparo antes da aula**: seção `#preparo` do Cap 01 (Python, PyCharm e autoteste de Python básico).

## Resultado por encontro (contrato com o aluno)

Cada dia termina com algo **funcionando e demonstrável** — ver `02-conteudo-curso.md`.
