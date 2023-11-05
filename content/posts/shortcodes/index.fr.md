---
title: "Codes abrégés"
date: 2023-11-05T14:06:25+02:00
description: "Codes abrégés"
menu:
  sidebar:
    name: "Code abrégés"
    identifier: shortcodes
    weight: 700
hero: boat.jpg
---
Ce billet échantillon est destiné à tester les éléments suivants :

- Image de héros par défaut.
- Différents shortcodes.

## Alerte

Les alertes suivantes sont disponibles dans ce thème.

{{< alert type="success" >}}
Voici une alerte avec `type="success"`.
{{< /alert >}}

{{< alert type="danger" >}}
Voici une alerte avec `type="danger"`.
{{< /alert >}}

{{< alert type="warning" >}}
Voici une alerte avec `type="warning"`.
{{< /alert >}}

{{< alert type="info" >}}
Voici une alerte avec `type="info"`.
{{< /alert >}}

{{< alert type="dark" >}}
Voici une alerte avec `type="dark"`.
{{< /alert >}}

{{< alert type="primary" >}}
Voici une alerte avec `type="primary"`.
{{< /alert >}}

{{< alert type="secondary" >}}
Voici une alerte avec `type="secondary"`.
{{< /alert >}}

## Image

#### Une image sans attributs.

{{< img src="/posts/shortcodes/boat.jpg" title="A boat at the sea" >}}

{{< vs 3 >}}

#### Une image avec les attributs `height` et `width`.

{{< img src="/posts/shortcodes/boat.jpg" height="400" width="600" title="A boat at the sea" >}}

{{< vs 3 >}}

#### Une image centrée avec les attributs `height` et `width`.

{{< img src="/posts/shortcodes/boat.jpg" height="400" width="600" align="center" title="A boat at the sea" >}}

{{< vs 3 >}}

#### Une image avec l'attribut `float`.

{{< img src="/posts/shortcodes/boat.jpg" height="200" width="500" float="right" title="A boat at the sea" >}}

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies. Praesent tellus risus, eleifend vel efficitur ac, venenatis sit amet sem. Ut ut egestas erat. Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat. Suspendisse nec ipsum eu erat finibus dictum. Morbi volutpat nulla purus, vel maximus ex molestie id. Nullam posuere est urna, at fringilla eros venenatis quis.

Fusce vulputate dolor augue, ut porta sapien fringilla nec. Vivamus commodo erat felis, a sodales lectus finibus nec. In a pulvinar orci. Maecenas suscipit eget lorem non pretium. Nulla aliquam a augue nec blandit. Curabitur ac urna iaculis, ornare ligula nec, placerat nulla. Maecenas aliquam nisi vitae tempus vulputate.

## Diviser

Ce thème supporte le découpage de la page en autant de colonnes que vous le souhaitez.

#### Diviser en 2 colonnes

{{< split 6 6>}}

##### Colonne de Gauche

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### Colonne de Droite

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{< /split >}}

#### Diviser en 3 colonnes

{{< split 4 4 4 >}}

##### Colonne de Gauche

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### Colonne du Milieu

Aenean dignissim dictum ex. Donec a nunc vel nibh placerat interdum.

---

##### Colonne de Droite

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{< /split >}}

## Espace vertical

Donner un espace vertical entre deux lignes.

Voici la ligne 1.
{{< vs 4>}}
Voici la ligne 2. Il devrait y avoir un espace vertical de `4rem` avec la ligne précédente.

## Vidéo

{{< video src="/videos/sample.mp4" >}}

<!-- markdown-link-check-disable-next-line -->
Vidéo de [Rahul Sharma](https://www.pexels.com/@rahul-sharma-493988) sur [Pexels](https://www.pexels.com).

