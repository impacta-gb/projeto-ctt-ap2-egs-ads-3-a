# Goroutines em Go

Goroutines são funções que executam de forma concorrente (em paralelo leve).

Elas são iniciadas com a palavra-chave `go`.

## Exemplo básico

```go
package main

import (
    "fmt"
    "time"
)

func mensagem() {
    fmt.Println("Executando em goroutine")
}

func main() {
    go mensagem()

    fmt.Println("Executando função principal")

    time.Sleep(time.Second)
}

Explicação
go mensagem() executa a função em paralelo
time.Sleep é usado para esperar a goroutine terminar

Explicação
go mensagem() executa a função em paralelo
time.Sleep é usado para esperar a goroutine terminar
Múltiplas goroutines
for i := 0; i < 3; i++ {
    go func(i int) {
        fmt.Println("Goroutine:", i)
    }(i)
}

time.Sleep(time.Second)
Boas práticas
Usar sincronização (channels ou waitgroups)
Evitar concorrência sem controle

Boas práticas
Usar sincronização (channels ou waitgroups)
Evitar concorrência sem controle

!!! warning
Goroutines sem controle podem causar bugs difíceis.

!!! tip
Use channels para comunicação segura entre goroutines.