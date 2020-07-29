# work-template-python

template for work based Python projects

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
