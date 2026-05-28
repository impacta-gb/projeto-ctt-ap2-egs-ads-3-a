
# Arrays, Slices e Maps

Essas são as principais estruturas para coleções em Go. Cada uma tem características e usos específicos.

## Arrays

Arrays têm tamanho fixo e tipo definido. O tamanho faz parte do tipo!

```go
var notas [3]int = [3]int{7, 8, 10}
fmt.Println(notas[0]) // 7
```

!!! warning "Atenção"
	Arrays em Go não são redimensionáveis. O tamanho é fixo após a declaração.

## Slices

Slices são "fatias" dinâmicas sobre arrays. São a estrutura de coleção mais usada em Go.

```go
valores := []int{10, 20, 30}
valores = append(valores, 40)
fmt.Println(valores) // [10 20 30 40]
```

Você pode criar slices a partir de arrays:

```go
arr := [5]int{1, 2, 3, 4, 5}
slc := arr[1:4] // [2 3 4]
```

!!! note "Referência compartilhada"
	Slices compartilham o array subjacente. Alterações em um slice podem afetar outros slices derivados do mesmo array.

## Maps

Maps armazenam pares chave-valor, ideais para buscas rápidas.

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

Você pode adicionar, remover e checar chaves facilmente:

```go
idades["Carlos"] = 30
delete(idades, "Luis")
_, existe := idades["Maria"]
```

## Comparativo rápido

| Estrutura | Tamanho   | Acesso por índice | Chave personalizada |
|-----------|-----------|-------------------|--------------------|
| Array     | Fixo      | Sim               | Não                |
| Slice     | Dinâmico  | Sim               | Não                |
| Map       | Dinâmico  | Não               | Sim                |

!!! tip "Dica de uso"
	Prefira slices para listas e maps para buscas por chave. Use arrays apenas quando o tamanho fixo for realmente necessário.

