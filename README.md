# elysia-smart-static
Elysia smart static is a fork of elysia static plugin that provides a tiny bit of extra functionality. It will:

1. Assume the user is looking for a `.html` file if no file extension is specified (i.e. `/docs/getting-started` -> `/docs/getting-started.html`)
2. Handle checking for index files (i.e. `/docs/getting-started -> /docs/getting-started/index.html`).

Essentially, this plugin allows elysia to just serve a folder.

If the user gives the route `/docs/getting-started` and both the files `/docs/getting-started.html` and `/docs/getting-started/index.html` exist, the one without the index will be preferred. A warning should be printed to the console if this happens.

The original elysia static plugin was created by @SaltyAnom and this fork was created by @firesquid6 for [inkdocs](https://github.com/firesquid6/inkdocs).


# Original README
Plugin for [elysia](https://github.com/saltyaom/elysia) for serving static folder.

## Installation
```bash
bun add @elysiajs/static
```

## Example
```typescript
import { Elysia } from 'elysia'
import { staticPlugin } from '@elysiajs/static'

const app = new Elysia()
    .use(staticPlugin())
    .listen(8080)
```

## Config
Below is an available config for a static plugin.

### assets
@default "public"

Asset path to expose as a public path

### prefix
@default '/public'

Path prefix to create a virtual mount path for the static directory

### staticLimit
@defualt 1024

If total files exceed this number, the file will be handled via wildcard instead of the static route to reduce memory usage

### alwaysStatic
@default boolean

If set to true, the file will always use a static path instead
