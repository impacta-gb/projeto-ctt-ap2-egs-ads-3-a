# Estruturas de Controle

Go possui poucas estruturas de controle, mas muito poderosas.

## If

```go
if idade >= 18 {
	fmt.Println("Maior de idade")
} else {
	fmt.Println("Menor de idade")
}
```

Tambem e possivel inicializar variavel dentro do `if`:

```go
if n := len(nome); n > 0 {
	fmt.Println("Nome valido")
}
```

## For

Go usa apenas `for`, cobrindo os papeis de `while` e `do-while`.

```go
for i := 0; i < 5; i++ {
	fmt.Println(i)
}
```

```go
for condicao {
	// equivalente a while
}
```

```go
for {
	// loop infinito
	break
}
```

## Switch

```go
switch dia {
case "sabado", "domingo":
	fmt.Println("Fim de semana")
case "segunda":
	fmt.Println("Inicio da semana")
default:
	fmt.Println("Dia util")
}
```

!!! tip "Switch sem expressao"
	Um `switch` sem valor pode substituir cadeias longas de `if/else if`.

```go
switch {
case nota >= 9:
	fmt.Println("Excelente")
case nota >= 7:
	fmt.Println("Bom")
default:
	fmt.Println("Precisa melhorar")
}
```

