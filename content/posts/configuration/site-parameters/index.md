---
title: "Configuring Site Parameters"
date: 2020-06-08T06:20:55+06:00
menu:
  sidebar:
    name: Site Parameters
    identifier: configuration-site-parameters
    parent: configuration
    weight: 105
---
{{< alert type="danger" >}}
This doc is outdated. For up-to-date examples, please follow this sample [repo](https://github.com/hugo-toha/hugo-toha.github.io).
{{< /alert >}}

After installing this theme, when you first run your site, it will start with the default parameters. It should look similar to this example site except it will not have any sections on the homepage. Those sections are added via some data files. In the next few posts, I am going to show you how you can add those sections by providing the data files.

In this post, I am going to show you how you can change the site parameters to change background, logo, author information, and enable/disable various features.

### Add Background Image

At first, let's set a background on your website. Put your desired background image in the `assets/images` directory. Then add the following in the `params` section of your `config.yaml` file.

```yaml
background: "images/<your background image name(with file extension)>"
```

### Add Site's Logo

Now, let's add a logo for your site. You have to provide two different logos. One is for the transparent navbar and another for the non-transparent navbar. Put your logos into `assets/images` directory and add the following in the `params` section of `config.yaml` file.

```yaml
# The inverted logo will be used in the initial transparent navbar and
# the main logo will be used in the non-transparent navbar.
logo:
  main: images/main-logo.png
  inverted: images/inverted-logo.png
  favicon: images/favicon.png
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

If your default branch isn't called `main` then you need to add your git default branch in the `params` section of your `config.yaml` file.

```yaml
gitBranch: <your git default branch name>
```

### Enable/Disable Newsletter

The newsletter feature only supports Mailchimp for now.  
Add the following in the `params` section of `config.yaml` file.

```yaml
newsletter:
  enable: true
  provider: mailchimp
  mailchimpURL: https://github.us1.list-manage.com/subscribe/post?u=19de52a4603135aae97163fd8&amp;id=094a24c76e
```

If you don't want to use the newsletter feature, you can hide it by adding following in the `params` section of  `config.yaml` file.

```yaml
newsletter:
  enable: false
```

### Enable RAW HTML in the Markdown File

If you want to use RAW HTML in your markdown files, you have to enable unsafe rendering. Otherwise, Hugo will not render the HTML. You can enable unsafe markdown rendering by adding following `goldmark` settings in the `markup` section of `config.yaml` file.

```yaml
markup:
  goldmark:
    renderer:
      unsafe: true
```

### Add Author Information

Now, provide your basic information. Create a `author.yaml` file in your `/data` directory and add the author information there.

```yaml
# some information about you
name: "Jane Doe"
nickname: "Jane"
image: "images/avatar.png"

# greeting message before your name. it will default to "Hi! I am" if not provided
greeting: "Hi, I am"

# give your contact information. they will be used in the footer
contactInfo:
  email: "janedoe@example.com"
  phone: "+0123456789"
  stack-overflow:
    icon: stack-overflow
    url: "https://stackoverflow.com/users/1/exampleUser"
    text: "ExampleUser"

# a summary of what you do
summary:
- I am a Developer
- I work with Go
- I love to work with some fun projects
```

> Note: `contactInfo` paramerters will use the `icon` parameter to find the icon. This parameter must match the font awesome icon names [examples](https://fontawesome.com/search?o=r&f=brands)

### Add Copyright Notice

Let's add a copyright notice for your site. This will be shown at the bottom of the footer. Create `site.yaml` file in your `/data` directory and add the following section there.

```yaml
copyright: © 2020 Copyright.
```

### Site's Description

Now, add a description of your site that will help the search engines to find your site. Add a description section in your `site.yaml` file.

```yaml
# Meta description for your site.  This will help the search engines to find your site.
description: Example site for hugo theme Toha.
```

### Add Custom Menus

If you want to add some custom menus in the navbar, you can easily add them by adding the following in the `site.yaml` file. Custom menus are visible in the navigation bar by default. To hide them, set `hideFromNavbar` to `true`. Custom menus are hidden from the footer's navigation area by default. To show a custom menu item in the footer, set its `showOnFooter` property to `true`.

```yaml
customMenus:
- name: Notes
  url: https://hossainemruz.gitbook.io/notes/
  hideFromNavbar: false
  showOnFooter: true
```

This is particularly helpful when you want to add a link to another site in the navbar.

### Example `params` Section

Finally, here is the `params` section used in this example site.

```yaml
# Site parameters
params:
  # background image of the landing page
  background: "images/background.jpg"

  # Provide logos for your site. The inverted logo will be used in the initial
  # transparent navbar and the main logo will be used in the non-transparent navbar.
  # It will default to the theme logos if not provided.
  logo:
    main: images/main-logo.png
    inverted: images/inverted-logo.png
    favicon: images/favicon.png

  # GitHub repo URL of your site
  gitRepo: https://github.com/hossainemruz/toha-example-site

  # specify whether you want to write some blog posts or not
  enableBlogPost: true

  # specify whether you want to show Table of Contents in reading page
  enableTOC: true

  # Provide newsletter configuration. This feature hasn't been implemented yet.
  # Currently, you can just hide it from the footer.
  newsletter:
    enable: true
```
