# Governança do projeto Mindcheck

Este documento define as regras operacionais mínimas para que Jira, código, Pull Requests e evidências permaneçam sincronizados.

## Fonte oficial de informação

- O Jira `MIND` é a fonte oficial de escopo, responsável, prioridade, Sprint e status.
- O GitHub é a fonte oficial de código, revisão técnica, automações e documentação versionada.
- Toda branch, commit e Pull Request deve referenciar uma issue `MIND-*`.
- Decisões que alterem escopo ou arquitetura devem ser registradas no Jira e, quando técnicas, em um ADR.

## Definition of Ready — DoR

Uma issue pode entrar em Sprint quando possuir:

- objetivo e valor esperado compreensíveis;
- descrição suficiente para execução sem adivinhações relevantes;
- responsável definido;
- prioridade e estimativa em Story Points;
- critérios de aceite objetivos e verificáveis;
- dependências, riscos e restrições identificados;
- evidências esperadas definidas;
- referências de UX/UI, API ou regra de negócio quando aplicáveis;
- tamanho compatível com uma Sprint; caso contrário, deve ser dividida.

O PO valida a prontidão funcional. O Tech Lead e o QA apoiam a validação técnica e de testabilidade quando necessário.

## Definition of Done — DoD

Uma issue só pode ser concluída quando:

- todos os critérios de aceite foram atendidos;
- implementação foi integrada pela branch e pelo Pull Request corretos;
- revisão obrigatória foi aprovada e discussões foram resolvidas;
- testes proporcionais ao risco foram criados ou atualizados e executados;
- pipeline obrigatório passou sem falhas;
- documentação, contrato de API, migration ou ADR foram atualizados quando aplicável;
- nenhuma credencial, dado pessoal indevido ou vulnerabilidade conhecida foi introduzida;
- evidências foram anexadas ou vinculadas na issue;
- o resultado foi validado pelo responsável de aceite;
- status, responsável, Story Points e Sprint permanecem corretos no Jira.

## Modelo mínimo de história ou tarefa

```markdown
## Contexto
Explique o problema, público afetado e motivo da entrega.

## Objetivo
Descreva o resultado esperado, não apenas a solução proposta.

## Escopo
- Incluído: ...
- Fora do escopo: ...

## Critérios de aceite
- [ ] Dado ... quando ... então ...
- [ ] ...

## Dependências e riscos
- Dependências: ...
- Riscos/restrições: ...

## Evidências esperadas
- PR/commits: ...
- Testes: ...
- Imagens, vídeo, logs, API ou documento: ...
```

## Evidências por papel

| Papel | Evidências mínimas esperadas |
| --- | --- |
| PO / Produto | backlog priorizado, critérios de aceite, decisões, atas e aceite da entrega |
| Tech Lead | ADRs, diagramas, decisões técnicas, revisões de PR e issues técnicas |
| UX/UI | fluxos, protótipos, componentes, especificações e comparação design–implementação |
| Frontend | commits, Pull Requests, telas, testes e evidências visuais |
| Backend | commits, Pull Requests, endpoints, contratos de API, migrations e testes |
| QA | casos e relatórios de teste, automações, bugs registrados e rastreabilidade |
| DevOps | workflows, Dockerfiles, logs de pipeline, ambientes e documentação operacional |

Links devem apontar para artefatos acessíveis à equipe. Evidências visuais precisam identificar o cenário testado e o resultado obtido.

## Prioridades

| Prioridade | Quando usar | Tratamento esperado |
| --- | --- | --- |
| Highest | incidente crítico, bloqueio total ou risco grave de segurança/dados | atuação imediata e comunicação ao time |
| High | entrega crítica do MVP, dependência bloqueante ou defeito relevante | priorizar na Sprint atual ou seguinte |
| Medium | trabalho planejado normal do produto | ordenar conforme valor, dependências e capacidade |
| Low | melhoria não urgente, refinamento ou débito técnico pequeno | manter no backlog até haver capacidade |
| Lowest | ideia futura ou conveniência sem impacto atual | revisar periodicamente e remover se perder valor |

Alterações de prioridade devem ser justificadas na issue quando afetarem a Sprint em andamento.

## Labels básicas

Use labels em minúsculas e com hífens. Evite criar sinônimos.

### Área

`frontend`, `backend`, `qa`, `ux-ui`, `devops`, `security`, `po`, `documentation`

### Natureza

`feature`, `bug`, `test`, `technical-debt`, `research`, `setup`

### Contexto adicional

`blocked`, `needs-refinement`, `needs-design`, `needs-evidence`, `lgpd`

Assignee, Sprint, prioridade e status devem usar seus campos próprios; labels não substituem esses campos.

## Atualização do fluxo de trabalho

### Ao iniciar

1. Confirmar que a DoR foi atendida.
2. Mover a issue para **Fazendo**.
3. Criar branch com a chave Jira.
4. Registrar dependência ou bloqueio descoberto.

### Durante a execução

- Manter o Jira atualizado diante de mudança de escopo, risco ou impedimento.
- Vincular o Pull Request à issue.
- Acrescentar evidências à medida que forem produzidas.
- Usar `blocked` somente enquanto existir um impedimento real e explicar como removê-lo.

### Na revisão

1. Preencher o template do Pull Request.
2. Solicitar revisão adequada ao tipo de mudança.
3. Anexar testes e evidências.
4. Corrigir ou responder a todos os comentários.

### Ao concluir

1. Confirmar a DoD.
2. Registrar link do PR, commit final e demais evidências no Jira.
3. Obter o aceite aplicável.
4. Mover a issue para **Concluído**.

## Responsabilidades de manutenção

- O PO mantém prioridades, Sprint, critérios e aceite.
- O Tech Lead mantém convenções técnicas, arquitetura e requisitos de revisão.
- QA mantém a estratégia de testes e critérios de evidência.
- Toda a equipe mantém suas issues e Pull Requests atualizados.
- Mudanças neste documento devem passar por Pull Request e ser comunicadas ao time.

