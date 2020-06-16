---
title: "Configuring Home Section"
date: 2020-06-08T06:20:55+06:00
hero: /images/posts/configuration/home-section-hero.svg
author:
  name: Md. Emruz Hossain
#   image: /assets/images/profile-image.jpg
categories:
- configuration
- configuration-home-section
---

After installing this theme, when you first run your site it may not look like what you are seeing in this example site. This is because you haven't provided the site's data yet. This post will show you how to configure the `Home` section of the landing page.

At first, you have to create a folder named `data` in the root of your site if it was not created already. This folder will contain the site's data in YAML format. Here, we are going to create a `site.yaml` file that will contain the necessary information to build the `Home` section.

Now, create `site.yaml` file in `data` directory of your site. Then, follow the following steps to configure your site.

### Set Background Image

At first, let's set a background for your website. Put your desired background image in `static/images` directory. Then add the following in your `site.yaml` file,

```yaml
# background image of the landing page
background: "images/<your background image name(with file extension)>"
```

If you are running your site in watch mode (`hugo server -w`), after saving the `site.yaml` file you should see the background image has been set to your site.

### Set Author Information

Now, you have to provide your basic information. Add the following `author` section in your `site.yaml` file,

```yaml
# some information about you
author:
  name: "Jane Doe"
  image: "images/avatar.png"
  # give your some contact information. they will be used in the footer
  contactInfo:
    email: "janedoe@example.com"
    phone: "+0123456789"
  # a summary of what you do. this will be used to create the typing carousel.
  summary:
  - I am a Developer
  - I work with Go
  - I love to work with some fun projects
```

Once you have added the author section in `site.yaml`, you should see the profile image, greeting message, and the typing carousel is showing properly.

### Add Menu Information

You might have noticed that only `Blog` entry was shown in the top menubar. To show the other menus, you have to provide their information in `menus` section `site.yaml`. Add the following `menus` section in your `site.yaml` file.

```yaml
# Menus of the home page
menus:
- name: Home
  url: "#home"
  weight: 1
- name: About
  url: "#about"
  weight: 2
- name: Skills
  url: "#skills"
  weight: 3
- name: Experiences
  url: "#experiences"
  weight: 4
- name: Projects
  url: "#projects"
  weight: 5
- name: Recent Posts
  url: "#recent-posts"
  weight: 6
- name: Achievements
  url: "#achievements"
  weight: 7
```

Now, you should see the menus are showing properly on your site. You can add any additional menu if you want. Just provide the URL to point your content properly.

{{< vs 2 >}}

The following image shows how the contents of `site.yaml` is mapped to the `Home` section.

{{< img src="/images/posts/configuration/home.png" >}}

### Example `site.yaml` File

Here, is the `site.yaml` file that has been used to create the `Home` section of this site.

```yaml
# background image of the landing page
background: "images/background.jpg"

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

# Menus of the home page
menus:
- name: Home
  url: "#home"
  weight: 1
- name: About
  url: "#about"
  weight: 2
- name: Skills
  url: "#skills"
  weight: 3
- name: Experiences
  url: "#experiences"
  weight: 4
- name: Projects
  url: "#projects"
  weight: 5
- name: Recent Posts
  url: "#recent-posts"
  weight: 6
- name: Achievements
  url: "#achievements"
  weight: 7
```
