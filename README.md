# CTT AP2 - Documentacao Go com Zensical

Projeto de documentacao da linguagem Go desenvolvido com Zensical,
seguindo fluxo colaborativo com Feature Branches, Pull Requests,
Code Review obrigatorio e pipeline CI/CD no GitHub Actions.

## Integrantes

- Integrante 1 - Nome completo
- Integrante 2 - Nome completo
- Integrante 3 - Nome completo

## Objetivo do projeto

- Construir documentacao tecnica de Go em Markdown.
- Publicar automaticamente no GitHub Pages.
- Garantir qualidade com validacao em matriz de versoes Python.
- Aplicar boas praticas de colaboracao no GitHub.

## Estrutura de conteudo

O menu contem as 10 paginas obrigatorias:

1. Introducao e Instalacao
2. Sintaxe Basica e Variaveis
3. Estruturas de Controle (If, For, Switch)
4. Arrays, Slices e Maps
5. Structs e Metodos
6. Tratamento de Erros
7. Concorrencia I: Goroutines
8. Concorrencia II: Channels
9. Gerenciamento de Pacotes (Go Modules)
10. Testes Automatizados em Go

## Fluxo colaborativo (GitHub)

### Regra principal

Nao e permitido push direto na branch `main`.

### Padrao de branches

Cada tarefa deve usar branch dedicada, por exemplo:

- `feat/doc-goroutines`
- `feat/doc-channels`
- `fix/workflow-cache`

### Processo de contribuicao

1. Criar branch de feature a partir da `main`.
2. Implementar alteracoes e abrir Pull Request para `main`.
3. Aguardar execucao do workflow (validacao/build).
4. Receber review de pelo menos 1 integrante.
5. Ajustar comentarios (se houver) e somente entao fazer merge.

## Branch Protection (configuracao obrigatoria)

No GitHub, em `Settings > Branches > Add rule` para `main`, habilitar:

- `Require a pull request before merging`
- `Require approvals` (minimo: 1)
- `Dismiss stale pull request approvals when new commits are pushed`
- `Require status checks to pass before merging`
- `Do not allow bypassing the above settings` (para repositorios que suportam)

## CI/CD no GitHub Actions

Workflow: `.github/workflows/docs.yml`

### Triggers

- `pull_request` para `main`
- `push` para `main`
- `schedule` semanal (`0 0 * * 0`)

### Jobs e arquitetura

1. `validation`
	- Roda em matriz de Python `3.10` e `3.11`
	- Instala dependencias
	- Executa build para validar a documentacao

2. `build_site`
	- Executa apos `validation`
	- Gera a pasta `site/`
	- Envia artefato `site-html`

3. `deploy_site`
	- Depende de `build_site` (`needs`)
	- Baixa artefato `site-html`
	- Publica no GitHub Pages
	- Usa condicional `if` para nunca rodar em Pull Request

### Otimizacoes aplicadas

- Cache de pacotes pip com `actions/cache`
- Separacao clara entre validacao, build e deploy
- Reuso de artefato entre jobs (upload/download)

## Como rodar localmente

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
zensical serve
```

Build local:

```bash
zensical build --clean
```

## Entregaveis finais

1. Link do repositorio GitHub com documentacao e workflow.
2. Link do site publicado no GitHub Pages.
3. Evidencias de colaboracao (PRs, reviews e aprovacoes).
4. Evidencias do CI/CD na aba Actions (matriz, cache e dependencia entre jobs).
