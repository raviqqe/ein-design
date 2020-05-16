# Effect system

- Impure functions are injected only as arguments to main functions.
  - All modules including standard ones are pure.
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

### Argument types

#### Parameters types

```
type Parameters
  ( arguments : Array String
  , environmentVariables : Map String String
  , ...
  )
```

#### Command types

```
type Command
  ( openFile : String -> FileMode -> File | Error
  , readFile : File -> String | Error
  , writeFile : File -> String -> None | Error
  , ...
  )
```

#### Concurrency types

- Concurrency errors among effects are not testable.

```
type Concurrency
  ( evaluateUnorderedStream : Stream (None -> Any) -> Stream Any
  , evaluateStream : Stream (None -> Any) -> Stream Any
  , splitStream : Stream Any -> Stream (Stream Any)
  , ...
  )
```

## Effect module

```
readFile : String -> Stream Command -> String | Error
readFile filename commands =
  let
    file = Command.openFile (commands @ 0) filename ReadOnly
  in
    ! Command.readFile (commands @ 1) file

writeFile : String -> String -> Stream Command -> None | Error
writeFile filename content commands =
  let
    file = Command.openFile (commands @ 0) filename WriteOnly
  in
    ! Command.writeFile (commands @ 1) file content

...
```

## Do notation

```
do commands
  content = Effect.readFile "foo.txt"
  result = ! Effect.writeFile "bar.txt" content
in
  result
```

is equivalent to:

```
let
  commandStreams = Effect.splitStream commands
  content = Effect.readFile "foo.txt" (commandStreams @ 0)
  result = ! Effect.writeFile "bar.txt" content (commandStreams @ 1)
in
  result
```
