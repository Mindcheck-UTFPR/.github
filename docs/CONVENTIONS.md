# Convenções de desenvolvimento

Este documento é a referência comum dos repositórios da organização Mindcheck.

## Estratégia de branches

| Branch | Uso | Origem | Destino |
| --- | --- | --- | --- |
| `main` | Versões estáveis e releases | `develop` ou `hotfix/*` | — |
| `develop` | Integração contínua | `main` | `main` |
| `feature/MIND-123-resumo` | Funcionalidade ou melhoria | `develop` | `develop` |
| `fix/MIND-123-resumo` | Correção ainda não publicada | `develop` | `develop` |
| `hotfix/MIND-123-resumo` | Correção urgente em produção | `main` | `main` e `develop` |
| `chore/MIND-123-resumo` | Manutenção sem mudança funcional | `develop` | `develop` |

Use letras minúsculas, hífens e a chave da issue. Exemplo: `feature/MIND-17-autenticacao-jwt`.

Branches devem ser removidas após o merge. Uma branch não deve misturar issues ou objetivos diferentes.

## Commits

Adotamos Conventional Commits com a chave do Jira:

```text
<tipo>(<escopo>): <descrição> [MIND-123]
```

Tipos aceitos:

- `feat`: nova funcionalidade;
- `fix`: correção de defeito;
- `test`: testes;
- `docs`: documentação;
- `refactor`: refatoração sem mudança funcional;
- `style`: formatação sem alteração de comportamento;
- `chore`: manutenção, dependências ou configuração;
- `ci`: automação e pipeline;
- `perf`: melhoria de desempenho.

Exemplos:

```text
feat(auth): adicionar autenticação JWT [MIND-17]
test(auth): cobrir renovação de sessão [MIND-19]
docs(org): documentar fluxo de branches [MIND-2]
```

## Pull Requests

- O título deve seguir o formato `MIND-123: descrição objetiva`.
- O PR deve ter `develop` como destino, exceto releases e hotfixes.
- O autor não deve aprovar o próprio PR.
- Toda conversa de revisão deve ser resolvida antes do merge.
- Alterações grandes devem ser divididas em entregas revisáveis.
- Use **Squash and merge** para manter um commit final por PR.

## Proteção mínima de branches

Configure `main` e `develop` com:

- Pull Request obrigatório antes do merge;
- pelo menos uma aprovação;
- aprovação invalidada quando novos commits forem enviados;
- conversas de revisão resolvidas;
- verificações automatizadas obrigatórias;
- branch atualizada antes do merge, quando suportado;
- bloqueio de force push e exclusão;
- aplicação das regras a administradores, quando possível.

Para `main`, permita merges somente a partir de `develop` ou `hotfix/*` e associe releases a tags versionadas, por exemplo `v1.0.0`.

## Qualidade e segurança

- Nunca registre senhas, tokens, chaves ou arquivos `.env`.
- Valide entradas e preserve a privacidade dos dados.
- Inclua testes proporcionais ao risco da mudança.
- Não reduza cobertura ou desative verificações sem justificativa no PR.
- Registre decisões arquiteturais relevantes em ADRs.

## Definition of Done

Uma entrega está concluída quando:

- critérios de aceite foram atendidos;
- código foi revisado e integrado;
- testes e pipeline passaram;
- documentação e evidências foram atualizadas;
- não há pendências críticas conhecidas;
- a issue do Jira reflete o resultado entregue.

