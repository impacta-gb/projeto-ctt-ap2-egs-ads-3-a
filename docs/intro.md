# Introducao e Instalacao

Go (ou Golang) e uma linguagem compilada criada para produtividade,
desempenho e simplicidade em sistemas modernos.

## Por que Go?

- Sintaxe simples e objetiva
- Compilacao rapida
- Excelente suporte a concorrencia
- Ferramental padrao muito forte (`go fmt`, `go test`, `go mod`)

## Instalacao

1. Acesse o site oficial: [go.dev/dl](https://go.dev/dl/)
2. Baixe a versao para seu sistema operacional.
3. Instale e confirme no terminal:

```bash
go version,
```

!!! note "Versao recomendada"
	Use uma versao estavel recente da serie 1.22+ (ou superior) para garantir
	compatibilidade com exemplos atuais.

## Primeiro programa

```go title="hello.go"
package main

import "fmt"

func main() {
	fmt.Println("Ola, Go!")
}
```

Execute com:

```bash
go run hello.go
```

## Estrutura minima de projeto

| Item | Funcao |
|---|---|
| `main.go` | Ponto de entrada da aplicacao |
| `go.mod` | Declaracao do modulo e dependencias |
| `go.sum` | Checksums para reproducao de build |

