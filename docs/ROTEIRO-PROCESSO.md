# Roteiro — processo de desenvolvimento

Cada tópico é um corte do vídeo. A ordem é a do processo dos repositórios.

## 1. Clonar o projeto

A pasta `mindCheck` não é um repositório. Cada pessoa clona os três projetos como pastas irmãs, com esses nomes, para o frontend e o backend acharem `../.github/`.

```bash
mkdir mindCheck
cd mindCheck
git clone https://github.com/Mindcheck-UTFPR/.github.git .github
git clone https://github.com/Mindcheck-UTFPR/frontend.git frontend
git clone https://github.com/Mindcheck-UTFPR/backend.git backend
```

Abra a pasta `mindCheck` no Cursor, com as três pastas no mesmo workspace. Requisitos para rodar o código: Node.js 22+ e pnpm 10+. O passo a passo de `pnpm install` e `pnpm dev` está no README de cada repositório de código.

## 2. Três repositórios, uma pasta

- `.github` — processo, produto, governança e decisões
- `frontend` — tela React
- `backend` — API, Prisma e pontuação

A pasta `.github` dentro de `frontend` ou `backend` é outra coisa: são os workflows do GitHub Actions.

## 3. Quem manda no quê

O Jira `MIND` define o que fazer. O GitHub guarda o código. O produto está em `docs/PRODUCT.md`: autoconhecimento para universitários, sem diagnóstico. A pontuação fica só no backend.

## 4. Escolher a issue

Abra uma issue `MIND-*`. Leia o objetivo, o aceite e o que fica de fora. Uma issue por vez.

## 5. Validar antes de codar

Confira a Definition of Ready: objetivo claro, responsável, aceite verificável, dependências e evidências. Sem isso, a issue não entra em implementação. Mova para **Fazendo**.

## 6. Atualizar a develop

No repositório certo (`frontend` ou `backend`), atualize a `develop`. A branch de trabalho nasce dela, não da `main`.

## 7. Criar a branch

Nome: `feature/MIND-123-resumo`, ou `fix/`, `chore/`. Hotfix sai da `main`. Letras minúsculas, hífen, uma issue só.

## 8. Decisão cara, se houver

ADR é uma página curta em `docs/adr/` que registra uma escolha difícil de desfazer. Serve para o time não depender da memória de quem implementou.

Só entra quando havia alternativa real. Exemplos: como modelar o questionário, como autenticar, onde persistir o histórico, como versionar a pontuação. A página tem quatro partes: o que era verdade naquele dia, a decisão no presente, as alternativas que ficaram de fora e o que o time aceita perder.

React, Express e PostgreSQL não viram ADR. Isso já é premissa do MVP. “A IA sugeriu” também não é decisão: a IA pode listar opções, e o time assina antes de seguir.

Se a issue só pede uma tela ou um endpoint dentro do que já está decidido, pule este passo. Se a escolha muda o banco, o contrato da API ou a regra de pontuação de um jeito custoso de reverter, escreva o ADR, pare e espere o aceite.

## 9. Implementar só o escopo

A issue diz o que entra e o que fica de fora. O código nasce disso.

Tela, texto e navegação vão no `frontend`. Rota, validação, Prisma, pontuação e regra de acesso vão no `backend`. O app envia as respostas; a faixa e o texto orientativo voltam da API. Check-in de humor não é questionário.

Uma branch, uma issue. Se aparecer outra correção no caminho, ela vira outra branch.

Cada tela precisa dos estados reais: carregando, vazio, erro, sem conexão, texto longo e permissão negada. Nenhuma frase afirma diagnóstico ou causa.

## 10. Commit no padrão

Mensagem:

```text
:emoji: tipo(escopo): descrição [MIND-123]
```

Exemplo: `:sparkles: feat(auth): adicionar página de login [MIND-18]`. O catálogo está em `docs/CONVENTIONS.md`. Commits pequenos.

## 11. Verificar na máquina

Antes do PR, rode no repositório que mudou. Se só o frontend mudou, não precisa rodar o backend, e o inverso também vale.

```bash
pnpm lint
pnpm test
pnpm build
```

`lint` pega erro de estilo e de TypeScript. `test` roda o Vitest. `build` confirma que o projeto compila. No backend, o build também gera o cliente do Prisma. Se um comando falhar, corrija e rode de novo. Desligar o lint, apagar o teste ou pular o pipeline para o PR ficar verde não conta como pronto.

## 12. Abrir o Pull Request

Destino: `develop`. Título: `MIND-123: descrição`. O GitHub já traz o esqueleto do texto.

## 13. Escrever a documentação do PR

Preencha, nesta ordem: História (por que), Objetivo (o que melhora), O que foi feito (por área, com verbo), Testes e verificações (só o que rodou de fato), Commits principais e Relacionados. Sem item relacionado, apague essa seção. Marque o checklist. O detalhe está em `docs/PULL-REQUESTS.md`.

## 14. Revisão e CI

O autor não aprova o próprio PR. Resolva os comentários. O pipeline precisa ficar verde.

## 15. Integrar e concluir

Squash merge. Apague a branch. No Jira, anexe o link do PR e as evidências, confira a Definition of Done e mova para **Concluído**.

## 16. O que não é automático

O processo está escrito. Quem segue essa ordem entrega no padrão. O Git não cria a branch, não valida a issue e não escreve a História do PR.
