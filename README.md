<!--
SPDX-FileCopyrightText: 2024 ThysTips <contact@thystips.net>

SPDX-License-Identifier: GPL-3.0-or-later
-->

Ansible Role: gh_assets
=========

Download assets from a Github Release.

TODO
---

- Add tests

Requirements
------------

N/A

Role Variables
--------------

- `gh_assets_github_token` | str : Github Personal Access Token to access private repositories (check `GH_TOKEN` env variable if unset).
- `gh_assets_github_api_version` | str : Github API version to use (default: `2022-11-28` : [](https://docs.github.com/fr/rest/about-the-rest-api/api-versions)).
- `gh_assets_src` | {} : Object containing the source repository and release to download assets from.
  - `repo` | str : Repository name
  - `owner` | str : Repository owner
  - `tag` | str : Release tag - `latest` (get latest release) or specific tag set
  - `download_sources_tarball` | bool : Download sources tarball (default: `false`)
  - `download_assets` | bool : Download assets (default: `true`) - useful to download sources only
  - `download_all_assets` | bool : Download all assets (default: `false`) - if `true`, all assets will be downloaded
  - `asset_name` | str : Asset name to download (default: undefined) - if not set and `download_all_assets` is `false`, the first asset will be downloaded
- `gh_assets_dst` | {} : Object containing the destination directory to download assets to.
  - `path` | str : Directory to download assets to (default: `/tmp`)
  - `asset_name` | str : File name for downloaded asset (default undefined) - if not set and `download_all_assets` is `false`, asset keeps its original name
  - `tarball_name` | str : File name for downloaded sources tarball (default undefined) - if not set, tarball keeps its original name (`<repo-name>-<tag-name>`)
  - `owner` | str : Owner of the directory (optional)
  - `group` | str : Group of the directory (optional)
  - `mode` | str : Mode of the directory (optional)

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: weytop.infrastructure.gh_assets
           gh_assets_github_token: "your_github_token"
           gh_assets_src:
             owner: "grafana"
             repo: "mimir"
             asset_name: "mimir-linux-amd64-sha-256"

License
-------

GPL-3.0-or-later

Author Information
------------------

This role was created in 2024 by [ThysTips](https://thystips.net).
