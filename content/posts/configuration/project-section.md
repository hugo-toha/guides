---
title: "Configuring Projects Section"
date: 2020-06-08T06:20:35+06:00
hero: /images/posts/configuration/projects-section-hero.svg
menu:
  sidebar:
    name: Projects Section
    identifier: configuration-projects
    parent: configuration
    weight: 140
---

{{< alert type="danger">}}
 *Warning:* New breaking changes has been introduced in the `master`. This guide is now outdated. It will be updated soon. Now, your site configuration files should be in `data/sections` directory and should follow [this](https://github.com/hossainemruz/toha-example-site/tree/master/data/sections) format.
{{</ alert >}}

The `Projects` section has been designed to showcase your projects in a meaningful way. In this post, we are going to configure the `Projects` section of your site.

At first, create a `projects.yaml` file in the `data` directory of your site. Then, follow the following instructions.

### Add Project Filtering Buttons

Now, add a `buttons` section in your `projects.yaml` file as bellow,

```yaml
buttons:
- name: All
  filter: "all"
- name: Professional
  filter: "professional"
- name: Academic
  filter: "academic"
- name: Hobby
  filter: "hobby"
```

Each button has two properties. The first property is `name` which is the text that will be displayed on the button and the other is `filter` which specifies the category of the projects this button should select.

A button will show only those projects that have a tag that matches the text specified in the `filter` filed. The filter value `all` is treated specially. It matches all the projects even though they don't have `all` as a tag in their `tags` field.

### Add Your Projects

Now, add your projects under the `projects` section of your `projects.yaml` file as bellow,

```yaml
projects:
- name: Kubernetes
  logo: images/projects/kubernetes.png
  role: Contributor
  timeline: "March 2018 - Present"
  repo: https://github.com/kubernetes/kubernetes
  # url: ""
  summary: Production-Grade Container Scheduling and Management .
  tags: ["professional", "kubernetes", "cloud"]
```

You can specify the following field for a project,

- **name**: The name of the project.
- **logo**: The logo of the project. If the project does not have a logo, the theme will automatically add a place holder there.
- **role**: Your role in the project.
- **timeline**: The timeline when you have worked on the project.
- **repo**: If the project is an open-source project and hosted on Github, you can provide the repository URL. This will be used to show the star count for the project.
- **url**: If the project is not an open-source project or not hosted on Github, you can provide an URL of the project. This will create a button with the link in the project card.
- **summary**: A short description of your project.
- **tags**: A list of tags for your project. It will be used to select the project under a category by the filtering buttons.

>You can use markdown syntax in the `summary` field.

{{< vs 2 >}}

The following image shows how the contents of `projects.yaml` are mapped into the `Projects` section.

{{< img src="/images/posts/configuration/projects.png" >}}

### Example `projects.yaml` File

Here, is the `projects.yaml` file that has been used to create the `Projects` section of this site.

```yaml
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
  logo: images/projects/kubernetes.png
  role: Contributor
  timeline: "March 2018 - Present"
  repo: https://github.com/kubernetes/kubernetes # If your project is a public repo on GitHub, then provide this link. it will show star count.
  #url: ""  # If your project is not a public repo but it has a website or any external details url then provide it here. don't provide "repo" and "url" simultaneously.
  summary: Production-Grade Container Scheduling and Management.
  tags: ["professional", "kubernetes", "cloud"]

- name: Tensorflow
  logo: images/projects/tensorflow.png
  role: Developer
  timeline: "Jun 2018 - Present"
  repo: https://github.com/tensorflow/tensorflow
  #url: ""
  summary: An Open Source Machine Learning Framework for Everyone.
  tags: ["professional", "machine-learning","academic"]

- name: A sample academic paper
  role: Team Lead
  timeline: "Jan 2017 - Nov 2017"
  url: "https://www.example.com"
  summary: Lorem ipsum dolor sit amet consectetur adipisicing elit. Sapiente eius reprehenderit animi suscipit autem eligendi esse amet aliquid error eum. Accusantium distinctio soluta aliquid quas placeat modi suscipit eligendi nisi.
  tags: ["academic","iot"]

- name: Nocode
  logo: images/projects/no-code.png
  role: Nothing
  timeline: "Oct 2019 - Dec 2019"
  repo: https://github.com/kelseyhightower/nocode
  #url: ""
  summary: The best way to write secure and reliable applications. Write nothing; deploy nowhere.
  tags: ["hobby", "fun"]

- name: Toha
  logo: images/projects/toha.png
  role: Owner
  timeline: "Jun 2019 - Present"
  repo: https://github.com/hossainemruz/toha
  summary: A Hugo theme for personal portfolio.
  tags: ["hobby","hugo","theme","professional"]
```
