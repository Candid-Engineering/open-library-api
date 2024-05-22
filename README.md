# open-library-api

NOTE: *this is not an official Open Library package*. openlibrary.org does not currently provide an official package.

`open-library-api` is a node module that includes Open API Spec definitions for the [openlibrary.org API](https://openlibrary.org/developers/api). It is based on the [reference python library](https://github.com/internetarchive/openlibrary-client) provided by the Internet Archive.

The current implementation exposes just the basic `GET` APIs for `/author/{id}`, `/book/{id}` (aka `/edition/{id}`), and `/work/{/id}`. It also covers Edition lookup by ISBN: `/isbn/{isbn}`.

Possible future work:
- [ ] Search API
- [ ] Authentication (for write APIs)
- [ ] Write APIs (authentication is required)

## Getting Started - browsing documentation

To browse the Open API documentation, clone this library:
```
  git clone {.. TODO: fill address}
```
Then run `npm start` and open `localhost:3000` in your favorite browser.

## Getting Started - typescript client

The library comes equipped with a type-safe client based on [`openapi-fetch`](https://openapi-ts.pages.dev/openapi-fetch/). To use it, first intall this library:

```
  npm install open-library-api
```

Next, import the client and start making type-safe requests to the Open Library:

```
import { client } from 'open-library-api'

const { data, error, response } = await client.GET('/isbn/{isbn}.json', {
  params: { path: { isbn: '1234567890' } }
})
```

That's it, have fun!

## Contributions Welcome!

Feel free to open Pull Requests with additional features.
