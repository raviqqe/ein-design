# References

## Programming languages

- [Elm](https://github.com/elm)
- [Go](https://github.com/golang/go)
  - The package namespace system like Go works only with object-oriented programming as classes create subnamespaces.
  - [Channels - A Tour of Go](https://tour.golang.org/concurrency/2)
- [Gluon](https://github.com/gluon-lang/gluon)
- [Expresso](https://github.com/willtim/Expresso)
- [IntercalScript](https://github.com/Storyyeller/IntercalScript)
  - Case objects are similar to polymorphic variants in OCaml.
- [TypeScript](https://github.com/microsoft/TypeScript)
- [Haskell](https://github.com/ghc/ghc)
- [OCaml](https://github.com/ocaml/ocaml)
- [Nim](https://github.com/nim-lang/Nim)
  - Its garbage collection with deferred reference counting is interesting.

## Language design

- [Less is more: language features](https://blog.ploeh.dk/2015/04/13/less-is-more-language-features/)

## Type system

- [Lecture slides of recursive types at Cornell University](https://www.cs.cornell.edu/courses/cs4110/2012fa/lectures/lecture27.pdf)
- [Algebraic subtyping](https://www.cl.cam.ac.uk/~sd601/thesis.pdf)
  - [Polymorphism, Subtyping, and Type Inference in MLsub](https://www.cl.cam.ac.uk/~sd601/papers/mlsub-preprint.pdf)

## Garbage collection

### Reference counting

- [Counting Immutable Beans: Reference Counting Optimized for Purely Functional Programming](https://arxiv.org/abs/1908.05647)

### Immix GC

- [mu/immix-rust](https://gitlab.anu.edu.au/mu/immix-rust)
- [Immix: A Mark-Region Garbage Collector with Space Efficiency, Fast Collection, and Mutator Performance](https://www.cs.utexas.edu/users/speedway/DaCapo/papers/immix-pldi-2008.pdf)
- [Taking Off the Gloves with Reference Counting Immix](http://users.cecs.anu.edu.au/~steveb/pubs/papers/rcix-oopsla-2013.pdf)
- [Rust as a Language for High Performance GC Implementation](http://users.cecs.anu.edu.au/~steveb/pubs/papers/rust-ismm-2016.pdf)
