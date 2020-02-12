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
- Parameters
  - Command-line arguments
  - Environment variables
- Parallelism / Concurrency
  - Parallel evaluation
  - Concurrent queues

## Main functions

```
main : Parameters -> Stream Command -> Stream Concurrency -> None | Error
main parameters commands concurrencies = ...
```

## Effect module

```
readFile : String -> Stream Command -> String | Error
readFile filename commands =
  let
    file = .openFile (first commands) filename ReadOnly
  in
    .readFile (second commands) (! file)

writeFile : String -> String -> Stream Command -> None | Error
writeFile filename content commands =
  let
    file = .openFile (first commands) filename WriteOnly
  in
    .writeFile (second commands) file content

...
```

## Argument types

### Parameters types

```
type Parameters =
  { arguments : Array String
  , environmentVariables : Map String String
  , ...
  }
```

### Command types

```
type Command =
  { openFile : String -> FileMode -> File | Error
  , readFile : File -> String | Error
  , writeFile : File -> String -> None | Error
  , ...
  }
```

### Concurrency types

- Some concurrency bugs are not testable.
  - e.g. when effects are interleaved in multiple concurrent execution contexts

```
type Concurrency =
  { mapUnorderedStream : (Any -> Any) -> Stream Any -> Stream Any
  , mapStream : (Any -> Any) -> Stream Any -> Stream Any
  , splitStream : Stream Any -> Stream (Stream Any)
  , ...
  }
```

## Do notation

```
do commands
  content = Effect.readFile "foo.txt"
  Effect.writeFile "bar.txt" content
```

is equivalent to:

```
let
  commandStreams = Effect.splitStream commands
  commands = first commandStreams
  otherCommands = second commandStreams
in let
  content = Effect.readFile "foo.txt" otherCommands
in let
  commandStreams = Effect.splitStream commands
  commands = first commandStreams
  otherCommands = second commandStreams
in
  Effect.writeFile "bar.txt" content otherCommands
```

## History

- [v1](v1.md)
- [v2](v2.md)
- [v3](v3.md)
- [v4](v4.md)
