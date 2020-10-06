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
case x
  Ok y => Ok (y + 42)
  Error e => Error e
```
