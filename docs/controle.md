
# Estruturas de Controle (If, For, Switch)

Go possui poucas, mas poderosas, estruturas de controle. Elas tornam o código simples, seguro e fácil de ler.

## If/Else

O `if` em Go é direto e pode conter inicialização de variáveis:

```go
if idade >= 18 {
	fmt.Println("Maior de idade")
} else {
	fmt.Println("Menor de idade")
}

if n := len(nome); n > 0 {
	fmt.Println("Nome válido")
}
```

!!! tip "Dica"
	Não use parênteses na condição do `if` em Go.

## For

Go só tem o laço `for`, que cobre todos os casos de repetição:

```go
// Clássico
for i := 0; i < 5; i++ {
	fmt.Println(i)
}

// While
for condicao {
	// executa enquanto condicao for verdadeira
}

// Loop infinito
for {
	// executa para sempre
	break // ou return para sair
}
```

!!! note "Range em coleções"
	Use `for index, valor := range colecao` para iterar sobre arrays, slices, maps e strings.

## Switch

O `switch` facilita múltiplas condições:

```go
switch dia {
case "sábado", "domingo":
	fmt.Println("Fim de semana")
case "segunda":
	fmt.Println("Início da semana")
default:
	fmt.Println("Dia útil")
}
```

!!! tip "Switch sem expressão"
	Um `switch` sem valor pode substituir cadeias longas de `if/else if`:
	```go
	switch {
	case idade < 12:
		fmt.Println("Criança")
	case idade < 18:
		fmt.Println("Adolescente")
	default:
		fmt.Println("Adulto")
	}
	```

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

