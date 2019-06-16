# fastify-authz-secret-provider

Auth0 secret provider integration through `jwks-rsa` in Fastify.

- [jwks-rsa docs](https://github.com/auth0/node-jwks-rsa#usage)

# Install

```terminal
$ npm install -S fastify-authz-secret-provider
```

# Usage:

```js
const fastifySecretProvider = require('fastify-authz-secret-provider');
const fastifyJwt = require('fastify-jwt');

fastify.register(fastifyJwt, {
  secret: fastifySecretProvider({
    cache: true,
    rateLimit: true,
    jwksRequestsPerMinute: 5,
    jwksUri: 'https://__tenant__.auth0.com/.well-known/jwks.json',
  }),
  audience: 'https://api.example.com',
  issuer: 'https://__tenant__.auth0.com/',
  algorithms: ['RS256'],
  decode: { complete: true },
});
```

# Motivation

A [PR created on Auth0's GitHub](https://github.com/vcanales/fastify-authz-secret-provider) has gone completely stale waiting for review on this integration, which I've already used in a few projects, so I'm creating this to maintain it from one location.
