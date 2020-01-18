# The design of Ein programming language

- [Type system](type_system)
- [Builtin generic functions and types](builtin_generics.md)
- [Effect system](effect_system.md)
- [Module system](module_system.md)
- [Naming convention](naming_convention.md)
- [Random notes](random_notes.md)
- [References](references.md)

## Mission statement

Eliminate all software bugs in the world!

## Product vision

Make programming easy for beginners!

- Testable
  - Deterministic
  - Strict evaluation
  - Dependency injection
- Simple
  - Easy to learn
- Restricted
  - Statically typed
  - Less mistakes

## Product strategy

1. Programming language to write command line tools
1. Programming language to write HTTP API servers
1. Limited generics
1. Binary support
1. General-purpose programming language for beginners

## Product principles

- Perfection is achieved when there is nothing to take away.
- 1% does not matter.
  - e.g. Go
- Complexity can only be built upon simplicity.
  - Application logics are complex!
- Resemble but do not depend on existing technologies

## Design details

- Limited polymorphism
  - No generics (parametric polymorphism)
