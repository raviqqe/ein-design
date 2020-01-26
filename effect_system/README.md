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
    content = Effect.readFile "foo.txt" (first worlds)
  in
    Effect.writeFile "bar.txt" content (second worlds)
```

### Effect module

```
readFile : String -> World -> String | Error
writeFile : String -> String -> World -> None | Error
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
  content = Effect.readFile "foo.txt" world
in let
  world = first worlds
  worlds = tail worlds
in
  Effect.writeFile "bar.txt" content world
```

## Implementation

### World types

Their values contain results of primitive effects executed there for immutability and idempotency.

```
type World = { ... }
```

## History

- [v1](v1.md)
- [v2](v2.md)
