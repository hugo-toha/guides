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

In this post, we are going to deploy the site we have created in previous post in [Github Pages](https://pages.github.com/). At first, make sure that your repository name is `<your username>.github.io`. Then, commit any local uncommitted changes and push into Github.


#### Setup Default Branch

GitHub don't serve a site from hugo templates directly. Instead, we have to provide the generated (HTML, CSS, JS etc.) files after building the site. From now, we are going to maintain two branches for our site. The `main` (previously known as `master`) branch will holds the generated contents after building the site. Github will serve the site from this branch. We will create another branch named `source`. This will hold our markdowns files and hugo templates.

Let's create the `source` branch `main` branch and push it into Github.

```bash
# create the source brach
$ git checkout -b source
# push the source branch into Github
$ git push origin source
```

Now, we are going to set the `source` branch as our default branch. Go to  `Settings > Branches` of your repository and replace `main` with `source` under `Default branch` section. Then, save the change by clicking `Update` button. A screenshot of the process is shown below:

{{< img src="/posts/getting-started/github-pages/images/set_default_branch.png" align="center" >}}

{{< vs 2 >}}
Going forward, all our developments will happen against this `source` branch.

#### Set Github Pages Branch

Now, we have to tell Github which branch we are using for holding generated contents. Go to the `Settings` of your repository. Scroll down until you find `Github Pages` section. Select `main` branch and `/(root)` directory under `Source` section.

{{< img src="/posts/getting-started/github-pages/images/github_pages_branch.png" align="center" >}}

#### Enable Github Action

We are going to automate the deploying process using [Github Actions](https://github.com/features/actions). At first, make sure that Github Action is enabled in your repository. Go to `Settings > Actions` of your repository and make sure `Action permissions` is set to `Allow all actions`. Here, is a screenshot of the respective setting:

{{< img src="/posts/getting-started/github-pages/images/enable_action.png" align="center" >}}

#### Add Workflow

We are going to use [peaceiris/actions-hugo](https://github.com/peaceiris/actions-hugo) action to set up hugo and [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages) to deploy the site. Create `.github` folder at the root of your repository. Then, create `workflows` folder inside the `.github` folder. Finally, create a `deploy-site.yaml` file inside the `workflows` folder and add the following content there:

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

This action will start on every push into the `source` branch. It will build the site and commit the generated content into `main` branch.

#### Deploy

If you have followed the guide properly, your site should be ready to deploy in Github Pages. Now, if you push any commit into your `source` branch, a Github Action will start and deploy your site automatically.

Push a commit into the `source` branch and go to `Actions` tab of your repository to verify that the action has started.

{{< img src="/posts/getting-started/github-pages/images/action_running.png" align="center" >}}

{{< vs 2 >}}

Now, wait for the actions to complete. If it completes successfully, you should see a green tick indicating successful run.

{{< img src="/posts/getting-started/github-pages/images/action_completed.png" align="center" >}}

{{< vs 2 >}}

Once the Github Action has completed successfully, you can browse your site at `https://<your username>.github.io`.

{{< img src="/posts/getting-started/github-pages/images/site_deployed.png" align="center" >}}
