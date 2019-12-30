# Module system

## Exporting variables and types

In `github.com/ein-lang/foo/Foo.ein`,

```
export { Foo, bar }

type Foo = { foo: Number }

bar : Number -> Number
bar x = x
```

## Importing modules

```
import "github.com/ein-lang/foo/Foo"

type Bar = Foo.Foo

baz : Number -> Number
baz x = Foo.foo x
```
