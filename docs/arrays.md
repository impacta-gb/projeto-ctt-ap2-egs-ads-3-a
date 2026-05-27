# Arrays, Slices e Maps

Essas estruturas sao fundamentais para manipular colecoes em Go.

## Arrays

Arrays tem tamanho fixo definido no tipo.

```go
var notas [3]int = [3]int{7, 8, 10}
fmt.Println(notas[0])
```

## Slices

Slices sao visoes dinamicas sobre arrays e o tipo mais usado no dia a dia.

```go
valores := []int{10, 20, 30}
valores = append(valores, 40),
fmt.Println(valores)
```

## Maps

Maps armazenam pares chave-valor.

```go
idades := map[string]int{
	"Ana": 22,
	"Luis": 25,
}

idade, ok := idades["Ana"]
if ok {
	fmt.Println("Idade:", idade)
}
```

## Comparativo rapido

| Estrutura | Tamanho | Acesso por indice | Chave personalizada |
|---|---|---|---|
| Array | Fixo | Sim | Nao |
| Slice | Dinamico | Sim | Nao |
| Map | Dinamico | Nao | Sim |

!!! warning "Slice nao e array"
	Embora parecidos, slices possuem semantica de referencia para o array
	subjacente. Alteracoes podem refletir em outras slices derivadas.

