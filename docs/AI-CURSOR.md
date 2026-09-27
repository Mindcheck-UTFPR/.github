# Engenharia com IA no Cursor

 A IA do Cursor é ferramenta de engenharia, não autora do produto. Ela orquestra código a partir de uma especificação rastreável.

Este repositório (`.github`) é a **única fonte de treinamento** da IA. Frontend e backend não copiam o processo: eles apontam para cá.

## Como frontend e backend apontam para cá

Os três repositórios devem ficar clones irmãos:

```text
mindCheck/
  .github/     ← treinamento (docs + .cursor/rules)
  frontend/    ← só ponteiro + código da interface
  backend/     ← só ponteiro + código da API
```

No Cursor, abra `mindcheck.code-workspace` para indexar as três pastas. Assim a IA lê este repositório enquanto edita frontend ou backend.

Cada repo de código tem:

- `.cursor/rules/org-github.mdc` — manda ler `../.github/docs/`
- `AGENTS.md` — o mesmo ponteiro, no formato que o Cursor carrega sozinho

Não coloque o processo completo de novo em frontend/backend. Se algo mudar, mude aqui.

## Prompt-mãe

Todo pedido de código nasce de um trecho da issue `MIND-*`, deste repositório e do PRD em [PRODUCT.md](PRODUCT.md). Issue vaga → prompt vago → código errado com confiança.

Antes de gerar código, a IA deve restabelecer:

1. problema e público, sem vender tecnologia;
2. o que entra e o que fica fora desta issue;
3. critérios de aceite testáveis;
4. repositório certo (`frontend`, `backend` ou `.github`);
5. restrições da stack e da LGPD.

## Anatomia de um pedido que funciona

| Elemento | Pergunta | Exemplo Mindcheck |
| --- | --- | --- |
| Contexto | Onde isso vive? | backend Express + Prisma; issue `MIND-25`; pontuação no servidor |
| Tarefa | O que fazer agora? | calcular faixa da versão publicada do questionário |
| Restrições | O que não pode? | sem diagnóstico; sem log de respostas; sem pontuar no frontend |
| Formato | Como devolver? | arquivos no módulo `scoring`, com teste de exemplo |
| Aceite | Quando está pronto? | soma determinística; faixa da versão; critério da issue marcado |

Não peça o app inteiro. Não aceite a primeira resposta sem ler nem testar. Não cole senha, token ou `.env` no chat. Não pergunte “qual é o melhor?” para arquitetura: peça 2–3 alternativas com consequências neste contexto.

## Ordem de trabalho da IA

1. Ler a issue, `PRODUCT.md`, `ARCHITECTURE.md` e o código já existente no repositório certo.
2. Se a mudança for cara de desfazer, rascunhar um ADR em `docs/adr/` e parar para o time assinar.
3. Implementar só a issue. Não misturar frontend e backend sem necessidade, nem duas issues na mesma branch.
4. Cobrir estados reais: vazio, carregando, erro, dado em cache, conteúdo extremo e permissão negada.
5. Criar ou atualizar testes proporcionais ao risco. Rodar as verificações do repositório.
6. Atualizar documentação afetada. Preparar o PR com título `MIND-123: descrição` e o corpo de [PULL-REQUESTS.md](PULL-REQUESTS.md).

## Interface

Telas existem por causa de requisito. Toda tela precisa responder “qual RF/issue pede isto?”.

No frontend, projetar celular primeiro: toque confortável, texto legível, ação principal ao alcance de uma mão. O mockup com 3 itens não vale: use o pior caso (lista longa, título comprido, sem rede).

A pontuação do questionário **não** roda no app. O frontend envia respostas; o backend devolve faixa e texto orientativo. Nenhuma copy pode afirmar diagnóstico ou causalidade.

## Decisão de arquitetura

Se não havia alternativa real, não era decisão. Premissas da disciplina/produto (React, Express, PostgreSQL) não viram ADR.

ADR tem quatro seções: contexto, decisão no presente, alternativas reais, consequências assumidas. Modelo em [adr/README.md](adr/README.md).

## Anti-padrões

- Começar pelo código ou pela tela, e escrever o requisito depois.
- Entregar o caso feliz e chamar de pronto.
- Desativar lint, teste ou pipeline para “passar”.
- Commitar em `main`/`develop` ou misturar issues.
- Versionar IP, chave SSH, `.env` ou dado pessoal.
- Inventar clínica, marketplace, e-mail SMTP ou IA diagnóstica fora do MVP.
