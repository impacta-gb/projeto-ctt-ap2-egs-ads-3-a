
# Tratamento de Erros (Error Handling)

Em Go, erros são valores do tipo `error`. O padrão é retornar um erro como segundo valor e tratar explicitamente após cada chamada.

## Padrão básico

```go
func dividir(a, b float64) (float64, error) {
	if b == 0 {
		return 0, fmt.Errorf("divisão por zero")
	}
	return a / b, nil
}

resultado, err := dividir(10, 2)
if err != nil {
	log.Println("erro:", err)
	return
}
fmt.Println("resultado:", resultado)
```

## Wrapping de erros

Go permite "embrulhar" erros para dar mais contexto:

```go
if err != nil {
	return fmt.Errorf("falha ao ler configuração: %w", err)
}
```

## Criando erros personalizados

```go
var ErrUsuarioNaoEncontrado = errors.New("usuário não encontrado")

func buscarUsuario(id int) (Usuario, error) {
	// ...
	return Usuario{}, ErrUsuarioNaoEncontrado
}
```

## Boas práticas

- Sempre trate o erro logo após a chamada.
- Mensagens de erro devem dar contexto.
- Evite ignorar erro com `_` sem motivo forte.
- Use erros personalizados para casos comuns de falha.

!!! warning "Panic não substitui error"
	`panic` deve ser reservado para falhas irrecuperáveis (ex: bugs, corrupção de memória). Para regras de negócio e validações comuns, retorne `error`.

!!! tip "Dica"
	Use a função `errors.Is` e `errors.As` para comparar e extrair erros embrulhados.

