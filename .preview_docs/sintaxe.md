# Sintaxe Basica e Variaveis

A sintaxe do Go foi pensada para manter o codigo legivel e padronizado.

## Estrutura minima

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, Go")
}
```

## Variaveis e constantes

```go
var nome string = "Eduardo"
idade := 21
const linguagem = "Go"
```

- `var` permite declarar com tipo explicito.
- `:=` faz declaracao curta dentro de funcao.
- `const` define valor imutavel.

## Tipos mais comuns

| Tipo | Exemplo |
| --- | --- |
| int | `10` |
| float64 | `3.14` |
| string | `"texto"` |
| bool | `true` |

## Funcoes

```go
func Somar(a int, b int) int {
    return a + b
}
```

Retorno multiplo:

```go
func Dividir(a, b float64) (float64, error) {
    if b == 0 {
        return 0, fmt.Errorf("divisao por zero")
    }
    return a / b, nil
}
```

## Comentarios

```go
// comentario de uma linha

/* comentario
   em varias linhas */
```

!!! tip
Use `go fmt` com frequencia para manter o estilo oficial da linguagem.
