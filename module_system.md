# Module system

## Exporting variables and types

In `github.com/ein-lang/foo/Foo.ein`,

```
export { Foo, foo }

type Foo = { foo : Number }

foo : Number -> Number
foo x = x
```

## Importing modules

```
import "github.com/ein-lang/foo/Foo"

type Bar = { foo : Foo.Foo }

bar : Number -> Number
bar x = Foo.foo x
```
