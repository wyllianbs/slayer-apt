# Slayer Editor — APT repository

Signed APT repository for the **Slayer Editor**, a lightweight Qt 6 code editor
with an embedded terminal (tabs, syntax highlighting, and F5 compile-and-run for
C, C++, Python, Rust, Go, JavaScript, Java and shell scripts).

- **Source code:** https://github.com/wyllianbs/SE
- **Repository URL:** https://wyllianbs.github.io/slayer-apt
- **License:** GPL-3.0-or-later
- **Architecture:** amd64 · **Suite:** `stable` · **Component:** `main`

Requires **Qt 6 ≥ 6.8.2**, available on Debian 13 (trixie) and newer, and on
recent Ubuntu releases.

## Install

There are two ways to install, pick one.

### Option 1 — via `extrepo` (recommended)

[`extrepo`](https://salsa.debian.org/extrepo-team/extrepo) manages the repository
source and signing key for you, in one command:

```bash
sudo apt install extrepo
sudo extrepo enable slayer-editor
sudo apt update
sudo apt install slayer-editor
```

> **Note:** the metadata entry is under review in
> [extrepo-data](https://salsa.debian.org/extrepo-team/extrepo-data/-/merge_requests/585).
> `extrepo enable slayer-editor` works once that merge request is accepted. Until
> then, use Option 2.

### Option 2 — manual

Repository URL: **https://wyllianbs.github.io/slayer-apt/**

```bash
# 1. Add the signing key
curl -fsSL https://wyllianbs.github.io/slayer-apt/slayer-editor.gpg.asc \
  | sudo gpg --dearmor -o /usr/share/keyrings/slayer-editor.gpg

# 2. Add the repository
echo "deb [signed-by=/usr/share/keyrings/slayer-editor.gpg] https://wyllianbs.github.io/slayer-apt stable main" \
  | sudo tee /etc/apt/sources.list.d/slayer-editor.list

# 3. Install
sudo apt update
sudo apt install slayer-editor
```

## Update

Once the repository is configured (either option), new releases are picked up
automatically:

```bash
sudo apt update && sudo apt upgrade
```

## Uninstall

```bash
sudo apt remove slayer-editor
```

If you used **Option 1 (extrepo)**, disable the repository with:

```bash
sudo extrepo disable slayer-editor
sudo apt update
```

If you used **Option 2 (manual)**, remove the source and key:

```bash
sudo rm /etc/apt/sources.list.d/slayer-editor.list /usr/share/keyrings/slayer-editor.gpg
sudo apt update
```

## Verify the signing key

The repository and its packages are signed with this GPG key:

```
Fingerprint: B6BD E0A3 F0DD CB58 3204  5883 B971 11B8 B62B 9BC1
Owner:       Wyllian Bezerra da Silva <wyllianbs@gmail.com>
```

It is the same key published on [mentors.debian.net](https://mentors.debian.net).
The public key is available at
[`slayer-editor.gpg.asc`](https://wyllianbs.github.io/slayer-apt/slayer-editor.gpg.asc).
