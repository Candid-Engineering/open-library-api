# open-library-api

NOTE: *this is not an official Open Library package*. openlibrary.org does not currently provide an official package.

`open-library-api` is a node module that includes Open API Spec definitions for the [openlibrary.org API](https://openlibrary.org/developers/api). It is based on the [reference python library](https://github.com/internetarchive/openlibrary-client) provided by the Internet Archive. The json schema was updated by hand and then generated into typescrupt defs using [openapi-typescript](https://openapi-ts.pages.dev/). To import the types in node, just:

1. Install the library: `npm install open-library-api`
2. Import the types: `import { paths, components, operations } from 'open-library-api'`

## Getting Started - browsing the documentation

This repository comes with an Open API Spec viewer powered by [RapiDoc](https://rapidocweb.com/). To browse the Open API documentation, clone this library:
```
  git clone git@github.com:Candid-Engineering/open-library-api.git
```
Then run `npm start` and open `http://localhost:3000` in your favorite browser.

## Getting Started - node typescript client

While you may use the included OAS specs to generate an Open Library client in any language (e.g. by using [openapi-generator](https://github.com/OpenAPITools/openapi-generator)), the recommended approach for Node + TypeScript is to use `openapi-fetch`:

> openapi-fetch is a type-safe fetch client that pulls in your OpenAPI schema.
> Weighs 5 kb and has virtually zero runtime. Works with React, Vue, Svelte, or
> vanilla JS.

Using it is as simple as:
1. `npm install open-library-api`
2. `npm install openapi-fetch`
3. Create and use an `openapi-fetch` client using the `open-library-api` definitions:

```
import createClient from 'openapi-fetch'
import type { paths } from 'open-library-api'


const client = createClient<paths>({ baseUrl: 'https://openlibrary.org/' })

const { data, error, response } = await client.GET('/isbn/{isbn}.json', {
  params: { path: { isbn: '1234567890' } }
})
```

That's it, have nerdy 📖🐛 fun!

## Future Work
The current implementation only documents the basic `GET` APIs for `/author/{id}`, `/book/{id}` (aka `/edition/{id}`), and `/work/{/id}`. It also covers Edition lookup by ISBN: `/isbn/{isbn}`.

Features that are not currently included in this spec:
- [ ] [Search API](https://openlibrary.org/dev/docs/api/search)
- [ ] Authentication + Write APIs ([see reference python client](https://github.com/internetarchive/openlibrary-client?tab=readme-ov-file#authentication-against-production))

## Contributions Welcome!

Feel free to open Pull Requests with additional open-library features.
