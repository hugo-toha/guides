---
title: "Configuring Skills Section"
date: 2020-06-08T06:20:45+06:00
hero: /images/posts/configuration/skills-section-hero.svg
menu:
  sidebar:
    name: Skills Section
    identifier: configuration-skills
    parent: configuration
    weight: 120
---

{{< alert type="danger">}}
 *Warning:* New breaking changes has been introduced in the `master`. This guide is now outdated. It will be updated soon. Now, your site configuration files should be in `data/sections` directory and should follow [this](https://github.com/hossainemruz/toha-example-site/tree/master/data/sections) format.
{{</ alert >}}

The `Skills` section should give the viewer an idea about not only the list of skills you have but also an idea of the depth of your knowledge on a particular skill. In this post, we are going to configure the `Skills` section of your site.

At first, create `skills.yaml` files in the `data` directory of your site. Then, follow the following instruction.

### Add Your Skills

Now, let's add a `skills` section in your `skills.yaml` file as bellow,

```yaml
skills:
- name: Kubernetes
  icon: "images/skills/kubernetes.png"
  summary: "Capable of deploying, managing application on Kubernetes. Experienced in writing Kubernetes controllers for CRDs."
```

Here, you have to provide `name`, `icon`, and `summary` fields for a skill. The `summary` field should provide an idea about your depth of knowledge of this particular skill.

>You can use markdown syntax in the `summary` field.

{{< vs 2 >}}

The following image shows how the content of `skills.yaml` files are mapped into the `Skills` section.

{{< img src="/images/posts/configuration/skills.png">}}

### Example `skills.yaml` File

Here, is the `skills.yaml` file that has been used to create the `Skills` section of this site.

```yaml
# Your Skills.
# Give a summary of you each skill in the summary section.
skills:
- name: Kubernetes
  icon: "images/skills/kubernetes.png"
  summary: "Capable of deploying, managing application on Kubernetes. Experienced in writing Kubernetes controllers for CRDs."

- name: Go Development
  icon: "images/skills/go.png"
  summary: "Using as the main language for professional development. Capable of writing scalable, testable, and maintainable program."

- name: Cloud Computing
  icon: "images/skills/cloud.png"
  summary: "Worked with most of the major clouds such as GCP, AWS, Azure etc."

- name: Docker
  icon: "images/skills/docker.svg"
  summary: "Write most of the programs as dockerized container. Experienced with multi-stage, multi-arch build process."

- name: Prometheus
  icon: "images/skills/prometheus.png"
  summary: "Capable of setup, configure Prometheus metrics. Experienced with PromQL, AlertManager. Also, experienced with writing metric exporters."

- name: Linux
  icon: "images/skills/linux.png"
  summary: "Using as the main operating system. Capable of writing bash/shell scripts."

- name: Git
  icon: "images/skills/git.png"
  summary: "Experienced with git-based development. Mostly, use Github. Also, have experience in working with GitLab."

- name: C++
  icon: "images/skills/c++.png"
  summary: "Know basic C/C++ programming. Used for contest programming and problem solving."
```
