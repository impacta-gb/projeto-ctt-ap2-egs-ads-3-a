# Gerenciamento de Pacotes (Go Modules)

Go Modules e o sistema oficial para gerenciar dependencias.

## Inicializando modulo

```bash
go mod init github.com/sua-org/seu-projeto
``` ,

Isso cria o arquivo `go.mod`.

## Adicionando dependencias

Quando voce importa um pacote externo e roda build/test, Go atualiza o modulo.

```bash
go get github.com/google/uuid
```

## Arquivos importantes

| Arquivo | Papel |
|---|---|
| `go.mod` | Define modulo e versoes de dependencia |
| `go.sum` | Registra checksums para reproducibilidade |

## Comandos uteis

```bash
go mod tidy      # remove deps nao usadas e inclui faltantes
go mod download  # baixa dependencias
go list -m all   # lista modulos
```

!!! note "Boa pratica"
    Execute `go mod tidy` antes de abrir Pull Request para manter o projeto limpo.
