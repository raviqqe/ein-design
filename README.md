# The design of Ein programming language

- [Type system](type_system.md)
- [Command-query separation](command_query_separation.md)
- [Naming convention](naming_convention.md)
- [Random notes](random_notes.md)
- [References](references.md)

## Mission statement

Eliminate all software bugs in the world!

## Product vision

Make programming easy for beginners!

- Testable
  - Deteriministic
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
1. General-purpose programming language for biginners

## Product principles

- 1% does not matter.
  - e.g. Go
- Complexity can only be built upon simplicity.
  - Application logics are complex!

## Design details

- Limited polymorphism
  - No generics (parametric polymorphism)
