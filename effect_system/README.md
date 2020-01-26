# Effect system

- All effects have output.
  - e.g. `sleep : Number -> None | Error`
- Modules can be both pure or impure.

## Effects

- I/O
  - File system
  - Network
  - Clock
    - Time sort
- Environment
  - Command-line arguments
  - Environment variables

## Main functions

```
import "github.com/ein-lang/ein/Effect"

main : Stream World -> None | Error
main worlds =
  let
    content = Effect.readFile (first worlds) "foo.txt"
  in
    Effect.writeFile (second worlds) "bar.txt" content
```

### Effect module

```
readFile : World -> String -> String | Error
writeFile : World -> String -> String -> None | Error
```

## Do notation

```
do worlds
  content = Effect.readFile "foo.txt"
  Effect.writeFile "bar.txt" content
```

is equivalent to:

```
let
  world = first worlds
  worlds = tail worlds
in let
  content = Effect.readFile world "foo.txt"
in let
  world = first worlds
  worlds = tail worlds
in
  Effect.writeFile world "bar.txt" content
```

## Implementation

### World types

The values contain states or results of primitive effects executed there for immutability and idempotency.

```
type World = { ... }
```

## History

- [v1](v1.md)
- [v2](v2.md)
