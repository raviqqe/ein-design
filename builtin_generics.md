# Builtin generic functions and types

## Functions

```
map : (a -> b) -> [a] -> [b]

reduce : (a -> b -> b) -> b -> [a] -> b
```

## Types

### Structural subtyping

```
type Error = { kind = "Error", ... }

type Result = ... | Error

type Option = ... | null
```

### Nominal types

```
type Result a b = Ok a | Error b

type Option a = Some a | None
```
