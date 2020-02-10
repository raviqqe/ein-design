# Type system

- Nominal typing
- Restricted polymorphism

## Built-in types

### Functions

```
a -> b
```

### Primitives

```
Boolean
None
Number
String
```

### Collections

#### Arrays

```
Array a
```

##### Update

```
[...a, 42]
[42, ...a]
```

#### Maps

```
Map a b
```

##### Update

```
{ ...a, "foo" = "bar" }
```

#### Streams

```
Stream a
```

### Top types

```
Any
```

## User-defined types

### Record types

- Encapsulated
  - Properties are hidden by default.

```
type Person =
  { name : String
  , age : Number
  }
```

#### Exporting properties

```
export { Person { ... } }
```

#### Initialization

```
Person { name = "foo", age = 42 }
```

#### Property access

```
.name person
```

#### Update

```
{ ...person, name = "bar" }
```

### Union types

- Type aliases

```
type Foo =
    Bar
  | Baz
  | Blah
```

#### Extension

```
type Foo =
    Bar
  | Baz

type Blah =
    Foo
  | Qux
```

## Special types

### Result types

```
type Result =
    Foo
  | Error
```

#### Error types

```
type Error =
  { context : Any
  }
```

#### ! unary operator

##### Semantics

```
! function : (a -> b -> ... -> c) -> (a | Error -> b | Error -> ... -> c | Error)
```

## Expressions

### Conditionals

#### If expressions

```
if True then 42 else 13
```

#### Case expressions

```
case foo of
  { name = "John" } -> e1
  { name = "Doe" } -> e2
  { name } -> e3
```

##### Type switch

- Used with union or top types

```
case bar of
  Foo -> e1
  Bar -> e2
  Baz -> e3
```

### Iteration

#### Array comprehension

```
[x * x for x in xs if isEven x]
```

## History

- [v1](v1.md)
- [v2](v2.md)
- [v3](v3.md)
- [v4](v4.md)
- [v5](v5.md)
- [v6](v6.md)
- [v7](v7.md)
- [v8](v8.md)
- [v9](v9.md)
- [v10](v10.md)
