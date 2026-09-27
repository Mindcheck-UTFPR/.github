# Architecture Decision Records

Um ADR registra uma escolha cara de desfazer. Uma página, escrita no dia da decisão. Semana da entrega não depende da memória de ninguém.

Não use ADR para premissa já fechada (React, Express, PostgreSQL no MVP). Use quando havia alternativas reais — por exemplo modelagem, persistência, autenticação ou estratégia de pontuação.

## Modelo

```markdown
# ADR-00X — título curto

Data: AAAA-MM-DD
Status: proposta | aceita | substituída por ADR-00Y
Issue: MIND-XXX

## Contexto
O que era verdade quando decidimos: prazo, requisito, restrição, equipe.

## Decisão
Uma frase no presente: usamos X para Y.

## Alternativas consideradas
- Opção A — por que não.
- Opção B — por que não.

## Consequências assumidas
O que aceitamos perder e o que fica difícil de mudar depois.
```

A IA pode listar alternativas e trade-offs. Só o time assina a decisão. “Foi o que a IA sugeriu” não é contexto.
