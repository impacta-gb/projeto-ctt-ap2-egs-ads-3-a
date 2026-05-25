# Structs e Metodos

Structs sao usadas para organizar dados relacionados em um unico tipo.

## Criando uma struct

```go
type Pessoa struct {
    Nome  string
    Idade int
}
```

## Criando instancias

```go
p1 := Pessoa{Nome: "Ana", Idade: 30}
p2 := Pessoa{"Bruno", 22}
```

## Metodos

Metodo com receptor por valor:

```go
func (p Pessoa) Saudacao() string {
    return "Ola, meu nome e " + p.Nome
}
```

Metodo com receptor ponteiro (altera estado):

```go
func (p *Pessoa) FazerAniversario() {
    p.Idade++
}
```

## Struct aninhada

```go
type Endereco struct {
    Cidade string
    Estado string
}

type Cliente struct {
    Nome     string
    Endereco Endereco
}
```

## Tags em structs

```go
type Usuario struct {
    ID    int    `json:"id"`
    Email string `json:"email"`
}
```

!!! tip
Use receptor ponteiro quando precisar modificar o estado da struct.
