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
array @ Range.new 0 42
[ ...array, 42 ]
[ 42, ...array ]
```

#### Maps

```
Map a b
```

##### Operations

```
map @ "foo"
{ ...map, "foo" = "bar" }
```

#### Streams

```
Stream a
```

##### Operations

```
stream @ 0
stream @ Range.new 0 42
stream << x
```

### Top types

```
Any
```

## User-defined types

### Record types

- Properties are hidden outside the modules where they are defined.

```
type Person
  ( name : String
  , age : Number
  )
```

#### No-element records

```
type Foo
```

#### Operations

```
Person.name person
Person ( name = "foo", age = 42 )
Person ( ...person, name = "bar" )
```

### Union types

- Type aliases

```
type Foo =
    Bar
  | Baz
  | Blah
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
type Error
  ( context : Any
  )
```

#### ! unary operator

##### Semantics

```
! : (a -> b -> ... -> c) -> a | Error -> b | Error -> ... -> c | Error
```

## Expressions

### Conditionals

#### If expressions

```
if true then 42 else 13
```

#### Case expressions

```
case x = expression
  Person => ...
  Number => ...
  Boolean | None => ...
```

### Iteration

#### Comprehension

```
[ x for x in array if isEven x ]
{ k = v for k, v in map if isEven x }
```
