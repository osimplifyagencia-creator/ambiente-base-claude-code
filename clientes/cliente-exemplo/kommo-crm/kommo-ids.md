# Kommo IDs — Clínica Estética Exemplo

**Conta:** clinicaexemplo.amocrm.com  
**Account ID:** 99999999  
**Token:** ver `.env`

---

## Pipelines

| Nome | ID |
|---|---|
| Venda | 12000001 |
| Pós-Venda | 12000002 |

---

## Stages — Pipeline Venda (12000001)

| Stage | ID |
|---|---|
| Novo Lead | 90000001 |
| Qualificado | 90000002 |
| Agendado | 90000003 |
| Compareceu | 90000004 |
| Proposta Enviada | 90000005 |
| Ganho | 90000006 |
| Perdido | 90000007 |

## Stages — Pipeline Pós-Venda (12000002)

| Stage | ID |
|---|---|
| Cliente Ativo | 90000010 |
| Retorno Agendado | 90000011 |
| Inativo | 90000012 |

---

## Campos personalizados — Lead

| Campo | ID | Tipo |
|---|---|---|
| Procedimento de interesse | 11000001 | select |
| Orçamento | 11000002 | price |
| Origem | 11000003 | select |

## Campos personalizados — Contato

| Campo | ID | Tipo |
|---|---|---|
| WhatsApp | 11000010 | text |
| Data de nascimento | 11000011 | date |

---

## Usuários responsáveis

| Nome | ID |
|---|---|
| Recepcionista | 55000001 |
| Bot IA | 55000002 |
