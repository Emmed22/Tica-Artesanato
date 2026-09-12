# Tica Artesanato — branch `development`

⚠️ Esta é a branch de trabalho ativo. O código aqui pode estar incompleto ou quebrado — o estado "pronto" e validado do projeto fica em [`main`](../../tree/main), não aqui.

## Antes de escrever qualquer código

Leia `doc/manual-tecnico.html`, começando pela seção 00. Ele define a ordem de construção do projeto (domínio de negócio → banco → API → interfaces) e por que essa ordem existe — pular direto para código sem entender essa base gera retrabalho.

## Como contribuir

1. Crie uma branch a partir de `development`:
   ```
   git checkout development
   git pull origin development
   git checkout -b feature/nome-da-tarefa
   ```
2. Commits em português, no imperativo: `feat: adiciona CRUD de cor`, `fix: corrige transição de status inválida`.
3. Abra o Pull Request **contra `development`** — nunca direto contra `main`.
4. Referencie a Issue correspondente no PR (`Closes #N`).
5. Só marque a Issue como concluída quando o checklist da seção no manual técnico estiver 100%. Regra do próprio manual: "uma etapa só é considerada pronta quando o checklist dela estiver verde."

## Documentação técnica

- **`doc/manual-tecnico.html`** — guia completo, seção por seção, com checklist de progresso e pendências abertas
- **`doc/apresentacao.html`** — apresentação executiva do projeto

## Issues abertas

O trabalho até a modelagem/implementação do banco (seções 01 a 06 do manual) está quebrado em Issues — uma por seção, com o checklist correspondente. Veja a aba **Issues** do repositório.
