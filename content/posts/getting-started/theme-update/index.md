---
title: "Automate Theme Update"
date: 2020-06-08T20:00:15+06:00
menu:
  sidebar:
    name: Automate Theme Update
    identifier: getting-started-theme-update
    parent: getting-started
    weight: 40
---

You might want to keep your site up-to-date with the latest version of theme to enjoy the latest features and fixes. In this post, we are going to setup a `Dependabot` Github app to automatically update the theme version. The app will check daily if there is any update in the submodules. If it finds any update in the theme, it will create a PR updating your site to the latest theme version.

### Setup Dependabot

Enable `Dependabot` in your repository by clicking `Enable Dependabot` button under `Insights > Dependency Graph > Dependabot` settings of your repository. For more information please check [GitHub Documentation](https://docs.github.com/en/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/enabling-and-disabling-version-updates). A screenshot has been given below that is showing the process:

{{< img src="enable_dependabot.png" align="center" >}}

{{< vs 2 >}}

Now, create a `dependabot.yml` file in the `.github` folder of your repository with the following content:

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

You are all set. Now, dependabot will check for sub-module update daily. It will create a PR to your site if it finds any update in the theme.

To know more about the configuration options of Dependabot, please visit [here](https://docs.github.com/en/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/configuration-options-for-dependency-updates).
