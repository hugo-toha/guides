---
title: "Configuring Site Parameters"
date: 2020-06-08T06:20:55+06:00
hero: /images/posts/configuration/home-section-hero.svg
menu:
  sidebar:
    name: Site Parameters
    identifier: configuration-site-parameters
    parent: configuration
    weight: 105
---

After installing this theme, when you first run your site, it will start with the default parameters. It should look similar to this example site except it will not have any sections on the homepage. Those sections are added via some data files. In the next few posts, I am going to show you how you can add those sections by providing the data files.

In this post, I am going to show you how you can change the site parameters to change background, logo, author information, and enable/disable various features.

### Add Background Image

At first, let's set a background on your website. Put your desired background image in the `static/images` directory. Then add the following in the `params` section of your `config.yaml` file.

```yaml
background: "images/<your background image name(with file extension)>"
```

### Add Site's Logo

Now, let's add a logo for your site. You have to provide two different logos. One is for the transparent navbar and another for the non-transparent navbar. Put your logos into `static/images` directory and add the following in the `params` section of `config.yaml` file.

```yaml
# The inverted logo will be used in the initial transparent navbar and
# the main logo will be used in the non-transparent navbar.
logo:
  main: /assets/images/main-logo.png
  inverted: /assets/images/inverted-logo.png
```

### Add Copyright Notice

Let's add a copyright notice for your site. This will be shown at the bottom of the footer. Add the following in `params` section of `config.yaml` file.

```yaml
copyright: © 2020 Copyright.
```

### Add Author Information

Now, provide your basic information. Add the following `author` section in `params` section of your `config.yaml` file.

```yaml
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

### Enable Blog Post

If you want to write some blog posts on your site, you have to enable it first. Let's enable blog posting by adding the following in the `params` section of your `config.yaml` file.

```yaml
enableBlogPost: true
```

### Enable `Table Of Contents`

Now, if you want to show `Table Of Contents` section in your blog post, you have to enable it in the `params` section of `config.yaml` file.

```yaml
enableTOC: true
```

You can also control the level of your TOC by adding the following configuration in the `markup` section of your `config.yaml` file.

```yaml
markup:
  tableOfContents:
    startLevel: 2
    endLevel: 6
    ordered: false
```

Here, we have configured our TOC to show all headings from `h2` to `h6`.

### Enable `<Improve This Page>` Button

If you want to provide the readers an easy way to improve a post (i.e. typo fix, indentation fix, etc.), you can enable `<Improve This Page>` button by adding your git repository URL in the `params` section of your `config.yaml` file.

```yaml
gitRepo: <your site's Github repo URL>
```

This will add a button labeled `Improve This Page` at the bottom of every blog post. The button will route the user directly to the respective edit page in Github.

### Add Custom Menus

If you want to add some custom menus in the navbar, you can easily add them by adding the following in the `params` section of `config.yaml` file.

```yaml
customMenus:
- name: Notes
  url: https://hossainemruz.gitbook.io/notes/
```

This is particularly helpful when you want to add a link to another site in the navbar.

### Enable/Disable Newsletter

Although the newsletter feature is not functional yet, it is shown in the footer for aesthetic purposes. You can hide it by adding following in the `params` section of  `config.yaml` file.

```yaml
newsletter:
  enable: false
```

I would love to add this functionality as soon as possible. However, I am not familiar with the services required to make this functional. If you know such services that provide this newsletter functionality, please let me know in the comment.

### Enable RAW HTML in the Markdown File

If you want to use RAW HTML in your markdown files, you have to enable unsafe rendering. Otherwise, Hugo will not render the HTML. You can enable unsafe markdown rendering by adding following `goldmark` settings in the `markup` section of `config.yaml` file.

```yaml
markup:
  goldmark:
    renderer:
      unsafe: true
```

### Example `params` Section

Finally, here is the `params` section used in this example site.

```yaml
# Site parameters
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
  gitRepo: https://github.com/hossainemruz/toha-example-site

  # specify whether you want to write some blog posts or not
  enableBlogPost: true

  # specify whether you want to show Table of Contents in reading page
  enableTOC: true

  # specify the list of custom menus that you want to show in the top navbar.
  # they will be separated by a divider from the main menus.
  customMenus:
  - name: Notes
    url: https://hossainemruz.gitbook.io/notes/

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
