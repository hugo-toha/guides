---
title: "Analytics"
date: 2020-06-08T06:00:23+06:00
description: Adding analytics in hugo theme Toha
menu:
  sidebar:
    name: Analytics
    identifier: analytics
    weight: 600
---

## Analytics

This theme has built in support for various analytic tools. Currently, it supports the following analytics:

- [GoatCounter](https://www.goatcounter.com/)
- [counter.dev](https://counter.dev/)
- [Google Analytics](https://analytics.google.com)

{{< alert type="warning" >}}
Warning: When adding analytics, you should consider local legislation to see if a privacy banner is required to inform users of the tracking in personal data. In general (not legal advice), privacy-friendly, anonymous methods such as [counter.dev](https://counter.dev) and [GoatCounter](https://www.goatcounter.com/) don't need a banner, since they do not collect personally identifiable data.
{{< /alert >}}

### Goat Counter

[GoatCounter](https://www.goatcounter.com/) is the most complete, simple and privacy friendly analytics method supported in Toha. Its script tracks the most viewed pages, total number of users, devices, and much more, all while being open source!

To enable GoatCounter analytics in your site, you have to sign in at [goatcounter.com](https://www.goatcounter.com) and obtain a code for your site. Then, you have to add `analytics` section under `params.features` section of your `config.yaml` file as below:

```yaml
params:
  features:
    analytics:
      enabled: true
      goatCounter:
        code: <your goat counter code>
```

### counter.dev

[counter.dev](https://counter.dev) is a simple, privacy friendly and open source analytics website which enables you to track the total user count, first visited page and some other metrics on your website. Unfortunately, to keep things simple (and free) they don't show a ranking of the most visited pages, but rather the ones that are accessed the first.

You can enable it by adding the email you registered with at counter.dev's page in your `config.yaml` as below:

```yaml
params:
  features:
    analytics:
      enabled: true
      counterDev:
        id: <your counter.dev id>
```

The tracking code will be automatically added to your site.

Note: On some sites, [an error has been detected](https://github.com/ihucos/counter.dev/issues/37) where only the root directory ("/") is passed over to counter.dev, so the tracking wont show anything under the "pages" section. To fix this, one can add `referrerPolicy: no-referrer-when-downgrade` as a parameter on the "counterDev" section, ensuring that new page visits are always correctly passed onto counter.dev.

### Google Analytics

{{< alert type="danger" >}}
Beware that [according to recent case law](https://www.euractiv.com/section/politics/short_news/use-of-google-analytics-violates-eu-law-austrian-authority-rules/), Google Analytics might be illegal in the European Union
{{< /alert >}}

You can enable Google Analytics in your site by adding your tracking id in your `config.yaml` file as below:

```yaml
params:
  features:
    analytics:
      enabled: true
      google:
        id: UA-122321624-2
```

You can use both V3 or V4 tracking ID. The theme will automatically detect the tracking code version and add the respective tracking scripts accordingly to your site.

For additional privacy settings regarding Google Analytics, you can provide `privacy.googleAnalytics` section in your `config.yaml` file as described [here](https://gohugo.io/about/hugo-and-gdpr/#all-privacy-settings).
