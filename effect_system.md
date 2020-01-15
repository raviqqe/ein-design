# Effect system

- Everything is passed to the main function.
- Effects
  - I/O
    - File system
    - Network
  - Environment
    - Command-line arguments
    - Environment variables

## v1

### Main functions

```
import Effects

main : Executors -> Effect
main executors =
  writeFile "bar.txt" (executors.execute (Effects.readFile "foo.txt"))

```

### Types

#### Executors

```
type Executors =
  { execute : Effect -> EffectResult
  , rest : "readFile" -> ReadFileExecutor | "writeFile" -> WriteFile
  }
```

#### Effects

```
type EffectType =
    "readFile"
  | "writeFile"
  | "getArguments"
  | "getEnvironmentVariables"
  | ...

type Effect =
    ReadFile
  | WriteFile
  | ...

type ReadFile =
  { type : "readFile"
  , filename : String
  }

type WriteFile =
  { type : "writeFile"
  , filename : String
  , content : String
  }

...
```

## v2

### Main functions

```
import Effects

main : World -> Effect
main world =
  let
    { result, world } = world.readFile "foo.txt"
  in
    world.writeFile "bar.txt" result
```

### Types

```
type World =
  { readFile : String -> { result : String | Error, world: World }
  , writeFile : String -> String -> { result : Null | Error, world: World }
  , ...
  }
```

### Do notation?

#### v1

```
do writeFile "bar.txt" (do readFile "foo.txt")
```

or

```
let
  result = do readFile "foo.txt"
in
  do writeFile "bar.txt" result
```

is equivalent to:

```
let
  readFile = .readFile world
  writeFile = .writeFile world
  ...
in let
  { result, world } = readFile "foo.txt"
in let
  readFile = .readFile world
  writeFile = .writeFile world
  ...
in
  writeFile "bar.txt" result
```

#### v2

```
do result = readFile "foo.txt"
do writeFile "bar.txt" result
```

#### v3

```
do
  result = readFile "foo.txt"
  writeFile "bar.txt" result
```

##### Custom variable binding?

```
do state
  result = get "key1"
  set "key2" result
```
