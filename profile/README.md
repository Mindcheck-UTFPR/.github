# Mindcheck

O **Mindcheck** é um projeto acadêmico voltado a jovens adultos, principalmente universitários. A ideia é juntar check-ins de humor, fatores da rotina e questionários de bem-estar em um dashboard simples, ajudando a pessoa a perceber padrões e buscar apoio quando necessário.

> O Mindcheck não realiza diagnóstico. Os resultados são orientativos e devem encaminhar o usuário a profissionais e serviços adequados.

## Repositórios

| Repositório | Responsabilidade |
| --- | --- |
| [frontend](https://github.com/Mindcheck-UTFPR/frontend) | Interface React mobile-first e aplicativo Android com Capacitor/WebView |
| [backend](https://github.com/Mindcheck-UTFPR/backend) | API Node.js, regras do produto, autenticação e PostgreSQL |
| [.github](https://github.com/Mindcheck-UTFPR/.github) | Documentação geral e padrões compartilhados |

## Como trabalhamos

- O trabalho é planejado e acompanhado no projeto Jira `MIND`.
- `main` contém somente versões estáveis.
- `develop` é a base de integração do desenvolvimento.
- Toda mudança deve estar associada a uma issue e passar por Pull Request.
- Não são permitidos commits diretos em `main` ou `develop`.

Consulte o [guia de contribuição](../CONTRIBUTING.md), as [convenções técnicas](../docs/CONVENTIONS.md) e a [governança do projeto](../docs/GOVERNANCE.md) antes de iniciar uma tarefa.

## Stack do MVP

- React + TypeScript + Vite, começando pela experiência mobile;
- Capacitor para empacotar a aplicação React em um WebView Android;
- Node.js + TypeScript + Express no backend;
- PostgreSQL;
- Docker Compose e Nginx;
- VM gratuita da Oracle Cloud para demonstração.

## Equipe

O projeto é desenvolvido por estudantes, de forma colaborativa. A arquitetura e o deploy devem ser simples o bastante para o grupo entender, apresentar e manter.
