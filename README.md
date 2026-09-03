# Snova.Std — Snovalang Standard Library

The official **Standard Library (`Snova.Std`)** for the Snovalang programming language, written 100% in pure Snovalang.

## Documentation Standard

Every function, method, struct, class, and property in `Snova.Std` is documented using the standard Snovalang Doc format:

```snova
/* -- Doc:{funcName}
 *
 * -- Description: Explains what the declaration does and how it behaves.
 *
 * -- Param{paramName}: Description of the parameter.
 * -- Returns: Description of the returned result.
 */
```

## Module Overview

| Module | Package Path | Description |
|---|---|---|
| **IO** | `Snova.Std.IO` | `Reader`, `Writer`, `Closer` contracts, in-memory `ByteBuffer`, stream `copy`. |
| **Serialization** | `Snova.Std.Serialization` | `DataNode` universal AST, RFC 8259 compliant `JsonSerializer` & `JsonParser`. |
| **HTTP** | `Snova.Std.Http` | `HttpRequest`, `HttpResponse`, `HeaderMap`, HTTP methods and status helpers. |
| **Collections** | `Snova.Std.Collections` | `List` (ArrayList), `Map` (hash table dictionary), `Set`, `Queue`. |
| **Strings** | `Snova.Std.Strings` | `StringUtils` (`parseInt`, `intToString`, `split`, `join`), `StringBuilder`. |
| **Async** | `Snova.Std.Async` | `TaskState`, concurrent `Channel` communication streams. |
| **LSP** | `Snova.Std.Lsp` | Protocol models (`Position`, `Range`, `Diagnostic`, `RpcRequest`, `RpcResponse`), `LspTransport`. |
| **Mod** | `Snova.Std.Mod` | `snova.mod` parser, SemVer 2.0.0 comparator (`Version`), Git provider resolver. |

## Verification

Verify syntax and structure using `snovac`:
```bash
for f in src/*/*.snova; do
    snovac --check-parse "$f"
done
```
