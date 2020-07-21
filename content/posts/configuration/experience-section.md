---
title: "Configuring Experiences Section"
date: 2020-06-08T06:20:40+06:00
hero: /images/posts/configuration/experiences-section-hero.svg
menu:
  sidebar:
    name: Experiences Section
    identifier: configuration-experiences
    parent: configuration
    weight: 130
---

{{< alert type="danger">}}
 *Warning:* New breaking changes has been introduced in the `master`. This guide is now outdated. It will be updated soon. Now, your site configuration files should be in `data/sections` directory and should follow [this](https://github.com/hossainemruz/toha-example-site/tree/master/data/sections) format.
{{</ alert >}}

The `Experiences` section has been designed to truly reflect your career background. It should give the viewer an idea about the responsibilities you have handled in various stages of your career. In this post, we are going to configure the `Experiences` section of your site.

At first, create an `experiences.yaml` file in the `data` directory of your site. Then, follow the following instruction.

### Add Your Experiences

Now, let's add an `experiences` section in the `experiences.yaml` file as below,

```yaml
# Your experiences
experiences:
- designation: Software Engineer
  company:
    name: Example Co.
    url: "https://www.example.com"
    location: Dhaka Branch
    # company overview
    overview: Example Co. is a widely recognized company for cloud-native development. It builds tools for Kubernetes.
  start: Nov 2017
  # don't provide end date if you are currently working there. It will be replaced by "Present"
  end: Dec 2020
  # give some points about what was your responsibilities at the company.
  responsibilities:
  - Design, develop and manage disaster a recovery tool [Xtool](https://www.example.com) that backup Kubernetes volumes, databases, and cluster's resource definition.
  - My another responsibility.
  - My more responsibilities.
```

Each entry in the `experiences` section should have the following information,

- **designation**: Represents your position at the company.
- **company**: Some information about your company. You should provide `name`, `url`, `location`, and a brief `overview` of the company.
- **start**: Time when you had joined the company.
- **end**: Time when you have left the company. If you are currently working in the company, don't provide this field.
- **responsibilities**: A list of responsibilities you handled in the company. This section is very important as it will give the viewer an idea about the professional responsibilities you are capable to deal with.

> You can use markdown syntax in `overview` field of `company` section and `responsibilities` field.

{{< vs 2 >}}

The following image shows how the contents of `experiences.yaml` are mapped into the `Experiences` section.

{{< img src="/images/posts/configuration/experiences.png" >}}

### Example `experiences.yaml` File

Here, is the `experiences.yaml` file that has been used to create the `Experiences` section of this site.

```yaml
# Your experiences
experiences:
- designation: Software Engineer
  company:
    name: Example Co.
    url: "https://www.example.com"
    location: Dhaka Branch
    # company overview
    overview: Example Co. is a widely recognized company for cloud-native development. It builds tools for Kubernetes.
  start: Nov 2017
  # don't provide end date if you are currently working there. It will be replaced by "Present"
  # end: Dec 2020
  # give some points about what was your responsibilities at the company.
  responsibilities:
  - Design, develop and manage disaster recovery tool [Xtool](https://www.example.com) that backup Kubernetes volumes, databases, and cluster's resource definition.
  - My another responsibility.
  - My more responsibilities.

- designation: Software Engineer
  company:
    name: PreExample Co.
    url: "https://www.preexample.com"
    location: Nowhere
    overview: PreExample Co. is a gateway company to enter into Example co. So, nothing special here.
  start: March 2016
  end: May 2017
  responsibilities:
  - Write lots of example codes.
  - Read lots of examples.
  - See lots of example videos.

- designation: Intern
  company:
    name: Intern Counting Company (ICC).
    url: "https://www.intern.com"
    location: Intern Land
    overview: Intern counting Company (ICC) is responsible for counting worldwide intern Engineers.
  start: Jun 2015
  end: Jan 2016
  responsibilities:
  - Count lost of interns.
  - Count more interns.
  - Count me as an intern.
```
