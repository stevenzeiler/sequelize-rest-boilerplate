# sequelize-rest-boilerplate

Turn a Sequelize model into an Express router with CRUD routes in one line.

> **Status: dormant since 2014.** Written by Steven Zeiler on 2014-11-21 (four commits in about 20 minutes, v0.1.2) during his 2014 Ripple Labs era. It targets Sequelize 2.0 release candidates and Express 4.10. It has not been run against current versions, so use it as a reference, not a dependency.

## Install

    npm install sequelize-rest-boilerplate

(Not confirmed as published to npm; `npm install stevenzeiler/sequelize-rest-boilerplate` installs from GitHub.)

## Usage

    var SQLRest = require('sequelize-rest-boilerplate');
    var Payment = require('./sequelize_payment_model');

    var router = new SQLRest(Payment, 'payment');
    app.use('/payments', router);

    app.listen(process.env.PORT);

`new SQLRest(model, singular, plural)`: `plural` defaults to `singular + 's'`. Mount the router where you like. Your app needs `body-parser` (JSON) set up before the router, as `test/server.js` does.

## Routes

Relative to the mount path:

| Method | Path | Controller action |
|---|---|---|
| POST | `/` | create |
| GET | `/` | index (filters come from the request body) |
| GET | `/:id` | show |
| PUT | `/:id` | update |
| DELETE | `/:id` | destroy |

Responses are JSON, keyed by the singular or plural name, for example `{ "payment": { ... } }`. Errors are `{ "error": ... }`.

## Configuration

- `PORT`: only used by the example server in `test/server.js` (defaults to 5555).

## How it works

`lib/router.js` builds an `express.Router` and binds the five routes to a `Controller` (`lib/controller.js`) that calls Sequelize's `create`, `findAll`, `find` and `destroy`.

Known rough edges from reading the code (not from running it): the `update` action looks up the instance with the whole request body and then calls `updateAttributes` on the controller rather than the instance, which looks wrong. See [docs/STATUS.md](docs/STATUS.md).

## Tests

`npm test` is still the npm placeholder and exits with an error. `test/server.js` is an example server (in-memory SQLite) you can start by hand with `node test/server.js`; it was not run in this pass.

## Status

See [docs/STATUS.md](docs/STATUS.md). License: ISC (see [LICENSE](LICENSE)).
