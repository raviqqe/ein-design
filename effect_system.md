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
main : System -> None | Error
main system = ...
```

### System type

- Based on [WASI](https://wasi.dev/)

```
type System {
  fdWrite : Number -> [String] -> Number | Error,
  ... ,

  concurrency : Concurrency,
}
```

### Concurrency type

```
type Concurrency {
  parallel : Stream -> Stream,
  race : Stream -> Stream,
  split : Stream -> Stream, # Stream (Stream Any)
  ... ,
}
```
