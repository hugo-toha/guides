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

Toha currently supports three analytics methods. First, analytics themselves have to be enabled by setting:

```yaml
  features:
    Analytics:
      enabled: true
```

And, once that parameter has been set, any or all of the different methods can be independently specified as follows:

{{< alert type="warning" >}}
Note: When adding analtics, you should consider local legislation to see if a privacy banner is required to inform users of the tracking in personal data. In general (not legal advice), privacy-friendly, annonymous methods such as counter.dev and goatcounter.com dont need a banner, since they do not collect personally identifiable data.
{{< /alert >}}

### Goat Counter

[GoatCounter](https://www.goatcounter.com/) is the most complete, simple and privacy friendly analytics method provided by Toha. Its script tracks the most viewed pages, total number of users, devices, and much more, all while being open source! You can add the user ID you will receive from their page to your ```config.yaml`` like so:

```yaml
  features:
    Analytics:
      enabled: true

      # Goat Counter
      GoatCounter:
        code: <goat-counter-id>
```

### Counter.Dev

[Counter.dev](https://counter.dev) is a simple, privacy friendly and open source analytics website which enables you to track the total user count, first visited page and some other metrics on your website. Unfortunately, to keep things simple (and free) they dont show a ranking of the most visited pages, but rather the ones that are accessed the first. You can enable it by adding to your ```config.yaml``` the email you registered with at counter.dev's page:

```yaml
  features:
    Analytics:
      enabled: true

      # Counder.Dev
      CounterDev:
        id: <user-email>
```

The tracking code will be automatically added to your site

### Google Analytics

{{< alert type="danger" >}}
Beware that, [according to recent case law](https://www.euractiv.com/section/politics/short_news/use-of-google-analytics-violates-eu-law-austrian-authority-rules/), Google Analytics might be illegal on the European Union
{{< /alert >}}

You can also Google Analytics support by using one of the two following methods:

* Using Hugo's default ```GoogleAnalytics```variable, exposed directly in the configuration. You should add the user ID provided by google (it might start with UA- if it comes from an order version) directly in ```config.yaml```
* Under ```features/Analytics```. Your config file would look like this:

```yaml
  features:
    Analytics:
      enable: true

      # Google Analytics
      Google:
        id: <user-id>
```
