# rit-housing-data-schema

[![PyPI](https://img.shields.io/pypi/v/rit-housing-data-schema.svg)](https://pypi.org/project/rit-housing-data-schema/)
[![Changelog](https://img.shields.io/github/v/release/rit-hc-website/rit-housing-data-schema?include_prereleases&label=changelog)](https://github.com/rit-hc-website/rit-housing-data-schema/releases)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/rit-hc-website/rit-housing-data-schema/blob/main/LICENSE)

Normalized data schema for the output of the data-ingest pipeline.

## Installation

Install this library using `pip`:

```sh
pip install rit-housing-data-schema
```

## Usage

Import this package then use it to construct normalized objects with type
enforcement.

```python
from rit_housing_data_schema import location


location.NormalizedLocation(
  id="vaccinebot:uuid-for-site",
  source=location.Source(
    source="vaccinebot",
    id="uuid-for-site",
    fetched_from_uri="https://vaccinateTheStates.com",
    published_at="2021-01-13T00:00:00-08:00",
    data={},
  )
)
```

For more details on the schema, read the inline comments or the
[`data-ingest` wiki](https://github.com/rit-hc-website/data-ingest/wiki/Normalized-Location-Schema).

## Development

To contribute to this library, first checkout the code. Then create a new
virtual environment:

```sh
cd rit-housing-data-schema
python -mvenv venv
source venv/bin/activate
```

Or if you are using `pipenv`:

```sh
pipenv shell
```

Now install the dependencies, linters, and tests:

```sh
pip install -e '.[lint,test]'
```

To run code formatters:

```sh
isort .
black .
```

To run linters:

```sh
mypy .
flake8 rit_housing_data_schema
```

To run the tests:

```sh
pytest
```

## Release

ideally from within a virtual env as described above...
```
pip install build twine
python -m build
twine check dist/*
twine upload dist/*
```
