# Type system

- Nominal typing
- Generics

## Types

### Primitives

```
Number
String
```

#### Literals

```
-12.3
"String"
```

### Functions

```
a -> b
```

### Lists

```
[a]
```

#### Literals

```
[ 1, 2, 3 ]
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

### Unions

```
type Maybe a =
    Just a
  | None
```

## Expressions

### If expressions

```
if True then 42 else 13
```

### Case expressions

- Arguments are union types.

```
case x
  Person person => ...
  Number number => ...
  else => ...
```

#### Lists

```
case xs
  [] => ...
  [ x, ...xs ] => ...
```
