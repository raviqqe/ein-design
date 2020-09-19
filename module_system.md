# Module system

## Exporting variables and types

```
export { Foo, foo }

type Foo { foo : Number }

foo : Number -> Number
foo x = x
```

## Importing modules

```
import "github.com/ein-lang/foo/Foo"

type Bar { foo : Foo.Foo }

bar : Number -> Number
bar x = Foo.foo x
```

### Referencing

- A repository name + a module name
  - e.g. `github.com/ein-lang/foo/Foo/Bar` for a file named `Bar.ein` in a `Foo` directory in a repository of `github.com/ein-lang/foo`

### Aliasing

```
import F "github.com/ein-lang/foo/Foo"

type Bar { foo : F.Foo }

bar : Number -> Number
bar x = F.foo x
```
