# Como trabalhamos

Vale para todos os repositórios da WinNext, a menos que o repo tenha o próprio `CONTRIBUTING.md`.

## Fluxo em uma linha

`issue` → branch a partir da `main` → commits pequenos → **PR** → review + CI verde → **squash merge** → branch apagada.

Ninguém faz push direto na `main` (o ruleset da organização bloqueia).

## Branches

Formato: `tipo/descricao-curta`, em minúsculas e com hífens.

```
feat/login-google
fix/timeout-upload
chore/atualiza-deps
```

## Commits — Conventional Commits

```
<tipo>(<escopo opcional>): <descrição>
```

- **Tipos:** `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`
- **Descrição:** em português, verbo no presente, minúscula, sem ponto final, até ~72 caracteres
- **Escopo:** a área afetada (`auth`, `checkout`, `api`, `ui`…)
- **Breaking change:** `!` depois do tipo/escopo e rodapé `BREAKING CHANGE: ...`

```
feat(auth): adiciona login com Google
fix(api): corrige timeout no upload de arquivos grandes
refactor(checkout)!: troca cálculo de frete para a nova API
```

> Usamos **squash merge**: o **título do PR** vira a mensagem do commit na `main`, então ele
> precisa seguir esse padrão (o CI valida). Os commits intermediários da branch podem ser livres.

## Pull requests

- **Pequenos:** mire em menos de ~400 linhas alteradas. PR grande demora para revisar e esconde bug.
- **Rascunho (draft)** enquanto estiver em andamento.
- Preencha o template: o que muda, por quê, como testar, evidências (prints para UI).
- Vincule a issue no corpo: `Closes #123`.
- Precisa de **1 aprovação** e do **CI verde**. Resolva todas as conversas antes do merge.
- Use **auto-merge** quando estiver só esperando o CI.

## Code review

- Responda pedidos de review em até **1 dia útil**.
- Revise o código, não a pessoa. Explique o porquê e, quando possível, sugira o código.
- Prefixos ajudam a calibrar: `bloqueante:`, `sugestão:`, `nit:` (detalhe opcional), `dúvida:`.
- Aprove quando estiver bom o suficiente — perfeito é inimigo do entregue.

## Interface (UI)

Toda UI segue o `DESIGN.md` do repositório [`WinNext-Tech/brand`](https://github.com/WinNext-Tech/brand):
use os tokens (cores, tipografia, espaçamento), nunca cores ou tamanhos “soltos” no código.

## Assistentes de IA

- Cada repo tem um `AGENTS.md` com o contexto do projeto (stack, comandos, convenções).
  Mantenha-o atualizado: ele é lido pelo Claude Code e por outras ferramentas.
- As skills do time ficam em [`WinNext-Tech/skills`](https://github.com/WinNext-Tech/skills).
- Você é responsável por todo código que sobe, inclusive o gerado por IA: revise antes do PR.
