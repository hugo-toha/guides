---
title: "Quickstart"
date: 2022-08-09T00:00:00+06:00
description: Quick starting guide for the Toha theme
menu:
  sidebar:
    name: Quickstart
    identifier: quickstart
    weight: 2
---

**Greeting!** Thank you for deciding to use this theme. In this guide, I will show you how you can get started with this theme very quickly.

Here, I am going to assume that you want to start a fresh Hugo site using this theme. If you are already using Hugo for your site, then you must know how to use a theme. In that case, please follow this [sample repo](https://github.com/hugo-toha/hugo-toha.github.io) for further reference.

Now, let's get back into our mission. Simply, follow these 5 steps to get started with your site.

#### Step 1: Fork the example repo and rename

At first, **fork** this [sample repo](https://github.com/hugo-toha/hugo-toha.github.io) to your account. Then, rename the repo to whatever you want. If you want to use [Github Pages](https://pages.github.com/) to deploy your site, then rename it to `<your username>.github.io`. The sample repo comes with pre-configured Github Actions to publish the site in Github Pages and Netlify.

#### Step 2: Clone the forked repo locally

Once you have forked and renamed the repository, you can now clone the forked repository in your local machine for further changes. Use the `--recursive` flag with `git clone` command. This will force git to pull the theme locally.

```bash
git clone git@github.com:<your username>/<forked repo name> --recursive
```

#### Step 3: Change `config.yaml` file

Now, open the repository in an editor and change the following configurations in your `config.yaml` file located at the root of your repository.

##### Change the `baseURL`

At first change the `baseURL` to your site URL. If you want to use Github Pages to host your site, then set it as below:

```yaml
baseURL: https://<your username>.github.io
```

##### Change the  `gitRepo`

Now, change the `gitRepo` field under the `params` section to point to your forked repository. For example,

```yaml
gitRepo: https://github.com/<your username>/<your forked repo name>
```

##### Disable analytics or configure it properly

The sample repo comes with Google Analytics pre-configured. The analytics id point to the original site. So, either disable the analytics or configure it properly according to [this guide](/posts/analytics/).

You can disable the analytics by setting the following field under the `params.features` section:

```yaml
analytics:
  enabled: false
```

##### Disable news letter functionality

The sample repo comes with a pre-configured [mailchimp](https://mailchimp.com/) newsletter service. Disable it by setting the following field under the `params.footer` section.

```yaml
newsletter:
  enable: false
```

#### Step 4: Install Hugo and run the site locally

If you haven't installed Hugo already on your local machine, install it first by following the guide from [here](https://gohugo.io/getting-started/installing/). Then, run the site locally by running the following command:

```bash
hugo server -w
```

<br>

If everything goes right, you should see an output similar to this.
{{< img src="images/local_site.png" align="center" alt="Command to run site locally">}}

Now, go to [localhost:1313](http://localhost:1313/) in your browser and you should see your site running.

#### Step 5: Push the changes to Github

If you have come this far, it means your site is running locally without any issue. Let's push these changes to Github.

```bash
# stage all the changes
git add .

# commit the changes
git commit -m "Initial site setup" -s

# push the changes to Github
git push origin HEAD
```

### What Next

- Customize the background, logo, and a few other things of your site by following [this guide](/posts/configuration/site-parameters/).
- Add information about you by following [this guide](/posts/configuration/sections/about/).
- Add your skills information by following [this guide](/posts/configuration/sections/skills/).
- Add your experience information by following [this guide](/posts/configuration/sections/experiences).
- Deploy your site in Github Pages by following the guide from [here](/posts/getting-started/github-pages/).
- Deploy your site in Netlify by following the guide from [here](/posts/getting-started/netlify/).
