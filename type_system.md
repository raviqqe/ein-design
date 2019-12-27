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
type None {}
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

### Case expression

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

#### Flattening type switch?

```
case x of
  Null -> e1
  Foo { name: "John", ... } -> e2
  Foo { name: name, ... } -> e3
  Bar -> e4
```

## v4

- Nominal types
- No structural subtyping
- No type alias
- Similar to Go

```
// Product types
type Foo = { name: String, age: Number }

// Product types with functions
type Foo = { doSomething: Number -> Number }

// Sum types
type Bar =
    Foo Foo
  | Bar Bar // Bar.Bar
  | Baz
```

### Case expression

```
case foo of
  { name: "John", ... } -> e1
  { name: "Doe", ... } -> e2

case bar of
  Foo foo -> e1
  Bar bar -> e2
  Baz -> e3
```
