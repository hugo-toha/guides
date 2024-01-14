---
title: "Habilitar Tema Oscuro"
date: 2022-06-12T01:30:50+06:00
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Habilitar Tema Oscuro
    identifier: enable-dark-theme
    parent: customizing
    weight: 405
---

Para habilitar el modo oscuro en Toha `v4.0.0`, simplemente establece el campo `darkMode.enable` a `true` debajo de la sección `params.features` dentro del archivo `config.yaml`. Por ejemplo:

```yaml
params:
  features:
    darkMode:
      enable: true
```

¡Felicidades! Estas listo. Ahora puedes disfrutar del modo oscuro en tu sitio. El modo oscuro obedecerá a las preferencias del sistema del usuario.

