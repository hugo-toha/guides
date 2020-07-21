---
title: "Configuring About Section"
date: 2020-06-08T06:20:50+06:00
hero: /images/posts/configuration/about-section-hero.svg
menu:
  sidebar:
    name: About Section
    identifier: configuration-about
    parent: configuration
    weight: 110
---

{{< alert type="danger">}}
 *Warning:* New breaking changes has been introduced in the `master`. This guide is now outdated. It will be updated soon. Now, your site configuration files should be in `data/sections` directory and should follow [this](https://github.com/hossainemruz/toha-example-site/tree/master/data/sections) format.
{{</ alert >}}

The `About` section should give the viewer a brief idea about yourself. In this post, we are going to configure the `About` section of your website.

At first, create `about.yaml` file in the `data` directory of your site. Then, follow the following instructions.

### Add Your Work Information

Let's add some information about your current job. Add the following section in your `about.yaml` file,

```yaml
# your designation
designation: Software Engineer
# your company information
company:
  name: Example Co.
  url: "https://www.example.com"
```

### Add a Summary About Yourself

Now, let's add a summary of what you do. The purpose of this section is to give the viewer an idea about your professional expertise at a glance. Add the following section in your `about.yaml` file,

```yaml
# a summary about you
summary: 'I am a passionate software engineer with x years of working experience. I built OSS tools for [Kubernetes](https://kubernetes.io/) using GO. My tools help people to deploy their workloads in Kubernetes. Sometimes, I work on some fun projects such as writing a theme, etc.'
```

Try to make it as brief as possible. Don't make it too wordy. We have other sections that give more insight into your expertise.

>You can use markdown syntax in the `summary` field.

### Add Your Social Links

Now, we are going to add some links to your various profiles such as `LinkedIn`, `Twitter`, `Github` etc. Add the following `socialLinks` section in your `about.yaml` file,

```yaml
# your social links
# give as many as you want. use font-awesome for the icons.
socialLinks:
- name: Email
  icon: "fas fa-envelope"
  url: "example@gmail.com"

- name: Github
  icon: "fab fa-github"
  url: "https://www.github.com/example"

- name: Stackoverflow
  icon: "fab fa-stack-overflow"
  url: "#"

- name: LinkedIn
  icon: "fab fa-linkedin"
  url: "#"

- name: Twitter
  icon: "fab fa-twitter"
  url: "#"

- name: Facebook
  icon: "fab fa-facebook"
  url: "#"
```

You can use any [Font Awesome](https://fontawesome.com/icons?d=gallery) free icons in the icon field.

### Add a Resume

Now, let's add your resume. Put the resume pdf file in any folder under `static` directory. Then, add the following section in your `about.yaml` file,

```yaml
# your resume. this file path should be relative to you "static" directory
resume: "files/resume.pdf"
```

### Add Soft Skills Indicator

Now, let's add your strength indicator on various soft skills such as leadership, communication, teamwork, etc. Add the following section in your `about.yaml` file,

```yaml
# your soft skills
# give the percentage between 50 to 100 with 5 intervals.
# currently supported colors: blue, yellow, pink, green
softSkills:
- name: Leadership
  percentage: 85
  color: blue
- name: Team Work
  percentage: 90
  color: yellow
- name: Communication
  percentage: 85
  color: pink
- name: Hard Working
  percentage: 85
  color: green
```

Currently, the skill percentage should be between 50 and 100 and should be divisible by 5. The following colors are available for skills percentage indicator,

- blue
- yellow
- pink
- green

{{< vs 2 >}}

The following image shows how the contents of `about.yaml` are mapped into the `About` section.

{{< img src="/images/posts/configuration/about.png" >}}

### Example `about.yaml` File

Here, is the `about.yaml` file that has been used to create the `About` section of this site.

```yaml
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
- name: Email
  icon: "fas fa-envelope"
  url: "example@gmail.com"

- name: Github
  icon: "fab fa-github"
  url: "https://www.github.com/example"

- name: Stackoverflow
  icon: "fab fa-stack-overflow"
  url: "#"

- name: LinkedIn
  icon: "fab fa-linkedin"
  url: "#"

- name: Twitter
  icon: "fab fa-twitter"
  url: "#"

- name: Facebook
  icon: "fab fa-facebook"
  url: "#"

# your soft skills
# give the percentage between 50 to 100 with 5 intervals.
# currently supported color: blue, yellow, pink, green
softSkills:
- name: Leadership
  percentage: 85
  color: blue
- name: Team Work
  percentage: 90
  color: yellow
- name: Communication
  percentage: 85
  color: pink
- name: Hard Working
  percentage: 85
  color: green
```
