---
title: "Supports Links"
date: 2022-03-14T06:00:23+06:00
description: Adding support links in hugo theme Toha
menu:
  sidebar:
    name: Support Links
    identifier: supports
    weight: 660
---

This theme supports adding various support/donation links in your site. Currently, supported support links are:

- [Ko-fi](https://ko-fi.com/)

## Ko-fi

You can add your Ko-fi floating button in your website. To add the floating button, add the `support` section under `params.features` section of your sites `config.yaml` file:

```yaml
params:
  features:
    support:
      enabled: true
      kofi:
        user: <your ko-fi user id>
        text: Tip Me
        textColor: '#f9fafc'
        backgroundColor: '#248aaa'
```
