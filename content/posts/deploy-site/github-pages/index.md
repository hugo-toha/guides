---
title: "Deploy site in Github Pages"
date: 2020-06-08T06:00:20+06:00
hero: /posts/deploy-site/github-pages/images/hero.svg
menu:
  sidebar:
    name: Github Pages
    identifier: deploy-site-github
    parent: deploy-site
    weight: 10
---

In this post, we are going to go though the process of deploying a hugo static site in [Github Pages](https://pages.github.com/). Here, we are going to create a hugo site from scratch, configure it with Toha theme, make it multilingual, add some example content, and finally deploy it in Github Pages.

### Preparing Github Repository

In this section, we are going to prepare an empty repository in Github for our example site. Then, on the later sections we will work on creating the desired site and deploying it in Github.

#### Create Github Repository

At first, create a repo named `<your user name>.github.io`. Please, add a README or LICENSE file. It will be helpful later. You can also fork the following example repository [hugo-toha/hugo-toha.github.io](https://github.com/hugo-toha/hugo-toha.github.io) and replace `hugo-toha` part with your own username.

#### Setup Default Branch

GitHub Pages don't serve from a hugo site directly. Instead, we have to provide the generated files after running `hugo --minify` command. So, we are going to maintain two branches. The `main` (previously known as `master`) brach will host the generated contents. Github will serve the site from this branch. We will create another branch named `source`. This will hold our markdowns files and hugo templates.

Let's create the `source` brach:

- At first, clone the repository to your local machine.

```bash
$ git clone git@github.com:hugo-toha/hugo-toha.github.io.git
```

- Now, enter into the repository and create a new branch named `source`.
```bash
$ git checkout -b source
```

- Finally, push the brach into Github.

```bash
$ git push origin source
```

Now, let's set the `source` branch as our default branch. Go to  `Settings > Branches` of your repository and replace `main` with `source` under `Default branch` section. Then, save the change by clicking `Update` button. A screenshot of the process is shown below:

{{< img src="/posts/deploy-site/github-pages/images/set_default_branch.png" align="center" >}}

Going forward, all our development will go against this `source` branch.

### Preparing Site

In this section, we are going to create our hugo site. Then, we will configure our site using Toha theme.

#### Create Site

At first make sure that you have [Hugo](https://gohugo.io/getting-started/installing/) installed. Then, run the following command in the root of your repository to initiate a hugo website.

```bash
$ hugo new site ./ -f=yaml --force
```

This will create a basic hugo site structure. If you run `hugo server` at this stage and navigate to the server url (typically `http://localhost:1313`), you will see a blank page.

#### Add Theme

Now, it is time to add Toha theme into our site. Add the theme as git sub-module of your repository using the following command:

```console
$ git submodule add https://github.com/hugo-toha/toha.git themes/toha
```

{{< vs 1 >}}

>Don't use SSH URL of the theme during adding it as git sub-module. Also, don't clone the theme in your `themes` directory using `git clone`. Otherwise, we won't be able to automate the site publishing.


#### Configure Site

Now, we are ready to configure our theme.

#####  Update `config.yaml`

##### Add Site Data

##### Add Author Data

##### Add Sections Data

##### Add Posts

### Publishing Site

#### Enable Github Action

At first, make sure that Github Action is enabled in your repository. Go to `Settings > Actions` of your repository and make sure `Action permissions` is set to `Allow all actions`. Here, is a screenshot of the settings:

{{< img src="/posts/deploy-site/github-pages/images/enable-action.png" align="center" >}}

#### Add Workflow

Now, create `.github` folder at the root of your repository. Then, create `workflows` folder inside `.github` folder. Finally, create `deploy-site.yaml` inside the `workflows` folder and the following content there:

```yaml
name: Deploy to Github Pages

# run when a commit is pushed to "source" branch
on:
  push:
    branches:
    - source

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
    # checkout to the commit that has been pushed
    - uses: actions/checkout@v2
      with:
        submodules: true  # Fetch Hugo themes (true OR recursive)
        fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod
    
    # install Hugo
    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: '0.77.0'
        extended: true

    # build website
    - name: Build
      run: hugo --minify

    # push the generated content into the `main` (former `master`) branch.
    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_branch: main # if your main branch is `master` use that here.
        publish_dir: ./public
```

You are all set. Now, if you commit commit the changes into your `source` branch. A Github Action will start. Wait for the Github Action to complete.

### Automate Theme Update

In this section, we are going to setup a `Dependabot` Github app to automatically update the theme version. The app will daily check if there is any update in the submodules. If there is any update, it will create a PR updating to the latest version.

- At first install `Dependabot`in your account/organization from [here](https://github.com/marketplace/dependabot-preview).
- Then, enable it in your repository by clicking `Enable Dependabot` button under `Insights > Dependency Graph > Dependabot` settings of your repository.
{{< img src="/posts/deploy-site/github-pages/images/enable-dependabot.png" align="center" >}}

{{< vs >}}

- Now, create a `dependabot.yml` file in the root of your repository with the following content:

```yaml
```
