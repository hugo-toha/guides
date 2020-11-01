---
title: "Deploy site in Github Pages"
date: 2020-06-08T22:00:20+06:00
hero: /posts/getting-started/github-pages/images/octocat.jpg
menu:
  sidebar:
    name: Deploy in Github Pages
    identifier: getting-started-github
    parent: getting-started
    weight: 20
---

In this post, we are going to go though the process of deploying a hugo static site in [Github Pages](https://pages.github.com/).


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

{{< img src="/posts/getting-started/github-pages/images/set_default_branch.png" align="center" >}}

Going forward, all our development will go against this `source` branch.

#### Set Github Pages Branch

`Settings -> Options` Scroll down until `Github Pages` section.

Make sure `Source` is set to `main` brach.

{{< img src="/posts/getting-started/github-pages/images/github_pages_branch.png" align="center" >}}

#### Enable Github Action

At first, make sure that Github Action is enabled in your repository. Go to `Settings > Actions` of your repository and make sure `Action permissions` is set to `Allow all actions`. Here, is a screenshot of the settings:

{{< img src="/posts/getting-started/github-pages/images/enable_action.png" align="center" >}}

#### Add Workflow

Now, create `.github` folder at the root of your repository. Then, create `workflows` folder inside `.github` folder. Finally, create `getting-started.yaml` inside the `workflows` folder and the following content there:

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



#### Deploy

##### Workflow Running

{{< img src="/posts/getting-started/github-pages/images/action_running.png" align="center" >}}

##### Workflow Completed

{{< img src="/posts/getting-started/github-pages/images/action_completed.png" align="center" >}}

##### Site Deployed

{{< img src="/posts/getting-started/github-pages/images/site_deployed.png" align="center" >}}