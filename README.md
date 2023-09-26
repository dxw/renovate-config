# dxw Standardised Renovate Configs

**These are under development, and may change without warning. We recommend not using them (yet) for anything which is mission critical.**

This repository holds some standard configurations for [Renovate](https://www.mend.io/renovate/), our preferred dependency update bot.

## Behaviour

### Internal

The internal config (`internal.json`) is intended for dxw internal repos where the impact of changes is low. It implements the following behaviours:

- Will create a "Dependency Dashboard" issue for the repository, for tracking the state of updates and triggering some behaviours
- Automatically merges minor and patch updates to all dependencies between 10am and 4pm
- Opens a PR for all updates, and requires all tests to pass
- Requires all major updates to have a PR explicitly opened via the Dependency Dashboard
- Will wait three days following a package release before opening PRs (to allow time for broken versions to be yanked)
  - For NPM packages (which have a higher churn), will wait five days.

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
