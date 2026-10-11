Esta pasta é um esqueleto de repositório de operação que acabei de baixar. Quero que você termine a montagem comigo. Leia primeiro o LEIA-ME.md e o CLAUDE.md inteiros.

Depois faça nesta ordem, um passo por vez:

1. Confira o ambiente e me diga o que falta, sem instalar nada sozinho: `git --version`, `python --version` (ou `python3`), `node --version`. Diga também em qual sistema estou (Windows, macOS ou Linux).

2. Me faça estas perguntas, todas de uma vez, e espere a resposta:
   - nome da empresa;
   - o que ela vende e para quem, em uma frase;
   - quais ferramentas eu uso (CRM, automação, banco, anúncios, WhatsApp);
   - quem trabalha no repositório além de mim;
   - nome de um cliente real para ser o primeiro, ou "nenhum por enquanto".

3. Com as respostas, preencha o CLAUDE.md: troque todo `<EMPRESA>` pelo nome, ajuste a primeira frase, e na seção "Onde as coisas estão" e nas convenções deixe só as ferramentas que eu uso. Não invente regra nova e não apague as Regras do OS. Faça o mesmo no `.claude/MAPA-DO-REPO.md`.

4. Git: se a pasta veio de um clone, rode `git remote -v` e, se o `origin` for o repositório do esqueleto, desligue com `git remote remove origin` (o repositório passa a ser só meu; não tente enviar nada para lá). Se não houver git, inicie (`git init`, ramo `main`). Antes do primeiro commit, confirme que nenhum arquivo `.env` aparece em `git status`. Faça o primeiro commit só depois de me mostrar a lista de arquivos e eu dizer que pode.

5. Se eu dei um cliente: copie `clientes/cliente-exemplo/` para `clientes/<nome-em-minusculas-com-hifen>/`, crie o `CLAUDE.md` dele com as seções Contexto, Pegadinhas, Estado e Pendências, e zere o `config.json` (deixe os campos, tire os valores fictícios). Renomeie cada `.env.exemplo` para `.env` e me diga quais chaves eu preciso preencher e onde consigo cada uma. Eu preencho no arquivo: nunca me peça para colar chave aqui na conversa.

6. Registre o que foi feito em `.claude/HISTORICO.md`, com a data de hoje.

Regras:
- Não leia nem imprima o conteúdo de arquivo `.env`.
- Não instale programa, extensão ou pacote sem me perguntar.
- Não crie pasta nem arquivo fora desta estrutura.
- Se um passo falhar, pare e me mostre o erro inteiro.

No fim, me diga: o que ficou pronto, o que depende de mim (chaves a preencher, programa a instalar) e a pergunta que eu devo fazer numa conversa nova para testar se o CLAUDE.md está sendo lido.
