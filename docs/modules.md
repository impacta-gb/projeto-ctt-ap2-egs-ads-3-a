
# Gerenciamento de Pacotes (Go Modules)

Go Modules é o sistema oficial para gerenciar dependências e versões em projetos Go. Ele permite reprodutibilidade, controle de versões e fácil integração de pacotes externos.

## Inicializando um módulo

No diretório do seu projeto, execute:

```bash
go mod init github.com/sua-org/seu-projeto
```

Isso cria o arquivo `go.mod`, que define o nome do módulo e as dependências.

## Adicionando dependências

Basta importar o pacote no seu código e rodar um comando de build ou test. O Go irá baixar e registrar a dependência automaticamente:

```go
import "github.com/google/uuid"
```

```bash
go get github.com/google/uuid
```

## Arquivos importantes

| Arquivo   | Papel                                      |
|-----------|---------------------------------------------|
| go.mod    | Define módulo e versões de dependência      |
| go.sum    | Registra checksums para reprodutibilidade   |

## Comandos úteis

```bash
go mod tidy      # remove dependências não usadas e inclui faltantes
go mod download  # baixa todas as dependências
go list -m all   # lista todos os módulos usados
```

!!! note "Boa prática"
    Execute `go mod tidy` antes de abrir Pull Request para manter o projeto limpo e reprodutível.

## Atualizando dependências

```bash
go get -u ./...
```

## Dicas

- Sempre versionar `go.mod` e `go.sum` no controle de versão.
- Use módulos para qualquer projeto Go, mesmo scripts pequenos.
