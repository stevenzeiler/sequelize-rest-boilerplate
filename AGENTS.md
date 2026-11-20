# AGENTS.md

## What this is

`sequelize-rest-boilerplate` is a small npm module (v0.1.2) that wraps a Sequelize model in an Express router with CRUD routes. Dormant since 2014-11-21.

## Stack

- JavaScript (ES5, CommonJS).
- Dependencies as declared in `package.json`: `express ^4.10.2`, `sequelize ^2.0.0-rc2`, `body-parser ^1.9.2`, `sqlite3 ^3.0.4`, `db-migrate ^0.7.1`. These are 2014-era ranges; `sqlite3` 3.x and Sequelize 2 rc are very unlikely to install or work on a current Node. Not tried in this pass.

## Layout

- `lib/router.js` (package main), `lib/controller.js`: the library.
- `test/server.js`, `test/model.js`, `test/database.js`: an example server and model, not an automated test.
- `docs/STATUS.md`: current state.

## Commands

- Install: `npm install` (known likely to fail on today's toolchain because of old `sqlite3`).
- Test: `npm test` is the npm placeholder and always fails. There are no automated tests.
- Run the example: `node test/server.js` (listens on `PORT` or 5555).

## Rules

- Add or update tests with every change. If a change cannot be tested, say why in the pull request.
- Never commit secrets: keys, tokens, passwords, `.env` files. Use placeholders such as `sXXXXXXXX`.
- Use Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`).
- Keep `docs/STATUS.md` current when behaviour or tooling changes.

## What agents may and may not do

- May: fix bugs, improve docs, add tests, open pull requests against `master`.
- May not, without Steven: archive or delete the repo, publish to npm or any registry, rewrite git history, change the license, or merge their own pull requests.
