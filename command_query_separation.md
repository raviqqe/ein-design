# Concept

## Stateful program model

- Paradigms
  - Object-oriented
  - Imperative

```
   input
     |
+----v----+
| program |
+----v----+
     |
   effect
```

## Stateless program model

- Paradigms
  - Functional
  - Dataflow

```
            query        query        query
              |            |            |
initial  +----v----+  +----v----+  +----v----+
 state --> program >--> program >--> program >-- ...
         +----v----+  +----v----+  +----v----+
              |            |            |
           command      command      command
```

or

```
  queries
     |
+----v----+
| program |
+----v----+
     |
  commands
```

## Analysis

### Arbitrary evaluation strategy

> WIP

As queries are just queries to the outside of programs, they do not have to be
evaluated always but only if necessary.
What must be guaranteed is only that all commands are run eventually
before programs finish.

### Reactiveness without theory

The model shows us that potential reactiveness inside programs is elicited
exactly by starting executing all commands at once.
As a result, programs would run in utmost reactiveness within the limits of
computational capacity.

### Inputs and commands are infinite in general

If sticking to the model, we need some way to express and handle an infinite
number of queries and commands although available memory is limited.
This problem is resolved by lazy evaluation and tail recursion as the former
allows function calls to be evaluated on demand and the latter
enables infinitely recursive function calls.

## Syntax

```
main : World -> [Effect]
main { fs, http } = [
  fs.readFile "xxx"
  fs.writeFile "aaa" "bbb"
  fs.writeFile "ccc" (do fs.readFile "ddd")

  http.get "http://localhost"
  http.post "http://localhost" "body"
  http.post "http://localhost" (do http.get "http://localhost")
]
```
