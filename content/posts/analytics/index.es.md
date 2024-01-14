---
title: "Analíticas"
date: 2020-06-08T06:00:23+06:00
description: Añadiendo analíticas del tema de hugo Toha
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Analíticas
    identifier: analytics
    weight: 600
---

## Analíticas

Este tema tiene soporte para varias herramientas de analíticas. Actualmente, soporta las siguientes analíticas:

- [GoatCounter](https://www.goatcounter.com/)
- [counter.dev](https://counter.dev/)
- [Google Analytics](https://analytics.google.com)
- [Matomo](https://matomo.org/)

Para una lista completa de las analíticas soportadas, puede consultar el archivo de ejemplo [config.yaml](https://github.com/hugo-toha/hugo-toha.github.io/blob/main/config.yaml).

{{< alert type="warning" >}}
Advertencia: Al añadir analíticas, debe considerar la legislación local para ver si se requiere un banner de privacidad para informar a los usuarios sobre el seguimiento de los datos personales. En general (no asesoramiento legal), los métodos anónimos y respetuosos de la privacidad, como [counter.dev](https://counter.dev) y [GoatCounter](https://www.goatcounter.com/), no necesitan un banner, ya que no recopilan datos de identificación personal.
{{< /alert >}}

### Goat Counter

[GoatCounter](https://www.goatcounter.com/) son las analíticas que soporta Toha más completas, simples y respetuosas con la privacidad. Su script rastrea las páginas más vistas, el número total de usuarios, dispositivos y mucho más, ¡todo mientras es de código abierto!

Para habilitar las analíticas de GoatCounter en tu sitio, tienes dos opciones: acceder a [goatcounter.com](https://www.goatcounter.com) y obtener un código para tu sitio web, y el segundo es self-hostear una instancia de GoatCounter. Después, tienes que añadir la sección `analytics` debajo de la sección `params.features` de tu archivo `config.yaml`, como a continuación:

```yaml
analytics:
  enable: true
  services:
    # GoatCounter
    goatCounter:
      code: <tu código de GoatCounter>  # Sin self-hostear (Primera opción)
      instance: <your GoatCounter instance url>  ## Para self-hosteat (Segunda opción). Sólo uses un método
```

### counter.dev

[counter.dev](https://counter.dev) es un sitio web de análisis de código abierto, sencillo y respetuoso con la privacidad que le permite realizar un seguimiento del recuento total de usuarios, la primera página visitada y algunas otras métricas de su sitio web. Desafortunadamente, para simplificar las cosas (y gratis), no muestran una clasificación de las páginas más visitadas, sino de aquellas a las que se accede primero.

Puedes habilitarlo añadiendo el email que te has registrado a la página de counter.dev debajo de la sección `params.features` de tu archivo `config.yaml`, como a continuación:

```yaml
analytics:
  enable: true
  services:
    counterDev:
      id: <su id de counter.dev>
```

El código de seguimiento automáticamente será añadido a tu sitio web.

Nota: En algunos sitios, aparece [an error has been detected](https://github.com/ihucos/counter.dev/issues/37), donde solo el directorio raíz ("/") se pasa a counter.dev, por lo que el seguimiento no mostrará nada en la sección "pages". Para solucionar este problema, se puede añadir `referrerPolicy: no-referrer-when-downgrade` como parámetro en la sección "counterDev", asegurando que las nuevas visitas a la página siempre se pasen correctamente a counter.dev.

### Google Analytics

{{< alert type="danger" >}}
Tenga en cuenta que, según la [jurisprudencia reciente](https://www.euractiv.com/section/politics/short_news/use-of-google-analytics-violates-eu-law-austrian-authority-rules/), Google Analytics podría ser ilegal en la Unión Europea
{{< /alert >}}

Puedes habilitar Google Analytics en tu sitio añadiendo tu id de rastreo debajo de la sección `params.features` de tu archivo `config.yaml`, como a continuación:

```yaml
analytics:
  enable: true
  services:
    # Google Analytics
    google:
      id: <tu id de rastreo de Google Analytics>
```

Puede utilizar el ID de seguimiento tanto V3 como V4. El tema detectará automáticamente la versión de seguimiento, y añadirá los scripts respectivos de acuerdo a tu sitio web.

Para configuraciones de privacidad adicionales de Google Analytics, puedes proveer la sección `privacy.googleAnalytics` dentro del archivo `config.yaml` descrito [aquí](https://gohugo.io/about/hugo-and-gdpr/#all-privacy-settings).

### Matomo

Puedes habilitar Matomo (antes Piwik) en tu sitio añadiendo tu configuración de matomo debajo de la sección `params.features` de tu archivo `config.yaml`, como a continuación:

```yaml
analytics:
  enable: true
  services:
    # Matomo / Piwik
    matomo:
      instance: matomo.example.com
      siteId: 1 # Número generado después de agregar tu sitio a tu instancia
```
