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

### Streams

```
Stream a
```

#### Operations

- Evaluation of elements are always delayed.

```
stream @ 1
stream @ Range.new 1 42
[ ...stream, 42 ]
[ 42, ...stream ]
[ x for x in stream if test x ]
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

#### Element-less records

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

```
Foo | Bar | Baz
```

### Type alias

```
type Foo = Bar
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

### If expressions

```
if True then 42 else 13
```

### Case expressions

```
case x = expression
  Person => ...
  Number => ...
  Boolean | None => ...
```
