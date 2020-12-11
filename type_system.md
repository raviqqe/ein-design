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

- Generic

```
[a]
```

#### Operations

```
[ 42, ...list ]
```

### Records

- Elements are private outside modules.

```
type Person {
  name : String,
  age : Number,
}
```

#### Operations

```
Person.name person
Person{ name = "foo", age = 42 }
Person{ ...person, name = "bar" }
```

### Enumerated types

```
type Foo
```

### Unions

```
Foo | Bar | Baz
```

### Any

```
Any
```

## Expressions

### If expressions

```
if True then 42 else 13
```

### Case expressions

#### Lists

```
case xs
  [] => ...
  [ x, ...xs ] => ...
```

#### Types

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
