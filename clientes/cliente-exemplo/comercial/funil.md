# Funil de Vendas — Clínica Estética Exemplo

## Visão geral

```
Lead Entra → Qualificação (bot) → Agendamento → Compareceu → Proposta → Ganho
                                                    ↓
                                               Não veio → Follow-up reativação
```

---

## Etapas do funil

### 1. Novo Lead
**Critério de entrada:** lead chega via WhatsApp, Meta Ads ou indicação  
**Responsável:** bot IA  
**Ação:** iniciar qualificação imediatamente  
**SLA:** resposta em até 2 minutos  
**Kommo stage:** `novo_lead` (90000001)

### 2. Qualificado
**Critério de passagem:** respondeu procedimento de interesse + tem disponibilidade de horário  
**Responsável:** bot IA → passa para humano se objeção de preço ou dúvida complexa  
**Ação:** oferecer agendamento  
**Kommo stage:** `qualificado` (90000002)

### 3. Agendado
**Critério de passagem:** confirmou data e horário  
**Responsável:** humano confirma no sistema  
**Ação:** enviar confirmação + lembrete 24h antes + lembrete 2h antes  
**Kommo stage:** `agendado` (90000003)

### 4. Compareceu
**Critério de passagem:** cliente apareceu na clínica  
**Responsável:** recepcionista atualiza Kommo  
**Ação:** bot envia mensagem pós-consulta + proposta se não fechou  
**Kommo stage:** `compareceu` (90000004)

### 5. Proposta Enviada
**Critério de passagem:** orçamento formal enviado  
**Responsável:** humano  
**Ação:** follow-up em 24h, 3d, 7d  
**Kommo stage:** `proposta_enviada` (90000005)

### 6. Ganho / Perdido
**Ganho:** procedimento realizado ou sinal pago  
**Perdido:** recusou proposta, sem resposta após 3 follow-ups, número inválido  
**Kommo stages:** `ganho` (90000006) / `perdido` (90000007)

---

## Critérios de qualificação (bot)

| Pergunta | Objetivo |
|---|---|
| Qual procedimento te interessa? | Segmentar oferta |
| Já fez esse procedimento antes? | Calibrar expectativa |
| Como ficou sabendo da clínica? | Rastrear origem |
| Qual a sua disponibilidade? | Partir pro agendamento |

**Desqualificar se:** menor de 18 anos, procedimento que a clínica não faz, localidade muito distante.

---

## Motivos de perda (Kommo)

- Preço — achou caro
- Concorrente — foi em outro lugar
- Sem retorno — parou de responder
- Não compareceu — agendou e não foi
- Fora do perfil — não era o público
