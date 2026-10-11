# Processo Comercial — Clínica Estética Exemplo

## Visão geral do fluxo

```
Meta Ads / Indicação / Orgânico
         ↓
   WhatsApp (bot IA)
         ↓
   Qualificação → Agendamento
         ↓
   Atendimento presencial
         ↓
   Pós-venda (bot + humano)
```

---

## Responsabilidades

| Etapa | Responsável | Ferramenta |
|---|---|---|
| Primeiro contato e qualificação | Bot IA | n8n + WhatsApp |
| Confirmação de agendamento | Bot IA | n8n + Kommo |
| Atendimento presencial | Recepcionista | Kommo |
| Proposta e negociação | Humano | WhatsApp direto |
| Follow-up pós-proposta | Bot IA | n8n + Supabase FUP |
| Reativação de inativos | Bot IA | n8n + Supabase FUP |

---

## Regras operacionais

**Horário do bot:** 7h–19h, seg–sex  
**Fora do horário:** bot informa o horário de atendimento e coloca em fila  
**Tempo máximo sem resposta do bot:** 2 minutos  
**Escalonamento para humano:** objeção de preço > R$ 500 ou pedido explícito

**Regra de follow-up:**
- FU1: 30 min após silêncio
- FU2: 2h
- FU3: 15h
- FU4: 3 dias
- FU5: 7 dias (template)
- FU6: 15 dias (template)
- FU7: 30 dias (template)
- FU8: 60 dias (template)

**Quando parar o follow-up:**
- Cliente respondeu → `upsert_lead_on_message` reseta o stage
- Lead marcado como Ganho ou Perdido no Kommo → webhook para o n8n marca stage = done no Supabase

---

## Integração Kommo ↔ n8n

| Evento no Kommo | Ação no n8n |
|---|---|
| Lead criado | Registra no Supabase via `upsert_lead_on_message` |
| Stage → Ganho | Para follow-up (stage = done) |
| Stage → Perdido | Para follow-up (stage = done) |
| Cliente responde | Reseta cadência (stage = 0) |
| Agendamento confirmado | Agenda lembrete 24h + 2h |

---

## SLA de resposta

| Situação | SLA |
|---|---|
| Lead novo | 2 min (bot) |
| Objeção complexa | 30 min (humano) |
| Proposta formal | 4h (humano) |
| Follow-up sem resposta | Cadência automática |
