# Processo de desenvolvimento do Mindcheck

Este documento traduz os slides de **Gerência de Configuração de Software**, **Ferramentas de Versionamento** e **Projeto usando IA** para o jeito de trabalhar da organização. A IA do Cursor deve seguir este fluxo, não inventar outro.

## Como esta pasta funciona

A pasta local `mindCheck` **não é um repositório**. São três repositórios irmãos:

| Pasta | Repositório | Papel |
| --- | --- | --- |
| `.github` | [Mindcheck-UTFPR/.github](https://github.com/Mindcheck-UTFPR/.github) | Padrões da organização: processo, governança, produto, sprints, ADRs |
| `frontend` | [Mindcheck-UTFPR/frontend](https://github.com/Mindcheck-UTFPR/frontend) | Interface React e app Android (Capacitor/WebView) |
| `backend` | [Mindcheck-UTFPR/backend](https://github.com/Mindcheck-UTFPR/backend) | API Express, Prisma, PostgreSQL, pontuação |

Não substitua `frontend` ou `backend` por esta pasta. A pasta `.github` **dentro** de frontend/backend é outra coisa: são os workflows do GitHub Actions.

A IA do Cursor treina neste repositório. Frontend e backend só apontam para `../.github/` (veja [AI-CURSOR.md](AI-CURSOR.md)). Abra `mindcheck.code-workspace` para os três clones ficarem no mesmo workspace.

Fonte oficial de escopo: Jira `MIND`. Fonte oficial de código, revisão e documentação versionada: GitHub.

## Gerência de configuração (GCS)

O processo de GCS existe para identificar o que forma o produto, controlar mudanças, registrar status e auditar qualidade. No Mindcheck isso se materializa assim:

| Atividade GCS | Prática no Mindcheck |
| --- | --- |
| Identificação | Código, docs, testes, schema Prisma, workflows, ADRs e issues `MIND-*` são itens de configuração |
| Controle | Mudança só entra por branch + Pull Request; `main` e `develop` são protegidas |
| Status | Jira (Sprint, responsável, SP) + PR + relatório em `docs/SPRINTS/` |
| Auditoria | Revisão obrigatória, CI, DoD e evidências na issue |

Todo item novo deve ser rastreável até uma issue. Issue sem DoR não entra em implementação.

Itens típicos sob controle: requisitos, contratos de API, código-fonte, testes, migrations, Dockerfiles, workflows e decisões de arquitetura.

## Ordem que não se inverte

A IA multiplica a especificação que recebe. Especificação ruim vira código ruim, rápido.

```text
Problema (Jira + DoR)
    → o que / por quê (critérios de aceite, escopo e não-escopo)
    → decisão cara, se houver (ADR)
    → implementação de UMA issue
    → testes e evidências
    → Pull Request para develop
    → revisão + CI
    → squash merge e aceite no Jira
```

Não comece pelo código. Não peça o aplicativo inteiro. Não desenhe tela sem requisito. Não escolha arquitetura com “qual é o melhor?”.

## Ciclo de uma issue

1. Confirmar DoR: objetivo, aceite, dependências, evidências esperadas e responsável.
2. Mover a issue para **Fazendo**.
3. Atualizar `develop` e criar branch `tipo/MIND-123-resumo`.
4. Implementar só o escopo da issue. Commits pequenos no formato `:emoji: tipo(escopo): descrição [MIND-123]`, com o catálogo de [CONVENTIONS.md](CONVENTIONS.md).
5. Rodar lint, testes e build locais do repositório alterado.
6. Abrir PR para `develop` com o template preenchido e a issue vinculada.
7. Resolver revisão, manter o pipeline verde e anexar evidências.
8. Squash and merge. Remover a branch. Confirmar DoD e mover a issue para **Concluído**.

Hotfix sai de `main`, volta para `main` e também para `develop`. Release em `main` recebe tag (`v1.0.0`).

## Git, não SVN

O time usa Git distribuído e GitHub. Cada pessoa clona, trabalha offline na branch, faz commit local e envia com `push`. Integração é por Pull Request, não por commit direto em `main` ou `develop`.

- **Merge no PR:** squash merge, para um commit final por issue.
- **Rebase:** só na branch local, antes de compartilhar. Não rebaseie `main` nem `develop`.
- **Tags:** marcam releases estáveis, não branches de trabalho.
- **CI/CD:** GitHub Actions em cada repositório de código (`ci.yml`, `deploy.yml`, `monitoring.yml`).
- **Segurança:** branch protection, revisão obrigatória, nenhum segredo no repositório nem no prompt.

Detalhes de nome de branch, commit e proteção: [CONVENTIONS.md](CONVENTIONS.md). DoR, DoD, labels e evidências: [GOVERNANCE.md](GOVERNANCE.md). Trabalho com Cursor: [AI-CURSOR.md](AI-CURSOR.md).

## O que a IA pode fazer e o que o time decide

A IA faz bem rascunho de critério de aceite, alternativas com trade-offs, código de uma tarefa e testes proporcionais.

O time continua responsável por: escolher o problema, cortar escopo, definir o que é “pronto”, assinar ADR e aceitar ou rejeitar o que a IA entregou. “Foi o que a IA sugeriu” não é decisão de arquitetura.
