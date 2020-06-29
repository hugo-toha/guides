---
title: "Installation"
date: 2020-06-08T08:06:25+06:00
hero: /images/posts/installation/hero.svg
author:
  name: Md. Emruz Hossain
#   image: /assets/images/profile-image.jpg
categories:
- installation
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
baseURL: http://example.org/
languageCode: en-us
title: "Toha"
theme: "toha"

# Allow raw html in markdown file
markup:
  goldmark:
    renderer:
      unsafe: true

# Enable Google Analytics
googleAnalytics: <your google analytics id>

# Enable Disqus forum
disqusShortname: <your disqus short code>

# Enable global emoji support
enableEmoji: true

# Custom parameters
params:
  # background image of the landing page
  background: "images/background.jpg"

  # GitHub repo URL of your site
  gitRepo: <your site's Github repo URL>

  # specify whether you want to write blog post or not
  enableBlogPost: true

  # specify the list of custom menus that you want to show in the top navbar.
  # they will be separated by a divider from the main menus.
  customMenus:
  - name: Notes
    url: <your custom menu link>

  # some information about you
  author:
    name: "Jane Doe"
    image: "images/avatar.png"
    # give your some contact information. they will be used in the footer
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

Run your hugo site with this theme.

```console
hugo server -w
```

Don't panic if the generated site does not look like what have you seen in the demo. Now, you have to provide some data in `data` folder of your site.

Follow the posts giving step by step instructions for configuring your data folder from [here](https://toha.netlify.app/posts/configuration/home-section/home-section/).

You can also follow the sample format given in `themes/toha/exampleSite/data/sections` directory.
