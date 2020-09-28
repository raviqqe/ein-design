# Error handling

## Error type

```
type Error {
  error : Any,
}
```

## Error binding

```
let
  y : Number
  y ?= x
in
  y + 42
```

is equivalent to:

```
case y = x
  Error => y
  Number => y + 42
```
