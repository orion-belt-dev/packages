# Orion Belt packages

Signed package repositories for [Orion Belt](https://github.com/orion-belt-dev/orion-belt),
served by GitHub Pages at **https://pkgs.orion-belt.dev**: the server and agent for
Linux, and the `osh`, `ocp` and `oadmin` clients for Linux, macOS, Windows, the BSDs,
illumos and Solaris.

```bash
curl -fsSL https://pkgs.orion-belt.dev/install.sh | sh                # clients
curl -fsSL https://pkgs.orion-belt.dev/install.sh | sh -s -- agent    # agent (Linux)
curl -fsSL https://pkgs.orion-belt.dev/install.sh | sh -s -- server   # server (Linux)
```

```powershell
irm https://pkgs.orion-belt.dev/install.ps1 | iex                     # clients (Windows)
```

| Distribution | Repository |
|--------------|------------|
| Debian, Ubuntu, Raspberry Pi OS | `deb [signed-by=/usr/share/keyrings/orion-belt.gpg] https://pkgs.orion-belt.dev stable main` |
| Fedora, RHEL, Rocky, Alma, openSUSE | `https://pkgs.orion-belt.dev/orion-belt.repo` |
| Alpine | `https://pkgs.orion-belt.dev/apk` |
| Arch Linux, Arch Linux ARM | `Server = https://pkgs.orion-belt.dev/archlinux/$arch` |

The site's front page has the full commands and the signing key's fingerprint.

## How it is published

The site is the `gh-pages` branch, not this `main` branch. Every release of
orion-belt rebuilds it from the release's files and force-pushes it as a single
commit (it holds the latest release only), with
[`scripts/publish-packages-pages.sh`](https://github.com/orion-belt-dev/orion-belt/blob/master/scripts/publish-packages-pages.sh).
See [PACKAGING.md](https://github.com/orion-belt-dev/orion-belt/blob/master/docs/PACKAGING.md).

To rebuild it from an existing release, in the orion-belt repository:

```bash
ORION_GPG_KEY=<fingerprint> make publish-packages-pages FROM_RELEASE=1 PUSH=1
```

The custom domain needs a DNS record `pkgs CNAME orion-belt-dev.github.io`
(not proxied, so GitHub can issue the HTTPS certificate). The site's `CNAME`
file keeps the Pages setting.
