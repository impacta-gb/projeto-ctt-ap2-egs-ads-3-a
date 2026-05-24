# Testes Automatizados em Go

Go possui suporte nativo para testes automatizados através do pacote `testing`.

Os testes são fundamentais para garantir a qualidade e o funcionamento correto do código.

---

## Estrutura de arquivos de teste

Os arquivos de teste devem terminar com `_test.go`.

Exemplo:

```text
calculadora.go
calculadora_test.go 

Criando um teste simples

Arquivo: calculadora.go

package main

func Soma(a, b int) int {
    return a + b
}


Arquivo: calculadora_test.go

package main

import "testing"

func TestSoma(t *testing.T) {
    resultado := Soma(2, 3)
    esperado := 5

    if resultado != esperado {
        t.Errorf("Esperado %d, mas obteve %d", esperado, resultado)
    }
}

Executando testes
go test 

Testes com múltiplos casos (Table Driven)
func TestSomaTabela(t *testing.T) {
    testes := []struct {
        a, b     int
        esperado int
    }{
        {2, 3, 5},
        {1, 1, 2},
        {0, 0, 0},
    }

    for _, teste := range testes {
        resultado := Soma(teste.a, teste.b)

        if resultado != teste.esperado {
            t.Errorf("Erro: esperado %d, obteve %d", teste.esperado, resultado)
        }
    }
}

## Testando erros

func Dividir(a, b int) (int, error) {
    if b == 0 {
        return 0, fmt.Errorf("divisão por zero")
    }
    return a / b, nil
}

func TestDividir(t *testing.T) {
    _, err := Dividir(10, 0)

    if err == nil {
        t.Error("Esperava erro ao dividir por zero")
    }
}

## Cobertura de testes

go test -cover

Mostra quanto do código está sendo testado. 

Boas práticas
Criar testes para todas as funções críticas
Usar nomes claros (TestNomeFuncao)
Testar casos de sucesso e erro
Manter testes simples e objetivos 

!!! warning
Código sem testes pode gerar bugs em produção.

!!! tip
Use testes automatizados para validar mudanças antes de subir o código.



