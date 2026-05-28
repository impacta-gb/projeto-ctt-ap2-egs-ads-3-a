
# Concorrência I: Goroutines

Goroutines são funções ou métodos executados de forma concorrente e leve. Elas são a base da concorrência em Go e permitem criar milhares de tarefas paralelas com baixo custo.

## O que é uma goroutine?

Uma goroutine é criada usando a palavra-chave `go` antes de uma chamada de função:

```go
go minhaFuncao()
```

## Exemplo prático

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

    time.Sleep(500 * time.Millisecond) // Aguarda goroutines terminarem
}
```

!!! warning "Evite time.Sleep para sincronização"
    `time.Sleep` pode falhar em cenários reais. Prefira `sync.WaitGroup` ou `channels` para coordenação correta.

## Sincronizando goroutines com WaitGroup

O pacote `sync` oferece o tipo `WaitGroup` para aguardar múltiplas goroutines:

```go
import "sync"

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

wg.Wait() // Aguarda todas as goroutines terminarem
```

!!! tip "Dica"
    Use sempre `wg.Add` antes de iniciar as goroutines e `wg.Done` ao final de cada uma.

## Quando usar goroutines?

- Processamento paralelo (ex: downloads, cálculos, servidores web)
- Tarefas assíncronas (ex: timers, workers)

Goroutines são leves, mas não substituem processos do sistema operacional para isolamento forte.
