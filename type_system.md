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
- Needs μ constructors.
- Recursive types can be defined only by explicit type definitions.
  - Not by type inference
  - i.e. no automatic introduction of μ constructors

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
    Foo Foo // Bar.Foo
  | Bar Bar
  | Baz
```

### Case expression

```
case foo of
  { name = "John", ... } -> e1
  { name = "Doe", ... } -> e2

case bar of
  Foo foo -> e1
  Bar bar -> e2
  Baz -> e3

case bar of
  Foo { name = "John", ... } -> e1
  Bar (Foo foo) -> e2
  Bar (Bar bar) -> e3
  Bar (Baz baz) -> e4
  Baz -> e5
```

## v5

- Nominal product types
- Structurally-subtyped sum types
- Type aliases

```
// Product types
type Foo = { name : String, age : Number }

// Product types with functions
type Foo = { doSomething : Number -> Number }

// Sum types
type Bar =
    Foo // Bar.Foo
  | Bar
  | Baz
```

### Case expression

```
case foo of
  { name = "John", ... } -> e1
  { name = "Doe", ... } -> e2

case bar of
  Foo -> e1
  Bar -> e2
  Baz -> e3
```

## v6

- Structural typing
- ADT
- Polymorphic variants
- Separate namespaces for types and variables

```
// Type aliases
type Human = { name : String, age : Number }

// ADT
type Bar =
    Foo { firstName : String, lastName : String }
  | Bar { name : String, age : Number }
  | Baz Number
  | Blah

// Extend existing types
type Baz =
    ...Foo
  | Blah String

x : Bar
x = Foo { name = "John", age = 42 }
```

### Result types

```
type Result =
    ...Foo
  | Error String
```

### Option types

```
type Option =
    ...Foo
  | None
```

### Case expression

```
case foo of
  Foo { name = "John", ... } -> e1
  Foo { name = "Doe", ... } -> e2
  Foo { name, ... } -> e3

case bar of
  Foo { name, ... } -> e1
  Bar bar -> e2
  Baz baz -> e3
  Blah -> e4
```
