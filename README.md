# fastify-authz-secret-provider

Auth0 secret provider integration through `jwks-rsa` in Fastify.

- [jwks-rsa docs](https://github.com/auth0/node-jwks-rsa#usage)

# Install

```terminal
$ npm install -S fastify-authz-jwks
```

# Usage:

```js
const fastifySecretProvider = require('fastify-authz-jwks');
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

A [PR created on Auth0's GitHub](https://github.com/auth0/node-jwks-rsa/pull/31) has gone stale waiting for review on this integration, so I've created this fork to avoid further manual implementations 🚀
