# Sintaxe Basica e Variaveis

Go privilegia legibilidade e consistencia. O formatador oficial `gofmt`
padroniza o estilo automaticamente.

## Declaracao de variaveis

```go
package main

import "fmt"

func main() {
	var nome string = "Ana"
	idade := 21
	ativo := true

	fmt.Println(nome, idade, ativo)
}
```

## Tipos basicos

| Categoria | Tipos comuns |
|---|---|
| Inteiros | `int`, `int64`, `uint` |
| Ponto flutuante | `float32`, `float64` |
| Texto | `string` |
| Booleano | `bool` |

## Constantes

```go
const PI = 3.14159
const AppName string = "DocGo"
```

## Escopo

- Variaveis declaradas dentro de funcoes tem escopo local.
- Variaveis declaradas fora de funcoes pertencem ao pacote.

!!! warning "Evite variaveis globais sem necessidade"
	Prefira passar dependencias por parametro para facilitar testes e manutencao.

## Zero values

Quando uma variavel e declarada sem inicializacao, Go atribui um valor padrao:

```go
var i int       // 0
var f float64   // 0
var s string    // ""
var b bool      // false
```

