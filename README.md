# dxw Standardised Renovate Configs

This repository holds some standard configurations for [Renovate](https://www.mend.io/renovate/), our preferred dependency update bot.

## How to use

1. Install the [Renovate app](https://github.com/apps/renovate) for the repository, if not already installed.
1. Update the `renovate.json` file to extend our standard configuration:
   ```json
   {
     "$schema": "https://docs.renovatebot.com/renovate-schema.json",
     "extends": ["github>dxw/renovate-config:internal"]
   }
   ```
   If this is a new installation of Renovate then it will automatically open a new PR for this file.
1. Change any other [configuration options](https://docs.renovatebot.com/configuration-options/) specific to the repository.
1. If a new installation, merge the Renovate configuration PR.
1. If you have branch protection turned on and it requires reviews, make sure you either [bypass protections for Renovate or install renovate-approve](https://docs.renovatebot.com/key-concepts/automerge/#pull-requests-required).
