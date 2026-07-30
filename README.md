# Orion Belt packages (GitHub Pages)

Public static mirror of `orion-belt-agent` packages for the console **Add agent** install script.

**Package base URL:** https://orion-belt-dev.github.io/packages

Content is published on the `gh-pages` branch (not this `main` branch).

## Refresh from a release

From the [orion-belt](https://github.com/orion-belt-dev/orion-belt) repo:

```bash
make publish-packages-pages FROM_RELEASE=1 PUSH=1
```

Or after `make packages`:

```bash
make publish-packages-pages PUSH=1
```

## Local alternative

```bash
make packages && make serve-packages   # http://127.0.0.1:8765
```
