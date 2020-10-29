---
title: "Deploy site in Github Pages"
date: 2020-06-08T06:00:20+06:00
hero: /images/posts/writing-posts/git.svg
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

At first, create a repo named `<your user name>.github.io`. Please, add a README or LICENSE file. It will be helpful later. You can also fork the following example repository [toha-theme/toha-theme.github.io](https://github.com/toha-theme/toha-theme.github.io) and replace `toha-theme` part with your own username.

#### Setup Default Branch

GitHub Pages don't serve from a hugo site directly. Instead, we have to provide the generated files after running `hugo --minify` command. So, we are going to maintain two branches. The `main` (previously known as `master`) brach will host the generated contents. Github will serve the site from this branch. We will create another branch named `source`. This will hold our markdowns files and hugo templates.

Let's create the `source` brach:

- At first, clone the repository to your local machine.

```bash
$ git clone git@github.com:toha-theme/toha-theme.github.io.git
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

{{< img src="/images/deploy-site/github/set_default_branch.png" align="center" >}}

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
$ git submodule add https://github.com/hossainemruz/toha.git themes/toha
```

{{< vs 1 >}}

>Don't use SSH URL of the theme during adding it as git sub-module. Also, don't clone the theme in your `themes` directory using `git clone`. Otherwise, we won't be able to automate the site publishing.


#### Configure Site

Now, we are ready to configure our theme.

#####  Update `config.yaml`

##### Add Sections

##### Add Posts

### Publishing Site

#### Enable Github Action

#### Add Workflow

### Automate Theme Update
