---
title: "Automate Theme Update"
date: 2020-06-08T20:00:15+06:00
hero: /posts/getting-started/theme-update/configure-bot.svg
menu:
  sidebar:
    name: Automate Theme Update
    identifier: getting-started-theme-update
    parent: getting-started
    weight: 40
---

### Automate Theme Update

In this section, we are going to setup a `Dependabot` Github app to automatically update the theme version. The app will check daily if there is any update in the submodules. If there is any update, it will create a PR updating to the latest version.

- At first install `Dependabot`in your account/organization from [here](https://github.com/marketplace/dependabot-preview).
- Then, enable it in your repository by clicking `Enable Dependabot` button under `Insights > Dependency Graph > Dependabot` settings of your repository.

{{< img src="/posts/getting-started/theme-update/enable_dependabot.png" align="center" >}}

{{< vs >}}

- Now, create a `dependabot.yml` file in the `.github` folder of your repository with the following content:

```yaml
# Update dependencies

version: 2
updates:
# Update the git submodules
- package-ecosystem: "gitsubmodule"
  directory: "/"
  schedule:
    interval: "daily"
  labels:
  - "dependencies"
  - "automerge"
```

To know more configuration options for Dependabot, please visit [here](https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/configuration-options-for-dependency-updates).