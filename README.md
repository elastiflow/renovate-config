# Overview

Centralized repo for the shared Renovate configs

- [Guide](https://docs.renovatebot.com/config-presets/)
- [Config Presets doc](https://docs.renovatebot.com/presets-config/)
- [Blog post](https://www.jvt.me/posts/2023/01/30/renovate-global-defaults/)
- [Package rules](https://docs.renovatebot.com/configuration-options/#packagerules)

Note `tf-modules.json` and `go-cantina-band.json` present purely for backwards compatibility

## Test the config

Run the renovate in the container

```sh
  docker run --rm -it \
    -e GITHUB_COM_TOKEN='{GH_PAT}' \
    -e LOG_LEVEL=debug --entrypoint=bash \
    -v `pwd`:/usr/src/app ghcr.io/renovatebot/renovate:full
```

Useful renovate commands/hints:

- Validate the config

  ```sh
  renovate-config-validator --strict
  ```

- Dry-run renovate

  ```sh
  renovate --platform=local --dry-run=full
  ```

- Dry-run renovate to view packageFiles identified for version bumps

  ```sh
  echo "{$(renovate --platform=local --dry-run=full | awk '/DEBUG: packageFiles with updates/{f=1; next} /DEBUG/{f=0} f')}"
  ```

- Dry-run renovate to view extended branch details that are to be created. The info hints on which PRs are about to be created and what grouping is applied

  ```sh
  echo "{$(renovate --platform=local --dry-run=full | awk '/DEBUG: branches info extended/{f=1; next} /DEBUG/{f=0} f')}"
  ```

- Dry-run renovate to view extended branches summary that are to be created. The info hints on which PRs are about to be created and what grouping is applied

  ```sh
  echo "{$(renovate --platform=local --dry-run=full | awk '/DEBUG: Branch summary/{f=1; next} /DEBUG/{f=0} f')}"
  ```
