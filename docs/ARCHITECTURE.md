# Arquitetura inicial do Mindcheck

## Visão geral

O Mindcheck terá uma interface React mobile-first que funciona no navegador e também será empacotada como aplicativo Android usando Capacitor/WebView.

```text
Aplicativo Android (Capacitor/WebView) ou navegador
                         |
                       HTTPS
                         |
                       Nginx
                   /             \
          frontend React       /api
                                  |
                         Node.js + Express
                                  |
                             PostgreSQL
```

Os serviços de produção serão executados com Docker Compose em uma VM gratuita da Oracle Cloud. Nginx será a entrada pública, responsável por HTTPS, arquivos do frontend e proxy para a API.

## Decisões principais

- React + TypeScript + Vite para a interface.
- Capacitor para reaproveitar a interface em um WebView Android.
- Node.js + TypeScript + Express para a API.
- PostgreSQL para dados relacionais e históricos.
- Monólito modular no MVP.
- Docker Compose, Nginx e Oracle Cloud Free Tier para a demonstração.

## Cuidados

- Não versionar IPs privados, chaves SSH, senhas, tokens ou arquivos `.env`.
- Conferir os limites da conta gratuita e criar alertas de orçamento antes do deploy.
- Usar HTTPS e restringir no firewall somente as portas necessárias.
- Fazer backup do PostgreSQL e testar restauração.
- Não registrar respostas psicológicas ou dados de humor nos logs.

As decisões detalhadas devem ser registradas em ADRs curtos pelo responsável de arquitetura.
