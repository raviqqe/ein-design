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

#### Literals

```
False
True
None
42
-42
"String"
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

##### Update

> WIP

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