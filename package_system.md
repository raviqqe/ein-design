# Package system

## Package configuration files

### Command

```json
{
  "target": {
    "type": "Command",
    "name": "foo"
  },
  "dependencies": {
    "github.com/bar/baz": { "version": "master" }
  }
}
```

### Library

```json
{
  "target": {
    "type": "Library"
  },
  "dependencies": {
    "github.com/bar/baz": { "version": "master" }
  }
}
```
