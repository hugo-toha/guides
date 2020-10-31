---
title: "How to add a custom page"
date: 2020-06-08T00:00:00+00:00
hero: /images/posts/configuration/about-section-hero.svg
menu:
  sidebar:
    name: Adding New Page
    identifier: customizing-add-new-page
    parent: customizing
    weight: 410
---

This guide will show you how to create a fully standalone page separate from the Home page or the Posts that can then be linked to in your navigation or with other links. We will create an About Us page as an example.

### Create the Branch Bundle

The first step is to create a [branch bundle](https://gohugo.io/content-management/page-bundles/#branch-bundles) under the content folder for your new page. Basically, this just tells Hugo to create a page and route for this new content. For our about page we'll make the following file at `content/about/_index.md`

```yaml
---
title: "About"
date: 2020-07-04T01:49:53+06:00
---

Hello from about page.

```

### Create the Page UI

Next we'll want to create the actual UI for the page. To do so, we'll create `layouts/section/about.html` with the following contents.

```html
{{ define "header" }}
    <!-- Put your custom css file link here -->
    <link rel="stylesheet" href="/css/about.css" />
{{ end }}

{{ define "navbar" }}
    <!-- Add navbar to your about page -->
    {{ partial "navigators/navbar-2.html" (dict "baseURL" .Site.BaseURL "title" .Site.Title "hasToggleButton" false "navBrandURL"  .Site.BaseURL ) }}
{{ end }}

{{ define "content" }}
    <!-- Put your about page content here -->
    <div class="container about-content">
        <h1>This is  about page header</h1>
        {{ .Content }}
    </div>
{{ end }}
```

And for styling create a file `static/css/about.css` like this

```css
.about-content{
    width: 100%;
    height: 50vh;
    background-color: lightgrey;
    padding: 1rem;
    padding-top: 5rem;
}
```

> The CSS file is not required, if you don't need it, remove the link from your html file.

### Link to it

At this point, your custom page exists and is routeable via `/about` (based on the Branch Bundle folder path). You may link to it from any of your content, but a common use case would be to link to it from the navigation. You can supply custom menu items [here](http://localhost:1313/posts/configuration/site-parameters/#add-custom-menus). In our case we would update our `site.yaml` to include

```yaml
customMenus:
- name: About
  url: /about
```

And with that, you have a fully separate customizable page. Using the above gives you a bare bones example page to begin building on top of

<br />

{{< figure src="/images/posts/customizing/add-page/about-page.png" >}}