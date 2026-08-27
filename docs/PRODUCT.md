# Produto, MVP e roadmap do Mindcheck

## Problema e objetivo

Pessoas precisam acompanhar bem-estar, estresse e burnout de forma estruturada, mas questionários isolados não oferecem continuidade nem visão de evolução. O Mindcheck permite responder instrumentos validados, receber interpretação por dimensões e acompanhar resultados ao longo do tempo, preservando privacidade e rastreabilidade.

## Escopo do MVP

O primeiro release utilizável inclui:

- autenticação, sessão e controle de acesso (`MIND-17`, `MIND-18`, `MIND-19`);
- cadastro, versionamento e publicação de instrumentos (`MIND-20`, `MIND-21`, `MIND-22`);
- preenchimento, persistência e retomada de avaliações (`MIND-23`, `MIND-24`);
- cálculo e interpretação por faixas (`MIND-25`);
- resultado atual e histórico básico (`MIND-26`, `MIND-27`, `MIND-28`);
- relatório PDF e download (`MIND-29`, `MIND-30`);
- painel administrativo mínimo (`MIND-32`);
- direitos do titular, proteção e auditoria (`MIND-33`, `MIND-34`);
- testes críticos, ambiente reproduzível e pipeline (`MIND-35`, `MIND-36`, `MIND-37`, `MIND-38`, `MIND-39`).

## Fora do primeiro release

- envio de relatório por e-mail/SMTP (`MIND-31`), salvo sobra de capacidade;
- observabilidade e processo de release avançados (`MIND-40`);
- integrações externas, aplicativo móvel nativo, IA diagnóstica, recomendações clínicas, multi-tenant e personalizações avançadas;
- qualquer funcionalidade que interprete o resultado como diagnóstico médico.

## Princípios de aceite funcional

- O usuário consegue concluir a jornada principal sem intervenção administrativa.
- Resultados são calculados de forma determinística e rastreável à versão do instrumento.
- Acesso a dados pessoais respeita autenticação e autorização.
- Mensagens deixam claro que o produto não fornece diagnóstico.
- Erros críticos possuem tratamento compreensível e não expõem dados sensíveis.
- Toda história segue a DoR e a DoD registradas em `GOVERNANCE.md`.

## Ordem de execução

### Sprint 1 — Fundação

Setup, governança, arquitetura, UX inicial, estratégia de QA, autenticação inicial e modelagem dos instrumentos: `MIND-2`, `MIND-12`, `MIND-13`, `MIND-14`, `MIND-17`, `MIND-19`, `MIND-20`, `MIND-35`, `MIND-38`, `MIND-41`, `MIND-42`, `MIND-43`.

### Sprint 2 — Primeira jornada funcional

Design System, login frontend, versionamento/publicação de instrumentos e base do painel: `MIND-15`, `MIND-16`, `MIND-18`, `MIND-21`, `MIND-22`, `MIND-32`.

### Sprint 3 — Avaliação completa

Persistência de respostas, experiência do questionário e pontuação: `MIND-23`, `MIND-24`, `MIND-25`.

### Sprint 4 — Resultados e privacidade

API e interfaces de resultado/histórico, direitos do titular e hardening: `MIND-26`, `MIND-27`, `MIND-28`, `MIND-33`, `MIND-34`.

### Sprint 5 — Relatório, qualidade e release

PDF, download, automação, regressão e CI/CD: `MIND-29`, `MIND-30`, `MIND-36`, `MIND-37`, `MIND-39`. `MIND-31` e `MIND-40` entram somente após o núcleo do MVP estar estável.

## Dependências críticas

| Entrega | Depende de |
| --- | --- |
| Login frontend (`MIND-18`) | autenticação backend (`MIND-17`) e fluxo UX (`MIND-14`) |
| Editor de questionários (`MIND-21`) | Design System (`MIND-15/16`) e modelo (`MIND-20`) |
| Versionamento (`MIND-22`) | modelo de instrumentos (`MIND-20`) |
| Avaliação (`MIND-23/24`) | instrumento publicado (`MIND-20/22`) e UX (`MIND-14/15`) |
| Pontuação (`MIND-25`) | respostas persistidas (`MIND-23`) e regras versionadas (`MIND-20/22`) |
| Resultados (`MIND-26/27/28`) | pontuação concluída (`MIND-25`) |
| PDF/download (`MIND-29/30`) | resultados estáveis (`MIND-26`) |
| Testes críticos (`MIND-36/37`) | funcionalidades integradas e critérios rastreados (`MIND-35`) |
| Release (`MIND-39/40`) | ambiente reproduzível (`MIND-38`) e build/testes verdes |

## Regra de priorização

1. Segurança, privacidade e bloqueios técnicos.
2. Dependências que liberam múltiplas histórias.
3. Jornada ponta a ponta do usuário.
4. Administração necessária para sustentar a jornada.
5. Relatórios e conveniências.

O PO revisa este roadmap após cada Sprint usando capacidade concluída, riscos descobertos e feedback da equipe. Mudanças de escopo devem ser registradas no Jira.
