# .github

What the [Kostavo tools](https://github.com/kostavo-oss) share without sharing code:

- [`profile/README.md`](profile/README.md) — the organisation's front page
- [`.github/workflows/`](.github/workflows) — the CI and release workflows every tool calls
- [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE) and
  [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) — the defaults
  for any repo that doesn't bring its own

## The workflows

A tool made from [`cookiecutter-python`](https://github.com/kostavo-oss/cookiecutter-python)
already calls both.

### `python-ci.yml`

`ruff check`, `ruff format --check`, and `pytest` on every supported Python.

```yaml
jobs:
  python:
    uses: kostavo-oss/.github/.github/workflows/python-ci.yml@main
    # with:
    #   python-versions: '["3.11", "3.12", "3.13", "3.14"]'
```

| Input | Default | |
|---|---|---|
| `python-versions` | `'["3.11", "3.12", "3.13"]'` | The Pythons to run the tests on, as a JSON list |

### `python-release.yml`

Run on a `vX.Y.Z` tag. It checks that the tag and `pyproject.toml` name the same
version, runs the gate, builds the wheel and sdist, starts every command the wheel
declares, and leaves the files as the artifact `dist`.

It does not publish. PyPI's Trusted Publisher is a repository and a workflow file in it,
and [a reusable workflow can't be one](https://docs.pypi.org/trusted-publishers/troubleshooting/#reusable-workflows-on-github)
— so the tool's own `release.yml` publishes what this built:

```yaml
on:
  push:
    tags: ["v[0-9]+.[0-9]+.[0-9]+*"]

jobs:
  build:
    uses: kostavo-oss/.github/.github/workflows/python-release.yml@main

  publish:
    needs: build
    runs-on: ubuntu-latest
    environment: pypi
    permissions:
      id-token: write # PyPI Trusted Publishing (OIDC)
    steps:
      - uses: actions/download-artifact@v8
        with:
          name: dist
          path: dist
      - uses: pypa/gh-action-pypi-publish@release/v1
```

On PyPI, the tool's Trusted Publisher is then: owner `kostavo-oss`, the tool's
repository, workflow `release.yml`, environment `pypi`.

## License

[Apache-2.0](LICENSE).
