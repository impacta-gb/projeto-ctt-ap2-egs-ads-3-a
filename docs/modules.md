# Gerenciamento de Pacotes em Go (Go Modules)

Go Modules é o sistema oficial de gerenciamento de dependências do Go.

Ele permite organizar, versionar e compartilhar código de forma simples.

---

## Inicializando um módulo

Para iniciar um projeto com módulos:

```bash
go mod init meu-projeto

Isso cria o arquivo go.mod.

Arquivo go.mod

Exemplo:

module meu-projeto

go 1.21
Explicação
module: nome do projeto
go: versão da linguagem

Adicionando dependências

Quando você importa um pacote externo:

import "github.com/gin-gonic/gin"

Depois execute:

go mod tidy

Isso:

baixa dependências
atualiza o go.mod
cria o go.sum
Arquivo go.sum

Contém hashes de segurança das dependências.

👉 garante integridade dos pacotes

Atualizando dependências
go get -u

Ou específico:

go get github.com/gin-gonic/gin@latest
Removendo dependências não utilizadas
go mod tidy

Estrutura do projeto
meu-projeto/
 ├── go.mod
 ├── go.sum
 ├── main.go
 
Exemplo completo

package main

import (
    "fmt"
)

func main() {
    fmt.Println("Projeto com Go Modules")
}

Boas práticas
Sempre usar go mod tidy
Versionar go.mod e go.sum
Evitar dependências desnecessárias

!!! warning
Não versionar o go.mod pode quebrar o projeto em outras máquinas.

!!! tip
Use nomes de módulo claros e padronizados.

