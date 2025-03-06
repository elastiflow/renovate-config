# renovate-config

Repo to host org-wide renovate configs/presets

* [Guide](https://docs.renovatebot.com/config-presets/)
* [Blog post](https://www.jvt.me/posts/2023/01/30/renovate-global-defaults/)
* [Package rules](https://docs.renovatebot.com/configuration-options/#packagerules)

Useful debug commands:

  ```sh
  docker run --rm -it -e GITHUB_COM_TOKEN='{GH_PAT}' -e LOG_LEVEL=debug --entrypoint=bash -v `pwd`:/usr/src/app ghcr.io/renovatebot/renovate:full
  renovate-config-validator --strict 
  renovate --platform=local
  ```
