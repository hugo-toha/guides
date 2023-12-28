---
title: "Activer le mode sombre"
date: 2022-06-12T01:30:50+06:00
author:
  name: Nicolas Dietlin
  image: images/author/nicolas.jpg
menu:
  sidebar:
    name: Activer le thème sombre
    identifier: enable-dark-theme
    parent: customizing
    weight: 405
---

## Activation du mode sombre

Toha `v3.6.0` a introduit un thème sombre. Un grand merci à [@donfiguerres](https://github.com/donfiguerres). Ce guide vous montrera comment l'activer.

Tout d'abord, assurez-vous d'avoir mis à jour la version du thème en `v3.6.0` ou plus. Ensuite, ajoutez la section suivante sous la section `params` de votre fichier `config.yaml`.

```yaml
  darkMode:
    enable: true
    provider: darkreader
    default: system
```

Ici,

- **enable:** Spécifie ou non l'activation du mode sombre.
- **provider:** Spécifie le fournisseur sous-jacent qui sera utilisé pour fournir la fonctionnalité du mode sombre. Actuellement, il ne supporte que [darkreader](https://darkreader.org/). Nous pourrions soutenir d'autres fournisseurs dans le futur.
- **default:** Spécifie quel thème utiliser par défaut. Ca supporte les valeurs `system`, `light` et `dark`.
