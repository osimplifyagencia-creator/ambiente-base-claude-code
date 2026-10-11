# Ambiente base para o Claude Code no VS Code

Esta pasta é o esqueleto de um repositório de operação: onde ficam os clientes, as credenciais, os roteiros (skills) e as regras que o Claude segue. Você abre a pasta no VS Code e o Claude já sabe como trabalhar nela.

## O que tem aqui

| Arquivo ou pasta | Para que serve |
|---|---|
| `CLAUDE.md` | O contexto e as regras. O Claude lê sozinho em toda conversa. É o arquivo mais importante. |
| `.claude/settings.json` | Trava de segurança: o Claude não lê arquivo `.env`. |
| `.claude/skills/` | Os roteiros da casa. Começa só com o índice e o modelo de skill. |
| `.claude/agents/` | Dois ajudantes: `investigador` (acha a causa) e `provador` (prova que funciona). |
| `.claude/MAPA-DO-REPO.md` | O que tem dentro de cada pasta. |
| `clientes/cliente-exemplo/` | Um cliente fictício completo, para copiar a cada cliente novo. |
| `empresa/`, `biblioteca/`, `software/` | Pastas vazias, com uma linha dizendo o que entra nelas. |
| `PROMPT-DE-MONTAGEM.md` | O texto para colar no Claude e ele terminar a montagem com você. |

## Montar (uns 15 minutos)

1. Instale, se ainda não tiver: [VS Code](https://code.visualstudio.com), [Git](https://git-scm.com) e a extensão **Claude Code** (no VS Code, aba de extensões, procure "Claude Code" da Anthropic). Entre com a sua conta do Claude.
2. Clone o repositório (ou descompacte o zip) num lugar definitivo, com o nome do seu repositório, por exemplo `minha-empresa-automacoes`. Evite Downloads e pastas sincronizadas com nuvem. Se clonou, o passo 4 desliga a pasta do repositório de origem, para ela ser só sua.
3. No VS Code: **Arquivo, Abrir pasta** e escolha essa pasta. Abra sempre pela raiz, é dela que o Claude lê o `CLAUDE.md`.
4. Abra o painel do Claude Code, copie o conteúdo de `PROMPT-DE-MONTAGEM.md` e cole. Ele faz as perguntas, preenche o `CLAUDE.md` com os dados da sua empresa, inicia o git e cria o primeiro cliente.
5. Teste: numa conversa nova, pergunte "quais são as regras deste repositório e onde ficam os clientes?". Ele tem de responder com o que está no `CLAUDE.md`, sem você colar nada.

## Regras que valem desde o primeiro dia

- **Credencial mora em `.env`**, dentro da pasta do cliente, e o `.env` nunca entra no git (o `.gitignore` já cuida). Nunca cole token ou senha na conversa.
- **ID e endereço moram no `config.json`** do cliente, não na conversa.
- **Toda mudança importante vira uma linha no `historico.md`** do cliente.
- **Fez a mesma coisa duas vezes, vira skill.** Peça: "transforma o que acabamos de fazer numa skill". O modelo está no `INDICE.md`.

## Como crescer

- Cliente novo: "cria o cliente tal a partir do cliente-exemplo".
- Skill nova: uma pasta em `.claude/skills/<nome>/` com um `SKILL.md`, e uma linha no `INDICE.md`.
- O `CLAUDE.md` deve ficar curto. Quando crescer, mova o detalhe para um arquivo à parte e deixe só o link.
