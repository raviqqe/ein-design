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
- Lazy

```
List a
```

#### Operations

```
[ ...list, 42 ]
[ 42, ...list ]
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
Person{ name = "foo", age = 42 }
Person{ ...person, name = "bar" }
```

### Unions

```
Foo | Bar | Baz
```

### Any

```
Any
```

### Errors

```
type Error {
  error : Any,
}
```

#### ! unary operator

```
foo : a -> b -> ... -> c
```

to

```
! foo : a | Error -> b | Error -> ... -> c | Error
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

### Loop expressions

```
for sum xs
  case xs
    [] => sum
    [ x, ...xs ] => recur (sum + x) xs
```

```
for xs ys
  case xs
    [] => ys
    [ x, ...xs ] =>
      case y = f x
        Error => y
        Number => recur xs [ y, ...ys ]
```

## Others

### Type alias

```
type Foo = Bar
```
