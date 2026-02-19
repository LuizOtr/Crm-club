# CRM clube — Cronograma (iniciante | 2–4h/dia)

## Objetivo desta seção
Este cronograma define a **ordem recomendada** e a **estimativa de tempo** para concluir o MVP do projeto **CRM clube** usando **Spring Boot MVC (Kotlin)**, considerando que eu sou iniciante e tenho **2 a 4 horas por dia** para trabalhar.

> Observação: as estimativas são **faixas**. Sem usar IA, é normal ficar mais próximo do lado “lento” no início.

---

## Ordem recomendada (por onde começar e por quê)
1. **Setup + “Hello World web”**
   - Motivo: reduzir incerteza (Spring + Kotlin + Views) logo no começo.
2. **CRUD de Membros**
   - Motivo: fluxo completo Controller → Service → Repository → DB → View com baixa complexidade.
3. **Planos + Adesão (Membership)**
   - Motivo: introduz relacionamentos e prepara as mensalidades.
4. **Mensalidades (Invoices)**
   - Motivo: parte mais “lógica” (competência, unicidade, geração).
5. **Pagamento**
   - Motivo: transação e mudança de estado (OPEN → PAID).
6. **Relatório mensal**
   - Motivo: filtros + agregação (somatório) + inadimplentes.
7. **API JSON + testes**
   - Motivo: consolidar contratos e garantir regras no service.

---

## Estimativa total do MVP
- **Ritmo 2h/dia:** ~ **6 a 10 semanas**
- **Ritmo 4h/dia:** ~ **3 a 6 semanas**

> Se eu trabalhar apenas dias úteis (5/7), o calendário real pode “esticar” proporcionalmente.

---

## Cronograma por fase (2–4h/dia)
| Fase | Tempo (2h/dia) | Tempo (4h/dia) | Por que demora |
|---|---:|---:|---|
| 0) Setup + primeira página | 2–4 dias | 1–2 dias | ambiente, dependências, padrão MVC |
| 1) Membros (CRUD + Views) | 6–10 dias | 3–5 dias | validação, templates, fluxo completo |
| 2) Planos + Membership | 5–8 dias | 2–4 dias | relacionamentos, telas, regras básicas |
| 3) Invoices (gerar + listar + unicidade) | 8–14 dias | 4–7 dias | regras e edge cases (mês/competência) |
| 4) Pagamento (transação) | 4–7 dias | 2–3 dias | consistência + tratamento de erro |
| 5) Relatório mensal | 3–6 dias | 1–3 dias | queries e filtros |
| 6) API + testes de Service | 7–12 dias | 3–6 dias | DTOs, padronização de erros, testes |

---

## Entregável por fase (como saber que “acabou”)
### Fase 0 — Setup
- App sobe localmente
- `GET /` retorna uma View simples

### Fase 1 — Membros
- `GET /membros` lista
- `GET /membros/novo` + `POST /membros` cria
- `GET /membros/{id}/editar` + `POST /membros/{id}` edita
- `POST /membros/{id}/inativar` inativa

### Fase 2 — Planos + Membership
- Planos cadastra/lista
- Existe vínculo de membro com plano ativo (adesão)

### Fase 3 — Mensalidades
- Gerar mensalidades por `MM/yyyy`
- Duplicidade por competência não acontece
- Listagem por mês e status

### Fase 4 — Pagamento
- Pagar invoice OPEN cria Payment e marca invoice como PAID (atômico)

### Fase 5 — Relatório
- Receita do mês (somatório PAID)
- Inadimplentes (lista OPEN)

### Fase 6 — API + testes
- Endpoints mínimos em `/api`
- Testes cobrindo regras críticas (geração e pagamento)

---

## Rotina diária sugerida (2–4h)
- 10 min: definir 3 microtarefas (bem pequenas)
- 60–120 min: implementar 1 microentrega
- 30–60 min: testar manualmente e ajustar
- 10 min: commit com mensagem objetiva

