# Effect system

- Impure functions are injected only as arguments to functions.

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
main : Os -> None | Error
main os = ...
```

### OS type

```
type Os {
  arguments : List String,
  environmentVariables : List String,

  openFile : String -> FileMode -> File | Error,
  readFile : File -> String | Error,
  writeFile : File -> String -> None | Error,
  ... ,

  concurrency : Concurrency,
}
```

### Concurrency type

```
type Concurrency {
  parallel : Stream a -> Stream a,
  race : Stream a -> Stream a,
  split : Stream a -> Stream (Stream a),
  ... ,
}
```
