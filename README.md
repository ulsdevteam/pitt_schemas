# pitt_schemas

JSON schemas and validation helpers.

This is a local clone from the Rockefeller Center schemas: https://github.com/RockefellerArchiveCenter/rac_schemas

## Requirements
*   Python 3.4 or higher
*   [jsonschema](https://python-jsonschema.readthedocs.io/en/stable/)
*   [tox](https://tox.readthedocs.io/) (for running tests)
*   [pre-commit](https://pre-commit.com/) (for running linters before committing)
    *   After installing pre-commit, install the git-hook scripts:

    ```
    $ pre-commit install
    ```

## Installation

The recommended way to install this package is using `pip`:

```
pip install pitt_schemas
```

## Usage

This library has one main public method, `is_valid()`, which takes a dict as the first argument and a schema filename as the second.

```
from pitt_schemas import is_valid

data = {"key": "value" ... }
is_valid(data, "object.json")
```

`pitt_schemas` will attempt to add an appropriate extension to schema filenames in cases where it is either missing or incorrect. For example, if either `schema` and `schema.org` as schema filenames, `pitt_schemas` will attempt to open `schema.json`.

Invalid data will raise a `jsonschema.exceptions.ValidationError`, and an invalid schema filename will raise a `FileNotFoundError`.

### Available schemas

All schemas are located in the `schemas/` subdirectory of the `pitt_schemas/` directory.

#### Tests

`pitt_schemas` comes with unit tests as well as linting. The easiest way to make sure all tests pass is to run `tox` from the root of the repository. This will execute all tests, and will also run `autopep8` and `flake8` linters against the codebase.

## Documentation

Automatically generated HTML documentation in the `docs/` directory based upon `.json` files in the `schemas/` subdirectory of the `pitt_schemas/` directory.

### Requirements

*   Python 3.4 or higher
*   [json-schema-for-humans](https://github.com/coveooss/json-schema-for-humans)

## Usage

Running `generate_docs.py` will iterate over the `schemas/` subdirectory and write updated docs files to the `docs/` directory.

## License

Code is released under an MIT license. See`LICENSE.md`.
