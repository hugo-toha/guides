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

You might want to keep your site up-to-date with the latest version of theme to enjoy the latest features and fixes. In this post, we are going to setup a `Dependabot` Github app to automatically update the theme version. The app will check daily if there is any update in the submodules. If it finds any update in the theme, it will create a PR updating your site to the latest theme version.

### Setup Dependabot

At first install `Dependabot`in your account/organization from [here](https://github.com/marketplace/dependabot-preview). Then, enable it in your repository by clicking `Enable Dependabot` button under `Insights > Dependency Graph > Dependabot` settings of your repository. A screenshot has been given below that is showing the process:

{{< img src="/posts/getting-started/theme-update/enable_dependabot.png" align="center" >}}

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

You are all set. Now, depndabot will check for sub-module update daily. It will create a PR to your site if it find any update in the theme.

To know more about the configuration options of Dependabot, please visit [here](https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/configuration-options-for-dependency-updates).
