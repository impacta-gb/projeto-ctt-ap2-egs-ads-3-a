desempenho e simplicidade em sistemas modernos.

# Introdução e Instalação

Go (ou Golang) é uma linguagem de programação compilada, criada pela Google, focada em simplicidade, desempenho e concorrência eficiente. É muito usada em sistemas distribuídos, servidores web, automação e ferramentas de infraestrutura.

## Por que aprender Go?

- **Sintaxe clara e objetiva**: fácil de ler e manter.
- **Compilação rápida**: feedback imediato.
- **Concorrência poderosa**: goroutines e channels facilitam o paralelismo.
- **Ferramentas integradas**: `go fmt`, `go test`, `go mod` e outras já vêm prontas.
- **Desempenho próximo de C/C++**: ideal para aplicações de alta performance.

## Instalação do Go

1. Acesse o site oficial: [go.dev/dl](https://go.dev/dl/)
2. Baixe o instalador para seu sistema operacional (Windows, macOS ou Linux).
3. Siga as instruções do instalador.
4. Após instalar, abra o terminal e digite:

```bash
go version
```

Se aparecer algo como `go version go1.22.3 darwin/amd64`, está tudo certo!

!!! tip "Dica de ambiente"
	No Linux, prefira instalar via gerenciador de pacotes oficial ou Snap.

!!! note "Versão recomendada"
	Use sempre uma versão estável recente (1.22 ou superior).

## Seu primeiro programa em Go

Crie um arquivo chamado `hello.go` com o seguinte conteúdo:

```go title="hello.go"
package main

import "fmt"

func main() {
	fmt.Println("Olá, Go!")
}
```

Execute no terminal:

```bash
go run hello.go
```

Você verá:

```
Olá, Go!
```

## Estrutura mínima de um projeto Go

| Arquivo   | Função                                 |
|-----------|----------------------------------------|
| main.go   | Ponto de entrada da aplicação          |
| go.mod    | Declaração do módulo e dependências    |
| go.sum    | Checksums para reprodução de builds    |

!!! tip "Próximos passos"
	Explore os comandos `go help`, `go doc` e a documentação oficial para aprender mais sobre o ecossistema Go.

