padroniza o estilo automaticamente.

# Sintaxe Básica e Variáveis

Go privilegia legibilidade, simplicidade e consistência. O formatador oficial `gofmt` padroniza o estilo automaticamente, tornando o código limpo e uniforme.

## Declaração de variáveis

Existem duas formas principais de declarar variáveis em Go:

```go
var nome string = "Ana" // declaração explícita
idade := 21             // inferência de tipo (forma curta)
ativo := true
```

Você pode declarar múltiplas variáveis de uma vez:

```go
var a, b int = 1, 2
x, y := 3.5, 7.2
```

## Tipos básicos

| Categoria         | Tipos comuns                |
|-------------------|----------------------------|
| Inteiros          | `int`, `int8`, `int64`, `uint` |
| Ponto flutuante   | `float32`, `float64`       |
| Texto             | `string`                   |
| Booleano          | `bool`                     |

## Constantes

Constantes são declaradas com `const`:

```go
const PI = 3.14159
const AppName string = "DocGo"
```

## Zero values (valores padrão)

Quando uma variável é declarada sem valor inicial, Go atribui um valor padrão:

```go
var i int       // 0
var f float64   // 0
var s string    // ""
var b bool      // false
```

!!! tip "Dica"
    Use sempre nomes de variáveis claros e descritivos.

## Escopo de variáveis

- Variáveis declaradas dentro de funções têm escopo local.
- Variáveis declaradas fora de funções pertencem ao pacote.

!!! warning "Evite variáveis globais sem necessidade"
    Prefira passar dependências por parâmetro para facilitar testes e manutenção.

## Conversão de tipos

Go não faz conversão automática entre tipos. Use casting explícito:

```go
var x int = 10
var y float64 = float64(x)
```

## Dicas de sintaxe

- O ponto e vírgula é opcional na maioria dos casos.
- O bloco de código sempre usa `{}`.
- O nome do arquivo principal deve ser `main.go` e conter a função `main()`.

