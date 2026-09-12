<div align="center">

# 🧶 Tica Artesanato

**Vitrine digital e gestão de encomendas para artesanato em crochê sob encomenda**

Projeto Integrador · Desenvolvimento de Software Multiplataforma · Fatec DSM

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![Licença](https://img.shields.io/badge/licença-acadêmico-lightgrey)

</div>

---

## 📋 Índice

- [Sobre o projeto](#-sobre-o-projeto)
- [O problema](#-o-problema)
- [A solução](#-a-solução)
- [Escopo do MVP](#-escopo-do-mvp)
- [Arquitetura](#-arquitetura)
- [Stack tecnológica](#-stack-tecnológica)
- [Estrutura do repositório](#-estrutura-do-repositório)
- [Documentação](#-documentação)
- [Como rodar o projeto](#-como-rodar-o-projeto)
- [Equipe](#-equipe)
- [Roadmap](#-roadmap)
- [Status atual](#-status-atual)

---

## 🧶 Sobre o projeto

**Tica Artesanato** é uma profissional autônoma que produz peças de crochê artesanais sob encomenda — acessórios, decoração e itens personalizados, cada um montado conforme a escolha do cliente.

Hoje, toda a operação acontece de forma manual: catálogo em fotos soltas no celular, atendimento pelo WhatsApp e controle de pedidos na memória. Este projeto **não substitui o atendimento humano**. É uma ferramenta que organiza a vitrine, guia o cliente na montagem do pedido e dá à Tica visibilidade sobre o que está em andamento — mantendo o fechamento onde ele já funciona: uma conversa real no WhatsApp.

---

## 🎯 O problema

| Problema | Impacto |
|---|---|
| **Vitrine desorganizada** | Catálogo existe apenas em fotos soltas e conversas — difícil de navegar, comparar ou compartilhar com o cliente. |
| **Atendimento repetitivo** | Cada pedido começa do zero: produto, cor, tamanho e prazo são perguntados manualmente a cada conversa. |
| **Sem visibilidade dos pedidos** | Sem controle de status, a Tica depende da memória para saber o que está pendente, em produção ou pronto. |

---

## 💡 A solução

Um sistema com **duas portas de acesso**:

**Ambiente do cliente** (público, sem cadastro obrigatório)
- Vitrine com catálogo de peças ativas
- Jornada guiada "monte sua peça" — escolha de cor e tamanho por item
- Envio estruturado da solicitação para o WhatsApp da Tica
- Acompanhamento de pedido via **link mágico** (sem senha)

**Ambiente da Tica** (autenticado)
- Cadastro e gestão de produtos, cores e tamanhos
- Gestão de pedidos com máquina de status
- Histórico completo de transições de cada pedido
- Indicadores básicos do negócio

### Jornada do cliente

```
Vitrine → Monte a peça → Preenche dados → Revisão → Envio ao WhatsApp → Acompanha por link mágico
```

### Fluxo operacional do pedido

```
RECEBIDO → EM_NEGOCIACAO → CONFIRMADO → EM_PRODUCAO → PRONTO → ENTREGUE
                                                              ↘ CANCELADO
```

> Toda transição de status gera um registro histórico. O cliente recebe notificação por e-mail a cada mudança relevante.

---

## ✅ Escopo do MVP

| Entra no MVP | Fora do escopo |
|---|---|
| Vitrine digital com catálogo | Pagamento online / gateway |
| Jornada guiada de montagem de peça | Marketplace ou chat próprio |
| Envio estruturado para o WhatsApp | Rastreamento logístico em tempo real |
| Autenticação por link mágico (sem senha) | Sistema fiscal / contabilidade / ERP |
| Máquina de status com histórico | IA / recomendação de produtos |
| Notificação de status por e-mail | Loja multi-artesã |
| Indicadores básicos de negócio | Integrações pagas |

> Escopo reduzido por decisão, não por falta de ambição: o objetivo é garantir que o que entra funcione bem dentro do prazo de um semestre.

---

## 🏗 Arquitetura

Arquitetura em camadas, padrão MVC no backend:

```
Cliente (Angular / Ionic)
        ↓ HTTP / REST
   Controller  (recebe requisições)
        ↓
    Service    (regras de negócio)
        ↓
   Repository  (acesso a dados)
        ↓
   PostgreSQL (Supabase)
```

**Regras de negócio centrais:**
- Produto inativo não aparece na vitrine
- Toda transição de status é registrada em `pedido_status_historico`
- Link mágico tem expiração e uso único
- Lembrete automático por e-mail para pedidos parados há 5 dias em `RECEBIDO`
- Campo `estimativa_pronto_em` obrigatório ao mover para `EM_PRODUCAO`

**Segurança:** Spring Security + JWT para o painel da Tica. A vitrine e a jornada do cliente são públicas, sem exigir cadastro.

Em paralelo, um fluxo de analytics consome o mesmo banco:

```
PostgreSQL → ETL (Python) → Indicadores → Dashboard
```

---

## 🛠 Stack tecnológica

| Camada | Tecnologia |
|---|---|
| Backend | Java 21 · Spring Boot · Spring Security (JWT) |
| Frontend Web | Angular · TypeScript |
| Mobile | Ionic |
| Banco de dados | PostgreSQL (Supabase) |
| Dados / Analytics | Python (ETL e indicadores) |
| Infraestrutura | Docker · GitHub Actions |
| Versionamento | Git / GitHub (Issues, branches, Pull Requests) |

---

## 📁 Estrutura do repositório

```
tica-artesanato/
├── backend/              → API Java · Spring Boot
├── frontend/             → Angular · TypeScript
├── mobile/               → Ionic
├── data/                 → SQL · Python · dashboard
├── doc/                  → documentação técnica e apresentação
├── .github/workflows/    → pipelines CI/CD
├── docker-compose.yml
└── .env.example
```

---

## 📚 Documentação

Toda decisão de arquitetura, modelagem de banco e escopo está documentada em `doc/`:

- **`doc/manual-tecnico.html`** — guia de implementação seção por seção, com checklist de progresso
- **`doc/apresentacao.html`** — resumo executivo do projeto

> O trabalho ativo acontece na branch [`development`](../../tree/development). A `main` recebe apenas código validado e com checklist 100% concluído.

---

## 🚀 Como rodar o projeto

> Esta seção será preenchida com instruções reais (pré-requisitos, variáveis de ambiente, comandos Docker) assim que os serviços estiverem implementados. Até lá, consulte `doc/manual-tecnico.html` para entender a ordem de construção.

---

## 👥 Equipe

| Frente | Responsabilidade |
|---|---|
| Backend / Java | Spring Boot, API REST, banco de dados, segurança, regras de negócio |
| Frontend / Mobile | Angular, Ionic, UX/UI, integração com a API |
| Dados | SQL, Python, ETL, analytics e dashboard |

---

## 🗺 Roadmap

| Fase | Entregas |
|---|---|
| **Fase 1** — Requisitos e planejamento | PMC, personas, escopo do MVP, máquina de status validada com a Tica |
| **Fase 2** — Fundação | Repositório, ferramentas, Docker, conta Supabase |
| **Fase 3** — Banco de dados | Schema v3 (2 enums + 9 tabelas), modelagem e implementação no Supabase |
| **Fase 4** — Backend | API REST, regras de negócio, link mágico, máquina de status |
| **Fase 5** — Segurança | Spring Security, JWT, autenticação da Tica, rotas públicas vs. protegidas |
| **Fase 6** — Frontend e Mobile | Vitrine, jornada de montagem, painel da Tica, Angular + Ionic |
| **Fase 7** — Dados | ETL, Python, indicadores, dashboard |
| **Fase 8** — Deploy | Docker Compose, GitHub Actions, CI/CD |
| **Fase 9** — Qualidade e entrega | Testes, documentação final, validação com a Tica |

---

## 📌 Status atual

- [ ] PMC validado com a Tica
- [ ] Personas documentadas
- [ ] Escopo do MVP fechado
- [ ] Máquina de status validada (comportamento do lembrete de 5 dias)
- [ ] Repositório e estrutura de pastas criados
- [ ] Banco modelado (dbdiagram.io)
- [ ] Schema executado no Supabase
- [ ] Início do desenvolvimento

---

<div align="center">
Da foto solta no celular e das mensagens no WhatsApp para um sistema que organiza — sem tirar da Tica o cuidado artesanal em cada peça.
</div>
