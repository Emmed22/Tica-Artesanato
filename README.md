# 🧶 Tica Artesanato — branch `development`

> ⚠️ Esta é a branch de trabalho ativo. O código aqui pode estar incompleto ou quebrado. O estado validado do projeto fica em [`main`](../../tree/main) — não commite direto lá.

---

## Antes de escrever qualquer código

Leia `doc/manual-tecnico.html`, começando pela **seção 00**. Ele define a ordem de construção do projeto:

```
Domínio de negócio → Banco de dados → API → Interfaces
```

Pular essa ordem gera retrabalho. O manual existe exatamente para evitar isso.

---

## Fluxo de trabalho

### Branches

```
main          → código validado, checklist 100% completo
  └─ development   → integração do time
       └─ feature/nome-da-tarefa   → seu trabalho
```

### Passo a passo para contribuir

**1. Sempre parta da `development` atualizada:**
```bash
git checkout development
git pull origin development
git checkout -b feature/nome-da-tarefa
```

**2. Commits em português, no imperativo:**
```
feat: adiciona CRUD de cor
fix: corrige transição de status inválida
docs: atualiza README com instruções de setup
refactor: extrai validação de link mágico para service
```

**3. Abra o Pull Request contra `development` — nunca contra `main`.**

**4. Referencie a Issue no PR:**
```
Closes #3
```

**5. Só feche a Issue quando o checklist da seção no manual técnico estiver 100% verde.**

---

## Estrutura do projeto

```
tica-artesanato/
├── backend/              → API Java 21 · Spring Boot
├── frontend/             → Angular · TypeScript
├── mobile/               → Ionic
├── data/                 → SQL · Python · dashboard
├── doc/                  → documentação técnica e apresentação
├── .github/workflows/    → pipelines CI/CD
├── docker-compose.yml
└── .env.example          → variáveis de ambiente (nunca commite o .env real)
```

---

## Setup local

> Esta seção será preenchida assim que o `docker-compose.yml` e os serviços estiverem implementados. Por enquanto, siga o `doc/manual-tecnico.html` para entender o que precisa estar instalado antes de começar (seção 04).

**Pré-requisitos já definidos no manual:**
- Git
- JDK 21
- Node LTS
- Angular CLI
- Ionic CLI
- Docker

---

## Documentação técnica

| Arquivo | Conteúdo |
|---|---|
| `doc/manual-tecnico.html` | Guia completo, seção por seção, com checklist de progresso e pendências abertas |
| `doc/apresentacao.html` | Resumo executivo do projeto para apresentação |

> Toda decisão de arquitetura, modelagem de banco, regras de negócio e escopo está no manual técnico. Em caso de dúvida, ele é a fonte de verdade — não o que alguém lembra da última reunião.

---

## Issues e fases

O trabalho está quebrado em Issues por fase. Cada Issue tem o checklist correspondente às seções do manual técnico.

| Issue | Fase | Depende de |
|---|---|---|
| `[FASE 1]` | Requisitos, PMC e MVP | — |
| `[FASE 2]` | Fundação — repositório, ferramentas, Docker | Fase 1 |
| `[FASE 3a]` | Banco — modelagem do schema v3 | Fase 2 |
| `[FASE 3b]` | Banco — implementação no Supabase | Fase 3a |

> Fases 4 em diante (Backend, Segurança, Frontend, Mobile, Dados, Deploy, Qualidade) serão abertas como Issues no mesmo formato conforme o projeto avança.

Veja todas as Issues abertas na [aba Issues](../../issues) do repositório.

---

## Regras que não se negocia

- **Não commita direto em `main` nem em `development`.** Sempre via branch + PR.
- **Não commita `.env` com credenciais reais.** Use `.env.example` como template.
- **Não fecha Issue sem checklist 100%.** A regra é do próprio manual técnico.
- **Connection string do Supabase fica em variável de ambiente**, nunca no código.
