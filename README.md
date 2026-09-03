# Snova.Std — Biblioteca Padrão e Gerenciador de Módulos Snovalang

Repositório oficial da **Standard Library (`Snova.Std`)** e do **Gerenciador de Dependências (`snova-mod`)** para a linguagem Snovalang.

---

## 1. Estrutura de Módulos

O pacote segue o namespace padronizado `Snova.Std.*`:

| Módulo | Caminho do Pacote | Responsabilidade |
|---|---|---|
| **I/O** | `Snova.Std.IO` | Contratos `Reader`, `Writer`, `Closer`, `ByteBuffer`, cópia e streaming de dados. |
| **Serialization** | `Snova.Std.Serialization` | Árvore universal `DataNode`, codificador/formatador JSON e binário. |
| **HTTP** | `Snova.Std.Http` | `HttpRequest`, `HttpResponse`, `HeaderMap`, códigos de status e clientes HTTP. |
| **LSP** | `Snova.Std.Lsp` | Protocolo JSON-RPC 2.0, frames `Content-Length`, `Diagnostic`, `Range`, `Position`. |
| **Modules & Git** | `Snova.Std.Mod` | Parser de `snova.mod`, resolução SemVer (`v1.0.0`) e provedores Git (`github.com`, etc.). |

---

## 2. Gestão de Dependências (Estilo Go Modules)

O Snovalang adota o modelo de versionamento canônico baseado em URLs de provedores Git e versionamento semântico (SemVer), idêntico ao Go (`go.mod`).

### Arquivo `snova.mod`

```snova
module github.com/aggitech/snova-std

snova 1.0.0

require (
    github.com/supernova/snova-crypto v1.2.0
    gitlab.com/org/snova-sql v0.4.1 // indirect
)
```

### Comandos do CLI `snova-mod`

```bash
# Inicializar um novo módulo
snova-mod init github.com/minha-empresa/meu-app

# Baixar todas as dependências declaradas em snova.mod
snova-mod download

# Baixar um pacote específico com tag semver
snova-mod download github.com/supernova/snova-crypto@v1.2.0

# Copiar dependências locais para a pasta vendor (.snovalang/deps)
snova-mod vendor

# Limpar e sincronizar dependências
snova-mod tidy
```

### Cache de Dependências

Os pacotes baixados são mantidos de forma imutável e isolada no cache do usuário:
`~/.snova/pkg/mod/<host>/<org>/<repo>@<version>`

---

## 3. Como Construir

```bash
# Compilar o utilitário snova-mod
make

# Verificar sintaxe de todos os pacotes .snova
../snovac/build/snovac --check-parse src/IO/IO.snova
../snovac/build/snovac --check-parse src/Serialization/Serialization.snova
../snovac/build/snovac --check-parse src/Http/Http.snova
../snovac/build/snovac --check-parse src/Mod/Mod.snova
../snovac/build/snovac --check-parse src/Lsp/Lsp.snova
```
