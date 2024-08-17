# una-example-modules

This is an example of an [una](https://github.com/carderne/una) monorepo using the Modules style.

Read more about una:
- [Official docs](https://una.rdrn.me/)
- [Official docs on the Modules style](https://una.rdrn.me/style-modules/)

## About
This repository is basically the result of the following steps:
```bash
rye init una-example-packages
cd una-example-packages
rye add --dev una
rye run una create workspace --style=modules
rye sync
rye run una sync
rye add --dev basedpyright pytest
```

And then some extra settings added to root `pyproject.toml` file to get Pyright and Pytest to play nice.

## Commands
Sync the una dependency graph (that is, resolve all dependencies between packages in the monorepo):
```bash
rye run una sync
```

Formatting, linting etc (these are specified at the top of the root [pyproject.toml](./pyproject.toml)).
```bash
rye run fmt
rye run lint
rye run check
rye run test

# or just
rye run all
```

## Building
Builds should be run separately from each project directory.

For example:
```bash
cd projects/example_project
rye run build
# output will still be in root/dist by default
```
