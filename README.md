# Repositório de padrões da organização Mindcheck

Este repositório centraliza o perfil e os padrões compartilhados da organização.

- `profile/README.md`: página pública da organização no GitHub.
- `CONTRIBUTING.md`: guia padrão de contribuição.
- `docs/DEVELOPMENT.md`: processo de desenvolvimento (GCS, Git/GitHub e ciclo de uma issue).
- `docs/AI-CURSOR.md`: como a equipe e a IA do Cursor devem implementar a partir da especificação.
- `docs/CONVENTIONS.md`: branches, commits, PRs, proteção e Definition of Done.
- `docs/PULL-REQUESTS.md`: como escrever a documentação da Pull Request.
- `docs/GOVERNANCE.md`: DoR, DoD, prioridades, labels, modelo de história e evidências.
- `docs/PRODUCT.md`: visão do produto, escopo do MVP, roadmap e dependências.
- `docs/ARCHITECTURE.md`: arquitetura inicial, aplicativo WebView e hospedagem na Oracle Cloud.
- `docs/adr/`: modelo de Architecture Decision Record.
- `docs/SPRINTS/`: acompanhamento, aceites e relatórios das Sprints.
- `.github/pull_request_template.md`: template compartilhado de Pull Request.
- `.cursor/rules/`: regras persistentes canônicas para a IA do Cursor.

Este repositório é o treinamento da IA. Frontend e backend apontam para ele (`AGENTS.md` + `.cursor/rules/org-github.mdc`) e não duplicam o processo.

Por estar no repositório público `.github`, os arquivos comunitários são usados como padrão nos demais repositórios da organização quando não houver uma configuração específica.
