# Channels em Go

Channels são usados para comunicação entre goroutines de forma segura.

Eles permitem enviar e receber dados entre funções concorrentes.

## Criando um channel

```go
package main

import "fmt"

func main() {
    ch := make(chan int)

    go func() {
        ch <- 10
    }()

    valor := <-ch
    fmt.Println("Valor recebido:", valor)
}

Explicação
make(chan int) cria um canal
ch <- 10 envia valor
<-ch recebe valor
Channel com buffer

ch := make(chan int, 2)

ch <- 1
ch <- 2

fmt.Println(<-ch)
fmt.Println(<-ch)

Usando range em channels

func main() {
    ch := make(chan int)

    go func() {
        for i := 0; i < 3; i++ {
            ch <- i
        }
        close(ch)
    }()

    for valor := range ch {
        fmt.Println(valor)
    }
}

Boas práticas
Sempre fechar canais quando não forem mais usados
Evitar deadlocks (travamentos)
Usar channels para comunicação entre goroutines

!!! warning
Deadlock ocorre quando nenhuma goroutine consegue continuar a execução.

!!! tip
Channels ajudam a evitar problemas de concorrência.