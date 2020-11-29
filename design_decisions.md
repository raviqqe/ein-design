# Design decisions

## No standard library written in foreign languages

- If standard libraries are written in another language, both languages need to support all the backend.

### Pros

- Portability of the language and its standard library

### Cons

- Implementation of more stuff
  - e.g. KMP substring search

## Inductive definitions of low-level values

### Pros

- No cyclic reference is needed.
  - Reference counting is available.
