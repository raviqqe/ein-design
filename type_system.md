# Type system

- Nominal typing
- Restricted polymorphism

## Types

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

### Functions

```
a -> b
```

### Lists

- Maybe lazy

```
List a
```

#### Operations

```
list @ 1
list @ Range.new 1 42
[ ...list, 42 ]
[ 42, ...list ]
[ x for x in list if test x ]
```

### Records

- Elements are hidden outside the modules where they are defined.

```
type Person {
  name : String,
  age : Number,
}
```

#### Element-less records

```
type Foo
```

#### Operations

```
Person.name person
Person { name = "foo", age = 42 }
Person { ...person, name = "bar" }
```

### Unions

```
Foo | Bar | Baz
```

### Any

```
Any
```

## Special types

### Error types

```
type Error {
  context : Any,
}
```

#### ! unary operator

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

## Others

### Type alias

```
type Foo = Bar
```
