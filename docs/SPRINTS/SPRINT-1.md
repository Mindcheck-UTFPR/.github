# Sprint 1 — Fundação do Mindcheck

## Objetivo

Estabelecer a fundação técnica e operacional do produto: repositórios, governança, execução local, definição do MVP e mecanismo de acompanhamento/evidências.

## Planejamento

- Estado: ativa.
- Capacidade atribuída ao PO: 17 Story Points.
- Fonte oficial: board e Sprint `MIND Sprint 1` no Jira.

| Issue | Entrega | Responsável | SP | Snapshot |
| --- | --- | --- | ---: | --- |
| MIND-2 | Repositórios e estratégia de branches | Eduardo Ceron | 3 | Feito |
| MIND-12 | Governança e critérios de trabalho | Eduardo Ceron | 3 | Feito |
| MIND-13 | Estrutura base e execução local | Eduardo Ceron | 5 | Feito |
| MIND-41 | MVP, roadmap e priorização | Eduardo Ceron | 3 | Feito |
| MIND-42 | Gestão da Sprint e evidências | Eduardo Ceron | 3 | Fazendo na criação deste relatório |

## Evidências e aceites

| Issue | Evidência principal | Aceite funcional |
| --- | --- | --- |
| MIND-2 | [PR da documentação organizacional](https://github.com/Mindcheck-UTFPR/.github/pull/1) | repositórios e fluxo documentados |
| MIND-12 | [PR da governança](https://github.com/Mindcheck-UTFPR/.github/pull/2) | DoR, DoD, convenções e evidências publicados |
| MIND-13 | [Frontend PR #1](https://github.com/Mindcheck-UTFPR/frontend/pull/1), [correção PR #2](https://github.com/Mindcheck-UTFPR/frontend/pull/2), [Backend PR #1](https://github.com/Mindcheck-UTFPR/backend/pull/1) | lint, testes e build aprovados; onboarding e ambiente documentados |
| MIND-41 | [PR do MVP e roadmap](https://github.com/Mindcheck-UTFPR/.github/pull/3) | escopo, fora de escopo, dependências e ordem inicial definidos |
| MIND-42 | este relatório e o guia de gestão de Sprints | evidências consolidadas e rotina de acompanhamento publicada |

## Decisões

- Backend oficial adotado: Node.js + TypeScript + Express, substituindo a referência inicial a Spring Boot.
- PostgreSQL 16 é o banco local de referência.
- Jira é a fonte oficial do trabalho; GitHub é a fonte oficial de código e documentação.
- Entregas usam PR com squash merge e vínculo à issue.

## Riscos e impedimentos

- Docker não estava disponível no ambiente de validação; a configuração Compose foi revisada estaticamente. A equipe deve validar o healthcheck do PostgreSQL em uma máquina com Docker.
- A Sprint deve ser recalibrada pela quantidade efetivamente concluída, não pelos 56 SP inicialmente propostos antes da revisão de escopo.

## Fechamento do trabalho do PO

As cinco issues atribuídas ao PO nesta Sprint possuem responsável, Story Points, evidências e status rastreáveis. O encerramento da Sprint do time deve ocorrer somente após review das entregas dos demais responsáveis e registro da velocidade efetivamente concluída.

