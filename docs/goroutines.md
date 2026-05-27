# Concorrencia I: Goroutines

Goroutines sao funcoes executadas de forma concorrente e leve.

## Criando goroutines

```go
package main

import (
    "fmt"
    "time"
)

func tarefa(nome string) {
    for i := 1; i <= 3; i++ {
        fmt.Println(nome, "passo", i)
        time.Sleep(100 * time.Millisecond)
    }
}

func main() {
    go tarefa("A")
    go tarefa("B")

    time.Sleep(500 * time.Millisecond)
}
```

## Sincronizando com WaitGroup

```go
var wg sync.WaitGroup

wg.Add(2)
go func() {
    defer wg.Done()
    tarefa("A")
}()

go func() {
    defer wg.Done()
    tarefa("B")
}()

wg.Wait()
```

!!! warning "Evite time.Sleep como sincronizacao"
    `time.Sleep` pode falhar em cenarios reais. Prefira `sync.WaitGroup`
    ou `channels` para coordenacao correta.
