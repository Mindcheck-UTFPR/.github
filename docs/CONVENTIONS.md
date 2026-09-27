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

Cada commit leva um shortcode de emoji, o tipo do Conventional Commit, o escopo, a descrição e a issue:

```text
:<emoji>: <tipo>(<escopo>): <descrição> [MIND-123]
```

Escreva o shortcode (`:books:`, `:sparkles:`). O GitHub mostra o emoji. A descrição é uma frase curta em português, com verbo no infinitivo, sem ponto final.

```text
:sparkles: feat(auth): adicionar página de login [MIND-18]
:books: docs(readme): atualizar instruções de execução [MIND-2]
:bug: fix(questionario): interromper loop na validação [MIND-24]
:test_tube: test(auth): cobrir renovação de sessão [MIND-19]
```

### Catálogo

| Comando Git | Resultado no GitHub |
| --- | --- |
| `git commit -m ":tada: Commit inicial"` | 🎉 Commit inicial |
| `git commit -m ":books: docs: Atualização do README"` | 📚 docs: Atualização do README |
| `git commit -m ":bug: fix: Loop infinito na linha 50"` | 🐛 fix: Loop infinito na linha 50 |
| `git commit -m ":sparkles: feat: Página de login"` | ✨ feat: Página de login |
| `git commit -m ":bricks: ci: Modificação no Dockerfile"` | 🧱 ci: Modificação no Dockerfile |
| `git commit -m ":recycle: refactor: Passando para arrow functions"` | ♻️ refactor: Passando para arrow functions |
| `git commit -m ":zap: perf: Melhoria no tempo de resposta"` | ⚡ perf: Melhoria no tempo de resposta |
| `git commit -m ":boom: fix: Revertendo mudanças ineficientes"` | 💥 fix: Revertendo mudanças ineficientes |
| `git commit -m ":lipstick: feat: Estilização CSS do formulário"` | 💄 feat: Estilização CSS do formulário |
| `git commit -m ":test_tube: test: Criando novo teste"` | 🧪 test: Criando novo teste |
| `git commit -m ":bulb: docs: Comentários sobre a função LoremIpsum( )"` | 💡 docs: Comentários sobre a função LoremIpsum( ) |
| `git commit -m ":card_file_box: raw: RAW Data do ano aaaa"` | 🗃️ raw: RAW Data do ano aaaa |
| `git commit -m ":broom: cleanup: Eliminando blocos de código comentados e variáveis não utilizadas na função de validação de formulário"` | 🧹 cleanup: Eliminando blocos de código comentados e variáveis não utilizadas na função de validação de formulário |
| `git commit -m ":wastebasket: remove: Removendo arquivos não utilizados do projeto para manter a organização e atualização contínua"` | 🗑️ remove: Removendo arquivos não utilizados do projeto para manter a organização e atualização contínua |

No Mindcheck a linha completa inclui escopo e `[MIND-123]`. O catálogo acima mostra só o emoji e o tipo.

| Shortcode | Tipo | Uso |
| --- | --- | --- |
| `:tada:` | — | commit inicial do repositório |
| `:sparkles:` | `feat` | nova funcionalidade |
| `:lipstick:` | `feat` | estilização de interface |
| `:bug:` | `fix` | correção de defeito |
| `:boom:` | `fix` | reverter mudança ineficiente |
| `:books:` | `docs` | documentação |
| `:bulb:` | `docs` | comentário que explica uma função |
| `:recycle:` | `refactor` | refatoração sem mudança funcional |
| `:art:` | `style` | formatação sem mudança de comportamento |
| `:zap:` | `perf` | desempenho |
| `:test_tube:` | `test` | testes |
| `:bricks:` | `ci` | pipeline, Docker e automação |
| `:wrench:` | `chore` | manutenção, dependência ou configuração |
| `:card_file_box:` | `raw` | dado bruto versionado |
| `:broom:` | `cleanup` | código comentado ou variável sem uso |
| `:wastebasket:` | `remove` | arquivo que saiu do projeto |

## Pull Requests

- O título deve seguir o formato `MIND-123: descrição objetiva`.
- O corpo segue [PULL-REQUESTS.md](PULL-REQUESTS.md) e o template em `.github/pull_request_template.md`.
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

