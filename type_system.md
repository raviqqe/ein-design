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
false
true
none
42
-42
"string"
```

### Collections

#### Arrays

```
Array a
```

##### Operations

```
array @ 0
[...a, 42]
[42, ...a]
```

#### Maps

```
Map a b
```

##### Operations

```
map @ "foo"
{ ...a, ["foo"] = "bar" }
```

#### Streams

```
Stream a
```

##### Operations

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

#### Operations

```
.name person
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
if true then 42 else 13
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

#### Comprehension

```
[x * x for x in array if isEven x]
{k: v for k, v in map if isEven x}
```
