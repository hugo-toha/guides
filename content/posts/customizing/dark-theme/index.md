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

## Enable Dark Mode

Toha `v3.6.0` has introduced dark theme. Thanks to [@donfiguerres](https://github.com/donfiguerres). This guide will show you how to enable it.

At first, make sure you have updated the theme version to `v3.6.0` or later. Then, add the following section under `params` section of your `config.yaml` file.

```yaml
  darkMode:
    enable: true
    provider: darkreader
    default: system
```

Here,

- **enable:** Specifies whether to enable the dark mode or not.
- **provider:** Specifies the underlying provider that will be used to provide the dark mode functionality. Currently, it supports only [darkreader](https://darkreader.org/). We may support other providers in future.
- **default:** Specifies which theme to use by default. It supports `system`, `light` and `dark` values.
