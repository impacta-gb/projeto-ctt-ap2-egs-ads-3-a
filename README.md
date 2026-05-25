# CTT AP2 - Documentacao Go com Zensical

Projeto em grupo para construcao de um site de documentacao da linguagem Go, com fluxo colaborativo estrito no GitHub e publicacao automatizada no GitHub Pages via GitHub Actions.

## Integrantes

- Gilberto Pereira dos Santos Junior - RA 2501533
- Samuel Mussato Flores - RA 2501486
- Eduardo Silva Oliveira - RA 2501142

## Objetivo

Entregar uma documentacao tecnica em Markdown sobre Go, com:

- Feature Branches para toda mudanca.
- Pull Requests obrigatorios para integracao na main.
- Code Review com aprovacao de pelo menos 1 integrante.
- Pipeline CI/CD com validacao, build e deploy automatizado.

## Estrutura da Documentacao

As paginas obrigatorias estao no diretorio [docs/index.md](docs/index.md):

- Introducao e Instalacao
- Sintaxe Basica e Variaveis
- Estruturas de Controle (If, For, Switch)
- Arrays, Slices e Maps
- Structs e Metodos
- Tratamento de Erros
- Concorrencia I: Goroutines
- Concorrencia II: Channels
- Gerenciamento de Pacotes (Go Modules)
- Testes Automatizados em Go

## Fluxo de Trabalho Colaborativo

1. Criar branch de feature a partir da main.
2. Implementar apenas uma mudanca por branch (exemplo: `feat/doc-goroutines`, `fix/yaml-cache`).
3. Abrir Pull Request para main.
4. Solicitar review de outro integrante.
5. Corrigir comentarios, receber `Approve` e entao realizar merge.

## Protecao da Branch Main (Obrigatorio)

No GitHub, configurar Branch Protection Rule para `main` com:

- Block pushes diretos na main.
- Require a pull request before merging.
- Require approvals: minimo de 1.
- Require status checks to pass before merging.

## CI/CD no GitHub Actions

Arquivo do workflow: [.github/workflows/docs.yml](.github/workflows/docs.yml)

### Triggers

- `pull_request` para `main`.
- `push` para `main`.
- `schedule` semanal com cron `0 0 * * 0`.

### Jobs

1. `validate`
	- Executa em matriz Python 3.10 e 3.11.
	- Usa cache de pip via `actions/cache`.
	- Executa `zensical build --clean --strict`.
2. `build_site`
	- Depende de `validate` (`needs`).
	- Gera o site estatico.
	- Publica artefato HTML via `actions/upload-artifact`.
3. `deploy_site`
	- Depende de `build_site` (`needs`).
	- Faz download do artefato com `actions/download-artifact`.
	- Publica no GitHub Pages.
	- Protegido com condicional: nao executa em Pull Request.

### Condicional de seguranca do deploy

O deploy so executa em `push` na `main` ou no `schedule` semanal.

## Execucao local

Instalar Zensical:

```bash
pip install zensical
```

Rodar servidor local:

```bash
zensical serve
```

Gerar build local:

```bash
zensical build --clean --strict
```

## Evidencias para Entrega

1. Link do repositorio publico.
2. Link do site publicado no GitHub Pages.
3. Historico de PRs fechados com reviews e aprovacoes.
4. Aba Actions mostrando:
	- Matriz Python (3.10 e 3.11).
	- Cache de dependencias.
	- Dependencia entre jobs (`needs`).
	- Build e deploy com artefatos.
