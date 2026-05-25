# Concorrencia II: Channels

Channels sao a forma mais usada em Go para trocar dados entre goroutines com seguranca.

## Channel sem buffer

```go
ch := make(chan int)

go func() {
    ch <- 10
}()

valor := <-ch
fmt.Println(valor)
```

Nesse caso, envio e recebimento se sincronizam.

## Channel com buffer

```go
fila := make(chan string, 2)

fila <- "job-1"
fila <- "job-2"

fmt.Println(<-fila)
fmt.Println(<-fila)
```

Com buffer, o envio nao bloqueia enquanto houver espaco.

## Fechando channel e usando range

```go
ch := make(chan int)

go func() {
    for i := 0; i < 3; i++ {
        ch <- i
    }
    close(ch)
}()

for v := range ch {
    fmt.Println(v)
}
```

## Direcao de channels

```go
func produtor(out chan<- int) {
    out <- 42
    close(out)
}

func consumidor(in <-chan int) {
    for v := range in {
        fmt.Println(v)
    }
}
```

!!! warning
Deadlock acontece quando as goroutines ficam esperando envio/recebimento que nao acontece.

!!! tip
Feche o channel no lado produtor e evite fechar o mesmo channel mais de uma vez.
