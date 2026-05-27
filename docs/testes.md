# Testes Automatizados em Go

Go traz suporte nativo a testes com o pacote `testing`.

## Estrutura de arquivo

Arquivos de teste seguem o padrao `*_test.go`.

```go title="soma.go"
package calc

func Soma(a, b int) int {
    return a + b
}
```

```go title="soma_test.go"
package calc

import "testing"

func TestSoma(t *testing.T) {
    got := Soma(2, 3)
    want := 5

    if got != want {
        t.Fatalf("Soma(2,3) = %d; want %d", got, want)
    }
}
```

Execute:

```bash
go test ./...
```

## Cobertura

```bash
go test ./... -cover
```

## Testes em tabela

```go
func TestPar(t *testing.T) {
    casos := []struct {
        n    int
        want bool
    }{
        {2, true},
        {3, false},
        {10, true},
    }

    for _, c := range casos {
        got := c.n%2 == 0
        if got != c.want {
            t.Fatalf("n=%d got=%v want=%v", c.n, got, c.want)
        }
    }
}
```

!!! tip "Regra de ouro"
    Cada bug corrigido deve ganhar um teste para evitar regressao futura.
