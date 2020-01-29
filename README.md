# npm-migrate

Migrate all versions of a selected package from a registry to another one.

## Usage

```js

const migrate = require('npm-migrate')

const moduleName = 'my-private-module'
const from = 'http://your-old.private-registry.com:8080'
const to = 'http://nice-new.private-registry.org:8080'

// optional
const options = {
    debug: false // default
}

migrate(moduleName, from, to, options)
    .then((migrated) => console.log(migrated)) // list of migrated packages
    .catch((err) => console.error(err))


```

## What it does

1. Fetches all versions (or just those not already migrated) as tarballs from old registry
2. Publishes each version to the new registry
3. Cleans up after itself

## Known issues

- The dates of every version published will be reset to the date and time you run this script
- The migrating user will be added as maintainer

## Changelog

- @lipavsky - removed modificaiton of package.json -> broke shasums
- v1.2.0 - Work with scoped packages
- v1.3.0 - Compare both registries and migrate only the remaining versions not in the new registry
