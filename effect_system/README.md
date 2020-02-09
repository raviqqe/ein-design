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
- Environment
  - Command-line arguments
  - Environment variables
- Parallelism / Concurrency
  - Parallel evaluation
  - Concurrent queues

## Main functions

```
import "github.com/ein-lang/ein/Effect"

main : Environment -> Stream Command -> Stream Concurrency -> None | Error
main environment commands concurrencies = ...
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

### Concurrency types

```
type Concurrency =
  { sortByTime : Stream (None -> Any) -> Stream Any
  , parallelize : List (None -> Any) -> List Any
  , splitStream : Stream Any -> Stream (Stream Any)
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
  worldStreams = Effect.splitStream worlds
  worlds = first worldStreams
  otherWorlds = second worldStreams
in let
  content = Effect.readFile "foo.txt" otherWorlds
in let
  worldStreams = Effect.splitStream worlds
  worlds = first worldStreams
  otherWorlds = second worldStreams
in
  Effect.writeFile "bar.txt" content otherWorlds
```

## History

- [v1](v1.md)
- [v2](v2.md)
- [v3](v3.md)
- [v4](v4.md)
