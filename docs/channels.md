fila <- 10
go func() {

# Concorrência II: Channels

Channels permitem comunicação segura entre goroutines, evitando o compartilhamento direto de memória. São fundamentais para sincronizar e transferir dados entre tarefas concorrentes.

## O que é um channel?

Um channel é uma via de comunicação tipada:

```go
ch := make(chan string) // channel de strings
```

## Channel básico

```go
ch := make(chan string)

go func() {
    ch <- "mensagem pronta"
}()

msg := <-ch
fmt.Println(msg) // "mensagem pronta"
```

## Channel com buffer

Channels podem ter buffer, permitindo enviar múltiplos valores sem bloqueio imediato:

```go
fila := make(chan int, 2)
fila <- 10
fila <- 20

fmt.Println(<-fila) // 10
fmt.Println(<-fila) // 20
```

## Fechamento de channel

Feche um channel para sinalizar que não haverá mais valores:

```go
valores := make(chan int)


    defer close(valores)
    for i := 1; i <= 3; i++ {
        valores <- i
    }
}()

for v := range valores {
    fmt.Println(v)
}
```

## Padrão fan-out/fan-in

Distribua trabalho para várias goroutines (fan-out) e consolide resultados em um único channel (fan-in) para aumentar throughput.

```go
entrada := make(chan int)
saida := make(chan int)

// Fan-out: múltiplas goroutines lendo de entrada
for i := 0; i < 3; i++ {
    go func() {
        for v := range entrada {
            saida <- v * 2
        }
    }()
}

// Fan-in: uma goroutine consolidando resultados
go func() {
    for i := 1; i <= 5; i++ {
        entrada <- i
    }
    close(entrada)
}()

for i := 1; i <= 5; i++ {
    fmt.Println(<-saida)
}
```

!!! tip "Dica"
    Prefira channels para sincronização e passagem de dados entre goroutines. Evite usar variáveis globais compartilhadas.
