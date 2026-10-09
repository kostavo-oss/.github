# .github

What the [Kostavo tools](https://github.com/kostavo-oss) share without sharing code:

- [`profile/README.md`](profile/README.md) — the organisation's front page
- [`.github/workflows/`](.github/workflows) — a lint-and-test job any repo in the
  organisation can call (the tools themselves have their own CI in
  [`tools`](https://github.com/kostavo-oss/tools))
- [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE) and
  [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) — the defaults
  for any repo that doesn't bring its own
- [`SUPPORT.md`](SUPPORT.md) — where to ask a question, and where paid help is; also a
  default for any repo without its own
- [`SECURITY.md`](SECURITY.md) — how to report a vulnerability; a default too

## The workflows

Nothing calls it today: the tools share one repository and one workflow set. It stays
for a repo that wants a gate without writing one.

### `python-ci.yml`

`ruff check`, `ruff format --check`, and `pytest` on every supported Python.

```yaml
jobs:
  python:
    uses: kostavo-oss/.github/.github/workflows/python-ci.yml@main
    # with:
    #   python-versions: '["3.12", "3.13", "3.14"]'
```

| Input | Default | |
|---|---|---|
| `python-versions` | `'["3.11", "3.12", "3.13", "3.14"]'` | The Pythons to run the tests on, as a JSON list |

### Releases are per package

There is no shared release workflow. PyPI's Trusted Publisher is a repository and a
workflow file in it, and
[a reusable workflow can't be one](https://docs.pypi.org/trusted-publishers/troubleshooting/#reusable-workflows-on-github)
— so [`tools`](https://github.com/kostavo-oss/tools) has its own `release.yml`, and every
package releases the same way: a pull request bumps `version` in that package's
`pyproject.toml` and moves its changelog's notes under it, and merging it is the release.
The workflow sees a version on `main` that isn't out yet, runs the gate, publishes to PyPI
and makes the GitHub release and its tag (`<package>-vX.Y.Z`).

On PyPI, every tool's Trusted Publisher is: owner `kostavo-oss`, repository `tools`,
workflow `release.yml`, environment `pypi`.

## License

[Apache-2.0](LICENSE).
