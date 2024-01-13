---
title: "Enable Dark Theme"
date: 2022-06-12T01:30:50+06:00
author:
  name: Emruz Hossain
  image: images/author/emruz.jpg
menu:
  sidebar:
    name: Enable Dark Theme
    identifier: enable-dark-theme
    parent: customizing
    weight: 405
---

To enable the dark mode in Toha `v4.0.0`, simply set the `darkMode.enable` field to `true` under the `params.features` section in your `config.yaml` file. For example:

```yaml
params:
  features:
    darkMode:
      enable: true
```

Congratulations! You are all set. You can now enjoy the dark mode in your site. The dark mode will obey user's system preference.
