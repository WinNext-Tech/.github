# WinNext-Tech/.github

Repositório especial da organização. O GitHub usa os arquivos daqui como **padrão para todos os
repositórios da org** que não tiverem os seus próprios.

> ⚠️ Este repositório precisa ser **público** — o GitHub só aplica os arquivos padrão
> (templates de issue/PR, CONTRIBUTING, SECURITY) a partir de um `.github` público.
> Não coloque aqui nada interno ou sensível. O que é só para o time vai em `.github-private`.

## O que tem aqui

| Caminho | Para quê |
| --- | --- |
| `profile/README.md` | Página pública da organização (github.com/winnext) |
| `CONTRIBUTING.md` | Como trabalhamos: branches, commits, PRs, review, merge |
| `SECURITY.md` | Como reportar uma vulnerabilidade |
| `.github/ISSUE_TEMPLATE/` | Formulários de issue (bug e feature) usados por todos os repos |
| `.github/pull_request_template.md` | Template de PR usado por todos os repos |
| `.github/workflows/ci-node.yml` | **Workflow reutilizável** de CI para projetos Node (npm ou pnpm) |
| `.github/workflows/pr-title.yml` | **Workflow reutilizável** que valida o título do PR (Conventional Commits) |

## Usando os workflows reutilizáveis

Em qualquer repo da org, crie `.github/workflows/ci.yml` (o `template-base` já vem com isso):

```yaml
name: ci
on:
  pull_request:
  push:
    branches: [main]
permissions:
  contents: read
jobs:
  ci:
    uses: WinNext-Tech/.github/.github/workflows/ci-node.yml@main
    # with:
    #   working-directory: apps/web   # para monorepos
    #   scripts: "lint typecheck test build"
```

O CI detecta npm ou pnpm pelo lockfile, usa a versão do Node do `.nvmrc`/`.node-version`
(ou Node 24) e roda os scripts `lint`, `typecheck`, `test` e `build` que existirem no `package.json`.

> Mudanças aqui afetam todos os repos que usam `@main`. Para mudanças grandes, crie uma tag
> (`v1`, `v2`) e migre os repos aos poucos.
