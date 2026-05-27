# Introducao e Instalacao do Go

Go (Golang) e uma linguagem compilada criada para ser simples, eficiente e produtiva.

## Por que estudar Go

- Sintaxe limpa e direta.
- Compilacao rapida.
- Excelente suporte para concorrencia.
- Muito usado em backend, APIs e ferramentas de infraestrutura.

## Instalacao

Baixe no site oficial:

- https://go.dev/dl/

Depois de instalar, confira no terminal:

```bash
go version
```

Saida esperada (exemplo):

```text
go version go1.22.4 darwin/arm64
```

## Criando um projeto

```bash
mkdir meu-projeto-go
cd meu-projeto-go
go mod init meu-projeto-go
```

## Primeiro programa

```go
package main

import "fmt"

func main() {
    fmt.Println("Ola, Go!")
}
```

Executar:

```bash
go run main.go
```

Compilar:

```bash
go build
```

!!! note
Hoje, a forma recomendada de iniciar projeto Go e com Go Modules (`go mod init`).
