 
# Testes Automatizados em Go

Go traz suporte nativo a testes com o pacote `testing`, tornando fácil validar o comportamento do seu código.

## Estrutura de arquivos de teste

Arquivos de teste seguem o padrão `*_test.go` e ficam no mesmo pacote do código testado.

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

## Executando testes

Basta rodar:

```bash
go test ./...
```

## Cobertura de testes

Veja o percentual de código coberto por testes:

```bash
go test ./... -cover
```

## Testes em tabela

Testes em tabela facilitam múltiplos cenários:

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

## Dicas

- Use nomes descritivos para funções de teste: `TestNomeFuncao`.
- Use `t.Run` para subtestes.
- Use `go test -v` para saída detalhada.
        }
    }
}
```

!!! tip "Regra de ouro"
    Cada bug corrigido deve ganhar um teste para evitar regressao futura.
