---
title: "Comments"
date: 2022-03-14T06:00:23+06:00
description: Adding comments in hugo theme Toha
menu:
  sidebar:
    name: Comments
    identifier: comments
    weight: 650
---
## Comments

This theme has built-in support for comment on the posts. Currently, it support the following comment plugins:

- [Disqus](https://disqus.com/)
- [Valine](https://valine.js.org/)
- [Utterances](https://utteranc.es/)
- [Giscus](https://giscus.app/)

### Disqus

Disqus is a popular comment plug-in. After signing up to [Disqus](https://disqus.com/) you will need to provide your shortname under `params.features.comment` section of your `config.yaml` file as below:

```yaml
params:
  features:
    comment:
      enable: true
      disqus:
        shortName: <your-disqus-shortname>
```

### Valine

[Valine](https://valine.js.org/) appears to be a Chinese comments comments plugin. You can enable valine comment plugin by adding `valine` section under `params.features.comments` section as below:

```yaml
params:
  features:
    comment:
      enable: true
      valine:
        appId: app-id
        appKey: app-key
        avatar: avatar
        placeholder: placeholder
        lang: lang
        recordIP: recordIP
        enableQQ: enableQQ
```

### Utterances

Utterances uses [GitHub Issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues) to store the comments for your posts. This requires you to allow have a public repository, and the Utterances app to use your repository. Setup instructions can be found at the [Utterances home page](https://utteranc.es/).

```yaml
params:
  features:
    comment:
      enable: true
      utteranc:
        repo: your-repo/name
        issueTerm: url
        theme: light
```

### Giscus

Giscus is based off Utterances, but uses [GitHub Discussions](https://docs.github.com/en/discussions) as the backend. This requires you to allow have a public repository, and the Giscus app to use your repository. Setup instructions can be found at the [Giscus home page](https://giscus.app/).

To enable Giscus comment plugin, at first go to [giscus.app](https://giscus.app/). On the `Configuration` section, provide the necessary information. It will give you a script to include to your site. You just need to extract the respective information from the script and provide it under `params.features.comment.giscus` section as below:

```yaml
params:
  features:
    comment:
      enable: true
      giscus:
        repo: your-repo/name
        repoID: your-repo-id
        category: your-category
        categoryID: your-category-id
        # theme: light
        # map: url
        # reaction: 1
        # metadata: 0
        # inputPosition: bottom
        # crossOrigin: anonymous
```

The commented out options are optional. You can use them to further customize your comment experience.
