# Type system

- Nominal typing
- Rank-N types

## Types

### Primitives

```
Number
String
```

#### Literals

```
42
-42
"String"
```

### Functions

```
a -> b
```

### Lists

```
List a
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

#### Lists

```
case xs
  [] => ...
  [ x, ...xs ] => ...
```

#### Types

- Arguments need to be union types.

```
case x = expression
  Person => ...
  Number => ...
  Boolean | None => ...
```

## Others

### Type alias

```
type alias Foo = Bar
```
