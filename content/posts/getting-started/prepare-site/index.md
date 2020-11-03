---
title: "Prepare Your Site"
date: 2020-06-08T23:00:20+06:00
hero: /posts/getting-started/prepare-site/octocat.jpg
menu:
  sidebar:
    name: Prepare Site
    identifier: getting-started-prepare-site
    parent: getting-started
    weight: 10
---

Greeting! Thank you for deciding to use this theme. In this post, we are going to create a hugo site from scratch. Then, we will configure it with `Toha` theme, make it multilingual, add some example posts. At the end of this post, you should be able to run a fully functional hugo site with `Toha` theme locally.

If you want a head start, you can just fork [hugo-toha/hugo-toha.github.io](https://github.com/hugo-toha/hugo-toha.github.io) repo, rename it and update with your own data. This repo has already been configured to deploy in [Github Pages](https://pages.github.com/) and [Netlify](https://www.netlify.com/).

If you already have a hugo site, skip to the [Add Theme](#add-theme) section.

### Create Repository

At first, create a repository in Github. If you want to deploy this site in Github Pages, your repo named should be `<your user name>.github.io`. Clone the repository into your local machine and navigate into it.

### Create Site

Now, make sure that you have [Hugo](https://gohugo.io/getting-started/installing/) installed. This theme should work with hugo version `v0.68.0` and later. Now, run the following command in the root of your repository to initiate a hugo website.

```console
$ hugo new site ./ -f=yaml --force
```

This command will create a basic hugo site structure. Here, `-f=yaml` flag tells hugo to create configuration file in YAML format and `--force` flag forces hugo to create a site even if the target directory is not empty.

### Add Theme

Now, it is time to add a theme into your site. Add Toha theme as git sub-module of your repository using the following command:

```console
$ git submodule add https://github.com/hugo-toha/toha.git themes/toha
```

{{< vs 1 >}}

>Don't use SSH URL of the theme during adding it as git sub-module. Also, don't clone the theme in your `themes` directory using `git clone`. Otherwise, we won't be able to automate the site publishing using Github Action or Netlify.

### Run Site Locally

Now, you can already run your site locally. Let's run the site in watch mode using the following command:

```console
$ hugo server -t toha -w
```
If you navigate to `http://localhost:1313`, you should see a basic site with Toha theme. In the next section, we are going to configure the site to look like the [hugo-toha.github.io](https://hugo-toha.github.io/). As we have run the server in watch mode, any changes we make to the site will be instantly visible in the browser.

### Configure Site

Now, we are ready to configure our site. In this section, we are going to add  author information, different sections, and sample posts etc.

####  Update `config.yaml`

When you have created the site using `hugo new site` command, it has created a `config.yaml` file in the root of your repository. Replace the default content of the `config.yaml` file with the following:

```yaml
baseURL: https://hugo-toha.github.io

languageCode: en-us
title: "John's Blog"
theme: "toha"

# Manage languages
# For any more details, you can check the official documentation: https://gohugo.io/content-management/multilingual/
languages:
  en:
    languageName: English
    weight: 1

# Control TOC depth
markup:
  tableOfContents:
    startLevel: 2
    endLevel: 6
    ordered: false

# Enable global emoji support
enableEmoji: true

# Site parameters
params:
  # GitHub repo URL of your site
  gitRepo: https://github.com/hugo-toha/hugo-toha.github.io

  # specify whether you want to write some blog posts or not
  enableBlogPost: true

  # specify whether you want to show Table of Contents in reading page
  enableTOC: true

  # Provide newsletter configuration. This feature hasn't been implemented yet.
  # Currently, you can just hide it from the footer.
  newsletter:
    enable: true
```

Here, you are seeing a basic configuration for Toha theme. You can see the configuration file used in the example site form [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/config.yaml). For more detailed configuration options, please check [this post](https://toha-guides.netlify.app/posts/configuration/site-parameters/).

#### Add Data

Most of the contents of this theme is driven by some YAML files in `data` directory. In this section, we are going to add some sample data. Since, we building a multilingual site, we are going to keep the data for each language separate into their own locale folder.

At first, create `en` folder inside your `data` directory. We are going to add data for `English` language here.

##### Site Information

Now, create a `site.yaml` file inside `/data/en/` directory of your repository. Add the following content there:

```yaml
# Copyright Notice
copyright: © 2020 Copyright.

# Meta description for your site.  This will help the search engines to find your site.
description: Portfolio and personal blog of John Doe.
```
To see all the available options for site information, check [this sample file](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/site.yaml).

##### Author Information

Now, create a `author.yaml` file in `/data/en/` directory and add your information there as below:

```yaml
# some information about you
name: "John Doe"
nickname: "John"
# greeting message before your name. it will default to "Hi! I am" if not provided
greeting: "Hi, I am"
image: "images/author/john.png"
# give your some contact information. they will be used in the footer
contactInfo:
  email: "johndoe@example.com"
  phone: "+0123456789"

# some summary about what you do
summary:
  - I am a Developer
  - I am a Devops
  - I love servers
  - I work on open-source projects
  - I love to work with some fun projects
```

##### Add Sections

Now, we are going to add different sections into our home page. At first, create a `sections` folder inside your `/data/en` directory. Here, we are going to add few sections with minimum configurations. In order to see detailed configuration options for the sections, please visit [here](https://toha-guides.netlify.app/posts/configuration/sections/).

###### About Section

Create `about.yaml` file inside your `/data/en/sections/` directory. Then add the following contents there:

```yaml
# section information
section:
  name: About
  id: about
  enable: true
  weight: 1
  showOnNavbar: true
  template: sections/about.html

# your designation
designation: Software Engineer
# your company information
company:
  name: Example Co.
  url: "https://www.example.com"

# your resume. this file path should be relative to you "static" directory
resume: "files/resume.pdf"

# a summary about you
summary: 'I am a passionate software engineer with x years of working experience. I built OSS tools for [Kubernetes](https://kubernetes.io/) using GO. My tools help people to deploy their workloads in Kubernetes. Sometimes, I work on some fun projects such as writing a theme, etc.'

# your social links
# give as many as you want. use font-awesome for the icons.
socialLinks:
- name: Github
  icon: "fab fa-github"
  url: "https://www.github.com/example"

# your soft skills
# give the percentage between 50 to 100 with 5 intervals.
# currently supported colors: blue, yellow, pink, green, sky, orange
softSkills:
- name: Leadership
  percentage: 85
  color: blue
- name: Team Work
  percentage: 90
  color: yellow
```

Put the `resume.pdf` file in `/static/files` directory of your repository. You can find the `about.yaml` file used in the example site from [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/about.yaml).

###### Skills Section

Create `skills.yaml` file inside your `/data/en/sections/` directory. Then add the following contents there:

```yaml
# section information
section:
  name: Skills
  id: skills
  enable: true
  weight: 2
  showOnNavbar: true
  # Can optionally hide the title in sections
  # hideTitle: true

# Your Skills.
# Give a summary of you each skill in the summary section.
skills:
- name: Kubernetes
  icon: "/images/sections/skills/kubernetes.png"
  summary: "Capable of deploying, managing application on Kubernetes. Experienced in writing Kubernetes controllers for CRDs."
  url: "https://kubernetes.io/"

- name: Go Development
  icon: "/images/sections/skills/go.png"
  summary: "Using as the main language for professional development. Capable of writing scalable, testable, and maintainable program."
  url: "https://golang.org/"

- name: Cloud Computing
  icon: "/images/sections/skills/cloud.png"
  summary: "Worked with most of the major clouds such as GCP, AWS, Azure etc."
```

Put the skills images into `/static/images/sections/skills/` directory of your repository. You will find the images [here](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/static/images/sections/skills). Also, you can find the `skills.yaml` file used in the example site from [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/skills.yaml).

###### Experiences Section

Create `experiences.yaml` file inside your `/data/en/sections/` directory. Then add the following contents there:

```yaml
# section information
section:
  name: Experiences
  id: experiences
  enable: true
  weight: 3
  showOnNavbar: true
  # Can optionally hide the title in sections
  # hideTitle: true 

# Your experiences
experiences:
- company:
    name: Example Co.
    url: "https://www.example.com"
    location: Dhaka Branch
    # company overview
    overview: Example Co. is a widely recognized company for cloud-native development. It builds tools for Kubernetes.
  positions:
  - designation: Senior Software Engineer
    start: Nov 2019
    # don't provide end date if you are currently working there. It will be replaced by "Present"
    # end: Dec 2020
    # give some points about what was your responsibilities at the company.
    responsibilities:
    - Design and develop XYZ tool for ABC task
    - Design, develop and manage disaster recovery tool [Xtool](https://www.example.com) that backup Kubernetes volumes, databases, and cluster's resource definition.
    - Lead backend team.

- company:
    name: PreExample Co.
    url: "https://www.preexample.com"
    location: Nowhere
    overview: PreExample Co. is a gateway company to enter into Example co. So, nothing special here.
  positions:
  - designation: Software Engineer
    start: March 2016
    end: May 2017
    responsibilities:
    - Write lots of example codes.
    - Read lots of examples.
    - See lots of example videos.
```

You can find the `experiences.yaml` file used in the example site from [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/experiences.yaml).

###### Project Section

Create `projects.yaml` file inside your `/data/en/sections/` directory. Then add the following contents there:

```yaml
# section information
section:
  name: Projects
  id: projects
  enable: true
  weight: 4
  showOnNavbar: true
  # Can optionally hide the title in sections
  # hideTitle: true

# filter buttons
buttons:
- name: All
  filter: "all"
- name: Professional
  filter: "professional"
- name: Academic
  filter: "academic"
- name: Hobby
  filter: "hobby"

# your projects
projects:
- name: Kubernetes
  logo: /images/sections/projects/kubernetes.png
  role: Contributor
  timeline: "March 2018 - Present"
  repo: https://github.com/kubernetes/kubernetes # If your project is a public repo on GitHub, then provide this link. it will show star count.
  #url: ""  # If your project is not a public repo but it has a website or any external details url then provide it here. don't provide "repo" and "url" simultaneously.
  summary: Production-Grade Container Scheduling and Management.
  tags: ["professional", "kubernetes", "cloud"]

- name: Tensorflow
  logo: /images/sections/projects/tensorflow.png
  role: Developer
  timeline: "Jun 2018 - Present"
  repo: https://github.com/tensorflow/tensorflow
  #url: ""
  summary: An Open Source Machine Learning Framework for Everyone.
  tags: ["professional", "machine-learning","academic"]

- name: Toha
  logo: /images/sections/projects/toha.png
  role: Owner
  timeline: "Jun 2019 - Present"
  repo: https://github.com/hossainemruz/toha
  summary: A Hugo theme for personal portfolio.
  tags: ["hobby","hugo","theme","professional"]
```
Put the projects images into `/static/images/sections/projects/` directory of your repository. You will find the images [here](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/static/images/sections/projects). Also, you can find the `projects.yaml` file used in the example site from [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/projects.yaml).

###### Recent Posts Section

Create `recent-posts.yaml` file inside your `/data/en/sections/` directory. Then add the following contents there:

```yaml
# section information
section:
  name: Recent Posts
  id: recent-posts
  enable: true
  weight: 5
  showOnNavbar: true
```

You can find the `recent-posts.yaml` file used in the example site from [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/recent-posts.yaml).

> This section will be empty until you add any post in your site.

###### Achievements Section

Create `achievements.yaml` file inside your `/data/en/sections/` directory. Then add the following contents there:

```yaml
# section information
section:
  name: Achievements
  id: achievements
  enable: true
  weight: 6
  showOnNavbar: true
  # Can optionally hide the title in sections
  # hideTitle: true

# Your achievements achievements
achievements:
- title: Best Presenter
  image: /images/sections/achievements/presenter.jpg
  summary: Best presenter in the 2020 XYZ conference.
- title: Champion
  image: /images/sections/achievements/sport.jpg
  summary: Champion in cycling inter-city cycling championship 2020.
- title: Graduation
  image: /images/sections/achievements/graduation-cap.jpg
  summary: Received Bachelor of Science (B.Sc.) in Computer Science and Engineer from XYZ University.
- title: Award Winner
  image: /images/sections/achievements/woman-winner.jpg
  summary: Wined best paper award at IEE Conference 2020.
```
Put the projects images into `/static/images/sections/achievements/` directory of your repository. You will find the images [here](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/static/images/sections/achievements). Also, you can find the `achievements.yaml` file used in the example site from [here](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/achievements.yaml).

#### Add Posts

Now, we are ready add our first post into our site. Here, we are going to add this [introduction post](https://hugo-toha.github.io/posts/introduction/).

- At first, create a `posts` folder inside `content` directory of your site.
- Then, create `_index.md` file inside the `posts` directory. Copy the content of [this file](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/_index.md) file andd paste into the newly created `_index.md` file.
- Create `introduction` folder inside your `posts` directory.
- Add the following [hero.svg](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/introduction/hero.svg) inside your `introduction` folder.
- Now, create `index.md` file inside the `introduction` folder. This `index.md` file will hold the post contents.
- Add the following [sample contents](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/introduction/index.md) in the newly created `index.md` file.

Now, your post should appear at `http://localhost:1313/posts` and your `Recent Posts` section also should show this post card. For translating a post, just create a new file with name `index.<language code>.md` in the same directory. Then, add the translated content there.

For more sample posts, please visit [here](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/content/posts).

### What Next

At this point, your site should look similar to the [example site](https://hugo-toha.github.io/). Now, it's time to deploy your site. You can follow the following deployments guides:

- [Deploy in Github Pages](https://toha-guides.netlify.app/posts/getting-started/github-pages/)
- [Deploy in Netlify](https://toha-guides.netlify.app/posts/getting-started/netlify/)