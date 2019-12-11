# Type system

## v1

```
// Product types
type Foo = { name: String, age: Number }

// Sum types
type Bar = Foo Foo | Bar
```

## v2

- Structural subtyping?

```
// Product types
type Foo { name: String, age: Number }

// Sum types
type None
type Bar = Foo | None
```

## v3

- Structural subtyping
- No nominal types

```
// Product types
type Foo = { name: String, age: Number }

// Sum types
type Bar = Foo | Number | Null

// String enum types
type Baz = "foo" | "bar" | "baz"

// Branded types
type Blah = { type: "blah", ... }
```

## Case expression

```
type Foo = { name: String, ... }
type Bar = ...

case x of
  Null -> e1
  Foo ->
    case x of
      { name: "John", ... } -> e2
      { name: name, ... } -> e3
  Bar -> e4
```

### Flattening type switch?

```
case x of
  Null -> e1
  Foo { name: "John", ... } -> e2
  Foo { name: name, ... } -> e3
  Bar -> e4
```
