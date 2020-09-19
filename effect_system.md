# Effect system

- Impure functions are injected only as arguments to main functions.

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
  parallel: Stream Any -> Stream Any,
  race : Stream Any -> Stream Any,
  split : Stream Any -> Stream (Stream Any),
  ... ,
}
```
