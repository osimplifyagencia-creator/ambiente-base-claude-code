# <EMPRESA>: contexto do projeto

Repositório central de operações da <EMPRESA>: automações, CRM, prompts de IA, follow-up e sistemas próprios, para todos os clientes ativos.

> **Regra de roteamento:** pedido de trabalho começa pela skill da tarefa (ferramenta Skill), antes de ler arquivo ou buscar no repositório. A descrição de cada skill diz "Use quando" e "Não é". Se nenhuma serve, siga sem skill. Pergunta curta ou conversa não precisa de skill.

## Ciclo de trabalho

1. **Skill da tarefa**, pela regra acima.
2. **Executar** pelo menor caminho. Tarefa grande vira passos curtos, cada um com prova. Busca larga ou leitura de log grande vai para um agente (`investigador`, `provador`).
3. **Provar nos dois sentidos** antes de dizer pronto: o caso certo passa e o errado é barrado. Conta o efeito no mundo (banco, CRM, mensagem, tela clicada), nunca só a execução verde.
4. **Consertar e provar de novo.** Se depender de credencial, acesso ou decisão do dono, pare com a evidência.
5. **Relatar** assim: **Resultado** (o que ficou pronto ou falhou) · **Prova** (o que foi medido e onde conferir) · **Não feito ou risco** · **Próximo passo**. Sem prova, diga "não provado".
6. Tarefa longa grava o estado em `RETOMAR-AQUI.md` na pasta do trabalho antes de cada etapa grande.

## Onde as coisas estão

```
clientes/<slug>/   CLAUDE.md (contexto, carrega sozinho) · config.json (fonte da verdade) · historico.md
                   kommo-crm/.env · n8n/ · prompt/ · supabase/ · comercial/
empresa/           a própria <EMPRESA>: comercial, marketing, financeiro, operação
biblioteca/        material técnico reutilizável: workflows, modelos, documentação
software/          aplicativos próprios
.claude/           skills/ (INDICE.md) · agents/ · MAPA-DO-REPO.md · HISTORICO.md
```

Mapa completo em [.claude/MAPA-DO-REPO.md](.claude/MAPA-DO-REPO.md). Pasta nova relevante na raiz entra lá.

## Trabalhar num cliente

- O `CLAUDE.md` da pasta do cliente traz o contexto, as pegadinhas, o estado e as pendências. Leia antes de tocar em qualquer coisa dele.
- Depois, o `config.json`: IDs do CRM, endereços e nome dos arquivos de credencial. ID nunca fica só no chat.
- A chave já existe no `.env` do cliente: use pela variável, sem imprimir o valor.

  ```bash
  source clientes/<slug>/n8n/.env
  curl -s "$N8N_BASE_URL/api/v1/workflows/{id}" -H "X-N8N-API-KEY: $N8N_API_KEY"
  ```

- Mudança importante fechada: atualizar o `historico.md` e o bloco Estado/Pendências do `CLAUDE.md` do cliente.
- Cliente novo: copie `clientes/cliente-exemplo/` com o nome do cliente e preencha.

## Skills e agentes

- A lista de skills chega pela ferramenta Skill. Famílias e fronteiras entre vizinhas: [.claude/skills/INDICE.md](.claude/skills/INDICE.md).
- **Skill nova** (fez 2 vezes, vira skill): descrição de até 300 caracteres com "Use quando" e "Não é", e uma linha no `INDICE.md`.
- **Agentes** (`.claude/agents/`): `investigador` acha a causa com prova e não conserta; `provador` prova que a mudança funciona nos dois sentidos.

## Convenções

- `config.json` é a fonte da verdade. `historico.md` é obrigatório.
- `.env` nunca vai para o git. Token, senha e chave nunca são colados no chat nem em arquivo versionado.
- Pastas por cliente: `n8n/`, `prompt/`, `kommo-crm/`, `supabase/`, `comercial/`.
- Mudança cirúrgica em workflow do n8n: ler, mexer no nó, gravar. Não recriar o workflow inteiro.
- Commit e push só quando o dono pedir, em ramo próprio, estagiando arquivo a arquivo.

## Regras do OS

1. **Contexto:** todo cliente ativo tem `CLAUDE.md`; mudança importante atualiza `historico.md` e Estado/Pendências.
2. **Fez 2 vezes, vira skill.**
3. **Integração:** linha de comando própria, depois MCP, depois API direta com a documentação aberta.
4. **Credencial antes de código:** a credencial tem de existir e ter sido provada pelo uso antes de construir em cima dela.
5. **Automação é a última camada:** só automatiza o que já rodou manual algumas vezes sem correção.
6. **Tela nova não existe até ser clicada:** funciona de ponta a ponta, o desenho está certo no computador e no celular, e o que a tela mostra bate com o banco.
7. **Teste nasce marcado como teste** (`[QA]` no nome) e é limpo no fim.

## Como responder

Português do Brasil, curto e direto. A resposta vem primeiro, a explicação depois.

## Histórico

Mudanças do ambiente (skills, agentes, este arquivo) entram em [.claude/HISTORICO.md](.claude/HISTORICO.md).
