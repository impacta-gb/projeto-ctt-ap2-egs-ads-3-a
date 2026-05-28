# Arrays, Slices e Maps

Essas sao estruturas fundamentais para trabalhar com colecoes em Go.

## Arrays

Array tem tamanho fixo definido na declaracao.

```go
var numeros [3]int
numeros[0] = 10
numeros[1] = 20
numeros[2] = 30
```

## Slices

Slices sao dinamicos e aparecem muito mais em projetos reais.

```go
idades := []int{18, 25, 32}
idades = append(idades, 40)
```

Criando com `make`:

```go
valores := make([]int, 2, 5)
```

## Maps

Map guarda pares `chave -> valor`.

```go
notas := map[string]float64{
    "Ana":   9.5,
    "Bruno": 8.0,
}
```

Verificando se a chave existe:

```go
nota, ok := notas["Carlos"]
if !ok {
    fmt.Println("aluno nao encontrado")
} else {
    fmt.Println(nota)
}
```

Remocao:

```go
delete(notas, "Bruno")
```

!!! note
    A iteracao em map nao garante ordem.
