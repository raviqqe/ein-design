# Effect system

- Impure functions are injected only as arguments to main functions.
  - Any modules including standard ones are all pure.
- All effects have output.
  - For testability
  - e.g. `sleep : Number -> None | Error`

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
main worlds = ...
```

## Effect module

```
readFile : String -> Stream World -> String | Error
readFile filename worlds =
  let
    file = .openFile (first world) filename ReadOnly
  in
    .readFile (second worlds) (! file)

writeFile : String -> String -> Stream World -> None | Error
writeFile filename content worlds =
  let
    file = .openFile (first worlds) filename WriteOnly
  in
    .writeFile (second worlds) file content

...
```

## Argument types

### Parameters types

```
type Parameters =
  { arguments : List String
  , environmentVariables : Map String String
  , ...
  }
```

### Command types

```
type Command =
  { openFile : String -> File | Error
  , readFile : File -> String | Error
  , writeFile : File -> String -> None | Error
  , ...
  }
```

### Nondeterministics types

```
type Nondeterministics =
  { sortByTime : Stream (None -> Any) -> Stream Any
  , parallellize : List (None -> Any) -> List Any
  , ...
  }
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
  [worlds, otherWorlds] = Effect.split worlds
in let
  content = Effect.readFile "foo.txt" otherWorlds
in let
  [worlds, otherWorlds] = Effect.split worlds
in
  Effect.writeFile "bar.txt" content otherWorlds
```

## History

- [v1](v1.md)
- [v2](v2.md)
- [v3](v3.md)
- [v4](v4.md)
