# Concorrencia II: Channels

Channels permitem comunicacao segura entre goroutines sem compartilhar
estado mutavel diretamente.

## Channel basico

```go
ch := make(chan string)

go func() {
    ch <- "mensagem pronta"
}()

msg := <-ch
fmt.Println(msg)
```

## Channel com buffer,

```go
fila := make(chan int, 2)
fila <- 10
fila <- 20

fmt.Println(<-fila)
fmt.Println(<-fila)
```

## Fechamento de channel

```go
valores := make(chan int)

go func() {
    defer close(valores)
    for i := 1; i <= 3; i++ {
        valores <- i
    }
}()

for v := range valores {
    fmt.Println(v)
}
```

!!! tip "Padrao fan-out/fan-in"
    Distribua trabalho para varias goroutines (fan-out) e consolide resultados
    em um unico channel (fan-in) para aumentar throughput.
