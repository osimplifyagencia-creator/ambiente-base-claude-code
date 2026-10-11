# Índice das skills

Skill é um roteiro testado para um tipo de tarefa. Cada uma mora em `.claude/skills/<nome>/SKILL.md`. O Claude vê a descrição de todas e carrega a que serve.

## Famílias

Uma linha por skill, agrupada por assunto. Quando duas forem vizinhas, diga a fronteira.

| Família | Skill | Quando usar |
|---|---|---|
| (exemplo) CRM | `kommo-funil` | Montar ou mudar funil e etapas. Não é: disparo de mensagem. |

## Modelo de skill

Crie a pasta `.claude/skills/<nome-com-hifen>/` e, dentro, o arquivo `SKILL.md`:

```markdown
---
name: nome-com-hifen
description: "O que ela faz, em uma frase. Use quando: \"frase que a pessoa diria\", \"outra frase\". Não é: a tarefa vizinha (nome-da-outra-skill)."
---

# Título

O que esta skill resolve e qual o erro que ela evita.

## Antes de começar

O que precisa existir (credencial, arquivo, acesso) e como conferir.

## Passo a passo

1. Passo, com o comando.
2. Passo, com a prova de que deu certo.

## Pegadinhas

- O que já deu errado de verdade, e como reconhecer.

## Prova

Como saber que ficou pronto: o que medir e onde conferir.
```

Regras:

- A descrição tem até 300 caracteres e sempre traz "Use quando" e "Não é". É por ela que o Claude escolhe.
- Script que a skill usa fica em `.claude/skills/<nome>/scripts/`; material longo, em `references/`.
- Só vira skill o que já foi feito duas vezes. Pegadinha entra depois de medida, não por suposição.
