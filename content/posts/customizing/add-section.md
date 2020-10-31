---
title: "How to add a new section"
date: 2020-10-23T00:00:00+00:00
hero: /images/posts/configuration/about-section-hero.svg
menu:
  sidebar:
    name: Adding New Section
    identifier: customizing-add-new-section
    parent: customizing
    weight: 410
---

While the [configuration section](/posts/configuration) goes in detail on configuring each pre-defined section, this post will outline in detail how to add your own fully custom section and include it on the home page.

### Background

The existing "sections" for this theme are configured by the theme consumer via a `.yaml` file in the `./data/<locale>/sections` folders, and that data is then used by the theme's internal templates to provide the each of the stacked horizontal "sections" on the home page:

* About
* Skills
* Experiences
* Projects
* Recent Posts
* Achievements


Each of these existing sections have a set of common data used for displaying the sections in the correct order, providing headers, linking to them, etc. They also then have data structures specific to the template used to render the actual sections contents.

### Configuring a Custom Section

Configuring a custom section is as simple as providing a new `.yaml` file for your custom section in your `./data/<locale>/sections` folder, and writing your own custom template for it. Lets step through an example piece by piece assuming I want to make a new section called `custom`.

#### Required Configs

Firstly, you must create a new `.yaml` configuration file in your `data/<locale>/sections/` folder. In this example, we'll call it custom.yaml

In this file you MUST provide the following keys under the `section` key:

* name: The human readable name of your section used for things like the Nav and Headers
* id: A string used internally as the element ID used for linking and navigating. If no `template` override is provided, the template is assumed to be the id where spaces are replaced with hyphens.
* enable: A boolean (true/false) which enables or disables the section from displaying.
* weight: An integer that dictates the order the sections appear in relative to each other's weight in ascending order.
* showOnNavbar: A boolean (true/false) which enables or disable a nav item this particular section.

You may also provide the following optional keys under the `section` key:
* template: A string representing a specific template name to use instead of the `id`

An example config might be this:

```yml
section:
  name: My Custom Section
  id: custom
  template: custom-template
  enable: true
  weight: 7
  showOnNavbar: true
```

From there, you then just need to define your own template for rendering this section. The file should be defined in your project at the file location `layouts/partials/sections/custom-template.html`. To start, you can add the following:

```html
<div id="{{ .section.id }}">
  Hello New Section
</div>
```

> The div wrapper is important for navigating to the section via the Nav bar

With that, you should see your custom section being displayed on the home page and nav bar!

#### Customizing It

With your `.yaml` config file and `.html` template file, the power is all yours to do whatever you want with it. The full contents of the `.yaml` file are passed in as context to your Hugo template, so you can use that when building out the [template logic](https://gohugo.io/templates/). For example, you can append the following in your config file:

```yml
customData:
- data: value1
- data: value2
- data: value3
```

And then from there, you can use this data in your template as such

```html
<div id="{{ .section.id }}">
  <ul>
    {{ range .customData }}
      <li>
        {{ .data }}
      </li>
    {{ end }}
  </ul>
</div>
```

With that, the world is your oyster. You can add whatever data and markup you want in order to customize and make your site personal.