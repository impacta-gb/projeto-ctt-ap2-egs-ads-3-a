# Structs e Metodos

Structs permitem modelar dados compostos. Metodos adicionam comportamento
associado a esses dados.

## Declarando uma struct

```go
type Usuario struct {
	Nome  string
	Email string
	Ativo bool
}
```

## Criando instancias

```go
u1 := Usuario{Nome: "Maria", Email: "maria@email.com", Ativo: true}
u2 := Usuario{"Joao", "joao@email.com", false}
fmt.Println(u1, u2)
```

## Metodos

```go
type Conta struct {
	Saldo float64
}

func (c Conta) ExibirSaldo() float64 {
	return c.Saldo
}

func (c *Conta) Depositar(valor float64) {
	c.Saldo += valor
}
```

No exemplo acima:

- `ExibirSaldo` usa receiver por valor
- `Depositar` usa receiver por ponteiro para modificar estado

!!! tip "Quando usar ponteiro"
	Use receiver por ponteiro quando o metodo precisa alterar campos da struct
	ou quando deseja evitar copia de estruturas grandes.

