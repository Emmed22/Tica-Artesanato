# Tica Artesanato

Loja virtual de artesanato em crochê sob encomenda. O cliente monta a peça na vitrine, cadastra-se por link mágico, fecha o pedido em uma conversa real no WhatsApp e acompanha o status logado no sistema.

🚧 **Status:** em desenvolvimento — MVP ainda não lançado. O trabalho ativo acontece na branch [`development`](../../tree/development).

## Stack

| Camada | Tecnologia |
|---|---|
| Frontend web | Angular |
| Mobile | Ionic |
| Backend | Java 21 + Spring Boot |
| Banco de dados | PostgreSQL (Supabase) |
| Dados / Analytics | Python |
| CI/CD | Docker + GitHub Actions |

## Estrutura do repositório

```
tica-artesanato/
├── backend/    → API Java · Spring Boot
├── frontend/   → Angular · TypeScript
├── mobile/     → Ionic
├── data/       → SQL · Python · dashboard
├── doc/        → documentação técnica e apresentação
├── .github/workflows/
├── docker-compose.yml
└── .env.example
```

## Documentação

Toda a decisão de arquitetura, modelagem de banco e escopo do projeto está documentada em `doc/`:

- **`doc/manual-tecnico.html`** — guia de implementação seção por seção, com checklist de progresso
- **`doc/apresentacao.html`** — resumo executivo do projeto

## Fluxo de trabalho

`main` recebe apenas código que já passou pela branch `development` e cujo checklist da seção correspondente (no manual técnico) está 100% completo. Não se commita direto em `main`.
