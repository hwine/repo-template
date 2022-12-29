# repo-template

template for repositories -- focussed on Mozilla

# Assumptions

- You've set up your dev environment per our [dev environment
  docs](https://mozilla-hub.atlassian.net/wiki/spaces/SECENGOPS/pages/123241278/How+To+set+up+a+SecEng+dev+environment)
- You're not building a product, so the Apache 2.0 license is appropriate.
  ([reference](https://mozilla-hub.atlassian.net/wiki/spaces/SLP/pages/27394064/Licensing+Runbook+Software+Licensing+And+Code+Contribution+Between+Mozilla+And+Other+Orgs+Projects))
- You're working in Python, possibly using Docker

# Using this repo

There are 2 ways use this repo:
1. use it as a template when starting a new project
2. copy files from it into an existing project

## Tuning

Especially if you're using these files with an existing project, you may need to
tune the files to match the python version being used. Best practice is to
always work with the latest version of python possible, so we don't have to
update the code base for as long as possible.

For various reasons, you may need to work with an older version. If so, you'll
need to add that version in several places:
- ensure that version is installed on your dev machine:
  - `pyenv install 3.X.Y`  # install on your machine
  - `cd ${repo_checkout} ; pyenv local 3.X.Y `  # set as interpreter to use
- Add that version to the `tox.ini` file
- Set that version as the "base" version for the `pyupgrade` plugin for in
  `.pre-commit-config.yaml` file (usual format is `--py3X-plus`)

Even if you must use an older version, you're encouraged to _also_ support the
latest version (called 3.L.G (Latest & Greatest) here). This can easily be done
with `tox` and `pyenv` by adding the 3.L.G version as follows:
- install it:
  - `pyenv install 3.L.G`  # install on your machine
  - `cd ${repo_checkout} ; pyenv local 3.X.Y 3.L.G `  # set as interpreters to use
- Add that version to the `tox.ini` file

## Notes

Depending on your needs, you may want to comment out, or delete, some of the
pre-configured `pre-commit` hooks. In particular, the following hooks require
additional setup:

- `detect-secrets` helps avoid "oops" commits, but requires both:
  - `pipx install detect-secrets`
  - `detect-secrets scan > .secrets.baseline`  # from repo root
- `beautysh` for linting of shell scripts requires:
  - `pipx install beautysh`

For others, you'll may need to change default configurations or add exclude
files. By each hook definition in `.pre-commit-config.yaml`, doc links or common
config examples are given.
