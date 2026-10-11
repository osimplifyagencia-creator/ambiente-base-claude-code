# Clínica Estética Exemplo — Histórico

## Contexto do cliente
Clínica de estética em São Paulo, foco em procedimentos faciais e corporais. 
Atendimento híbrido (presencial + WhatsApp). Ticket médio: R$ 800.

**Responsável:** (nome)  
**Início da operação:** 2026-06-03

---

## Changelog

### 2026-06-03 — Setup inicial
- Criado projeto Supabase (ref: abcdefghijklmnop)
- Criados funis Venda + Pós-Venda no Kommo via API
- Deploy do workflow n8n de agente WhatsApp
- Sistema de follow-up v1 aplicado (8 FUPs, 7h–19h seg–sex)

### 2026-09-16 · Organização do repositório
- `config.json`: `ativo` passou de `true` para `false` e ganhou a chave `_nota`. A pasta é exemplo de estrutura com dados fictícios, não cliente, e com `ativo: false` os agentes `gerente-*` e os scripts não a tratam como implantação.
- O `CLAUDE.md` não foi criado: a regra 1 do OS vale para cliente ativo.

---

## Pendências

- [ ] Validar script de objeção de preço com a cliente
- [ ] Configurar retargeting via Salesbot após 30 dias sem retorno
- [ ] Conectar Meta Ads ao Kommo para rastrear origem dos leads

---

## Decisões importantes

- **Lead_id como TEXT**: conta Kommo da cliente usa IDs com prefixo, não BIGINT puro
- **Pipeline pós-venda separado**: cliente pediu para não misturar leads novos com clientes ativos
- **Horário 7h–19h seg–sex**: atendentes entram às 7h30 mas o bot pode iniciar 30min antes
