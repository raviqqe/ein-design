# Error handling

## Result type

```
type Result x e =
    Ok x
  | Error e
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
  Ok => Ok y + 42
  Error => y
```
