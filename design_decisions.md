# Design decisions

## No standard library written in foregin languages

### Pros

- Portability of the language and its standard library

### Cons

- Implementation of more stuff
  - e.g. KMP substring search

## Inductive definitions of low-level values

### Pros

- No cyclic reference is needed.
  - Reference counting is available.
