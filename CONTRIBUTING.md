# Como contribuir com o Mindcheck

## Antes de começar

1. Escolha uma issue do projeto `MIND` no Jira.
2. Confirme escopo, critérios de aceite, dependências e responsável.
3. Mova a issue para **Fazendo**.
4. Crie uma branch a partir de `develop` seguindo as convenções abaixo.

## Fluxo de desenvolvimento

Siga o [processo de desenvolvimento](docs/DEVELOPMENT.md). Resumo:

1. Confirme a DoR da issue no Jira e mova para **Fazendo**.
2. Atualize sua cópia local de `develop`.
3. Crie uma branch curta e focada em uma única issue.
4. Se a mudança for cara de desfazer, registre um ADR antes do código.
5. Faça commits pequenos, claros e verificáveis.
6. Execute testes e verificações locais do repositório.
7. Abra um Pull Request para `develop` e preencha todo o template.
8. Resolva comentários da revisão e aguarde as verificações automatizadas.
9. Espere os testes.
10. Após aprovação, o revisor fará merge usando **Squash and merge**, salvo decisão técnica documentada.

## Trabalho com a IA do Cursor

A IA implementa uma issue por vez, a partir dos critérios de aceite. Ela não escolhe o problema, não corta escopo sozinha e não assina decisão de arquitetura.

Use [AI-CURSOR.md](docs/AI-CURSOR.md) como prompt-mãe: contexto, tarefa, restrições, formato e aceite. Não cole segredos no chat e não peça o aplicativo inteiro.

## Critérios mínimos para Pull Request

- Issue do Jira vinculada.
- Critérios de aceite atendidos.
- Testes criados ou atualizados quando aplicável.
- Documentação atualizada quando necessário.
- Sem segredos, credenciais ou dados pessoais no código e no histórico.
- Pipeline aprovado e pelo menos uma revisão.
- Evidências visuais anexadas para mudanças de interface.

Consulte também:

- [Processo de desenvolvimento](docs/DEVELOPMENT.md): GCS, Git/GitHub e ciclo de uma issue;
- [Engenharia com IA](docs/AI-CURSOR.md): como pedir e revisar código no Cursor;
- [Convenções técnicas](docs/CONVENTIONS.md): branches, commits e Pull Requests;
- [Documentação de Pull Request](docs/PULL-REQUESTS.md): história, objetivo, alterações e validação;
- [Governança do projeto](docs/GOVERNANCE.md): DoR, DoD, prioridades, labels e evidências.

