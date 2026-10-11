# Supabase — Notas de Schema — Clínica Estética Exemplo

**Project ref:** abcdefghijklmnop  
**MCP:** supabase-mcp-exemplo  
**Schema versão:** v1

---

## Cadência de follow-up

| Stage | Intervalo cumulativo | Delta (baseado no envio anterior) | Tipo |
|---|---|---|---|
| 0 → FU1 | 30 min | last_interaction + 30min | livre |
| 1 → FU2 | 2h | followup1_sent_at + 1h30 | livre |
| 2 → FU3 | 15h | followup2_sent_at + 13h | livre |
| 3 → FU4 | 3d | followup3_sent_at + 57h | template |
| 4 → FU5 | 7d | followup4_sent_at + 4d | template |
| 5 → FU6 | 15d | followup5_sent_at + 8d | template |
| 6 → FU7 | 30d | followup6_sent_at + 15d | template |
| 7 → FU8 | 60d | followup7_sent_at + 30d | template |

**Done stage:** 8  
**Horário comercial:** 7h–19h, seg–sex (America/Sao_Paulo)

---

## Customizações do schema padrão

- `lead_id` é **TEXT** (conta Kommo usa IDs com prefixo)
- Campo extra: `procedimento_interesse TEXT` adicionado à tabela leads
- UNIQUE index parcial: `leads_lead_id_unique WHERE lead_id IS NOT NULL`

---

## Queries úteis

```sql
-- Estado atual dos leads
SELECT * FROM vw_followup_status ORDER BY proximo_envio;

-- Saúde do sistema
SELECT * FROM vw_system_dashboard;

-- Leads prontos pra disparar agora
SELECT lead_id, nome, followup_stage, next_followup_due_at(leads.*)
FROM leads WHERE followup_stage < 8 AND next_followup_due_at(leads.*) <= NOW();

-- Histórico de alertas
SELECT * FROM system_health_log ORDER BY checked_at DESC LIMIT 20;
```
