---
title: "Configuring About Section"
date: 2020-06-08T06:20:50+06:00
menu:
  sidebar:
    name: About Section
    identifier: about-section
    parent: sections
    weight: 110
---

The `About` section should give the viewer a brief idea about yourself. In this post, we are going to configure the `About` section of your website.

At first, create `about.yaml` file in the `data/en/sections` directory of your site. Then, follow the following instructions.

### Add Section information
```yaml
section:
  name: About # Title of section (default: "")
  id: about # url id/slug of section *Required*
  enable: true # Boolean to determine if this section is enabled (default: false)
  weight: 1 # Order to display section in (default: alphabetical followed by weight)
  showOnNavbar: true # Boolean to determine if a link should be shown for this section on the navbar
  template: sections/about.html # allows you to point to a specific template.
```

#### Template setting
It is possible to overwrite which partial this section is grabbed from using the template property. The new template should be saved in your `layout/partials` directory.

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

### Add badges

Now, let's add your badges and strength indicator on various soft skills such as leadership, communication, teamwork, etc. Add the following section in your `about.yaml` file,

```yaml
# Show your badges
# You can show your verifiable certificates from https://www.credly.com.
# You can also show a circular bar indicating the level of expertise on a certain skill
badges:
- type: certification
  name: Certified Kubernetes Security Specialist
  url: "https://www.credly.com/org/the-linux-foundation/badge/exam-developer-certified-kubernetes-security-specialist"
  badge: "https://images.credly.com/size/680x680/images/f4bf92ed-8985-40b2-bc07-2f9308780854/kubernetes-security-specialist-logo-examdev.png"

- type: certification
  name: Istio and IBM Cloud Kubernetes Service
  url: "https://www.credly.com/org/the-linux-foundation/badge/exam-developer-certified-kubernetes-security-specialist"
  badge: "https://images.credly.com/size/680x680/images/8d34d489-84bf-4861-a4a0-9e9d68318c5c/Beyond_basics_of_Istio_on_Cloud_v2.png"

- type: certification
  name: Artificial Intelligence and Machine Learning
  url: "https://www.credly.com/org/grupo-bancolombia/badge/artificial-intelligence-and-machine-learning"
  badge: "https://images.credly.com/size/680x680/images/e027514f-9d07-4b29-862f-fe21a8aaebf1/ae.png"

- type: soft-skill-indicator
  name: Leadership
  percentage: 85
  color: blue

- type: soft-skill-indicator
  name: Team Work
  percentage: 90
  color: yellow

- type: soft-skill-indicator
  name: Hard Working
  percentage: 85
  color: orange
```

Currently, the skill percentage should be between 50 and 100 and should be divisible by 5. The following colors are available for skills percentage indicator,

- blue
- yellow
- pink
- green

{{< vs 2 >}}

The following image shows how the contents of `about.yaml` are mapped into the `About` section. (The configuration portion of the image is outdated and softSkills section has been replaced with badges)

{{< img src="images/about.png" >}}

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

# Show your badges
# You can show your verifiable certificates from https://www.credly.com.
# You can also show a circular bar indicating the level of expertise on a certain skill
badges:
- type: certification
  name: Certified Kubernetes Security Specialist
  url: "https://www.credly.com/org/the-linux-foundation/badge/exam-developer-certified-kubernetes-security-specialist"
  badge: "https://images.credly.com/size/680x680/images/f4bf92ed-8985-40b2-bc07-2f9308780854/kubernetes-security-specialist-logo-examdev.png"

- type: certification
  name: Istio and IBM Cloud Kubernetes Service
  url: "https://www.credly.com/org/the-linux-foundation/badge/exam-developer-certified-kubernetes-security-specialist"
  badge: "https://images.credly.com/size/680x680/images/8d34d489-84bf-4861-a4a0-9e9d68318c5c/Beyond_basics_of_Istio_on_Cloud_v2.png"

- type: certification
  name: Artificial Intelligence and Machine Learning
  url: "https://www.credly.com/org/grupo-bancolombia/badge/artificial-intelligence-and-machine-learning"
  badge: "https://images.credly.com/size/680x680/images/e027514f-9d07-4b29-862f-fe21a8aaebf1/ae.png"

- type: soft-skill-indicator
  name: Leadership
  percentage: 85
  color: blue

- type: soft-skill-indicator
  name: Team Work
  percentage: 90
  color: yellow

- type: soft-skill-indicator
  name: Hard Working
  percentage: 85
  color: orange
```
