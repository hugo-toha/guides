---
title: "Configuring Recent Posts Section"
date: 2020-06-08T06:20:34+06:00
menu:
  sidebar:
    name: Recent Posts Section
    identifier: recent-posts-section
    parent: sections
    weight: 150
---

The `Recent Posts` section will display the most recent posts from your content. The configuration is simple, and should be stored in `data/en/sections`.

### Configuration

After you have created the file `recent-posts.yaml`, the configuration is very simple,

```yaml
# section information
section:
  name: Recent Posts # Title of section (default: "")
  id: recent-posts # url id/slug of section *Required*
  enable: true # Boolean to determine if this section is enabled (default: false)
  weight: 6 # Order to display section in (default: alphabetical followed by weight)
  showOnNavbar: true # Boolean to determine if a link should be shown for this section on the navbar
  hideTitle: true # Can optionally hide the title in sections (default: false)
  numShow: 4 # Can optionally increase the number of posts to display (default: 3)
```

{{<img src="images/recent-posts.svg" >}}
