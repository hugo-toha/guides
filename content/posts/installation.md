---
title: "Installation"
date: 2020-06-08T08:06:25+06:00
hero: /images/posts/installation/hero.svg
description: Installation guide for Hugo theme Toha
menu:
  sidebar:
    name: Installation
    identifier: installation
    weight: 10
---

This post will give you step by step instructions on how to install and use this theme.

### Requirements

- Hugo Version 0.68.0 or higher

### Installation

- Create your site if you haven't already

```console
hugo new site my-site -f=yaml
cd my-site
git init
```

- Add the theme as git sub-module

```console
git submodule add https://github.com/hossainemruz/toha.git themes/toha
```

{{< vs 1 >}}

>Don't use SSH URL of the theme during adding as git sub-module. Also, don't clone the theme in your `themes` directory using `git clone`. They don't work well with Github Action or Netlify.

If you want to customize the theme templates, then fork it and use the fork as your theme.

### Configuration

Configure your `config.yaml` file of your site as below:

```yaml
baseURL: https://toha.netlify.app

languageCode: en-us
title: "<Your site Title>"
theme: "toha"

# Allow raw html in markdown file
markup:
  goldmark:
    renderer:
      unsafe: true
  tableOfContents:
    startLevel: 2
    endLevel: 6
    ordered: false

# Enable Google Analytics
googleAnalytics: <your site's google analytics id>
# Enable Disqus forum
disqusShortname: <your site's disqus short code>

# Enable global emoji support
enableEmoji: true

# Custom parameters
params:
  # copyright
  copyright: © 2020 Copyright.

  # background image of the landing page
  background: "images/background.jpg"

  # Provide logos for your site. The inverted logo will be used in the initial
  # transparent navbar and the main logo will be used in the non-transparent navbar.
  # It will default to the theme logos if not provided.
  logo:
    main: /assets/images/main-logo.png
    inverted: /assets/images/inverted-logo.png

  # GitHub repo URL of your site
  gitRepo: <your site's Github repo URL>

  # specify whether you want to write some blog posts or not
  enableBlogPost: true

  # specify whether you want to show Table of Contents in reading page
  enableTOC: true

  # specify the list of custom menus that you want to show in the top navbar.
  # they will be separated by a divider from the main menus.
  customMenus:
  - name: Notes
    url: <your custom menu link>

  # Provide newsletter configuration. This feature hasn't been implemented yet.
  # Currently, you can just hide it from the footer.
  newsletter:
    enable: true

  # some information about you
  author:
    name: "Jane Doe"
    nickname: "Jane"
    image: "images/avatar.png"
    # give your contact information. they will be used in the footer
    contactInfo:
      email: "janedoe@example.com"
      phone: "+0123456789"
    # a summary of what you do
    summary:
    - I am a Developer
    - I work with Go
    - I love to work with some fun projects
```

You can just copy the content for `config.yaml` files from `theme/toha/exampleSite/config.yaml`.

### Usage

Run your Hugo site with this theme.

```console
hugo server -w
```

When you first run your site, it will start with the default parameters. It should look similar to the [example site](https://toha.netlify.app) except it will not have any sections in the homepage. Those sections are added via some data files.

You can configure your site by following the step by step guides from [here](https://toha.netlify.app/posts/configuration/).
