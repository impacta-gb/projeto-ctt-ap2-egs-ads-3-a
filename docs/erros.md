# Tratamento de Erros

Em Go, erros sao valores. O padrao e retornar `error` e tratar explicitamente.

## Padrao basico

```go
func dividir(a, b float64) (float64, error) {
	if b == 0 {
		return 0, fmt.Errorf("divisao por zero")
	}
	return a / b, nil
}
```

Uso:

```go
resultado, err := dividir(10, 2)
if err != nil {
	log.Println("erro:", err)
	return
}
fmt.Println("resultado:", resultado)
```

## Wrapping de erros

```go
if err != nil {
	return fmt.Errorf("falha ao ler configuracao: %w", err)
}
```

## Boas praticas

- Trate erro logo apos a chamada.
- Mensagens de erro devem dar contexto.
- Evite ignorar erro com `_` sem motivo forte.

!!! warning "Panic nao substitui error"
	`panic` deve ser reservado para falhas irrecuperaveis. Para regras de
	negocio e validacoes comuns, retorne `error`.

