---

title: "Les Shortcodes"
date: 2023-11-05T14:06:25+02:00
description: "Codes abrégés"
menu:
  sidebar:
    name: "Les Shortcodes"
    identifier: shortcodes
    weight: 700
hero: boat.jpg
---

Ce billet d'échantillon est destiné à tester les éléments suivants :

- Manipulation d'une image.
- Différents shortcodes.

## Alerte

Ce thème propose différents types d'alertes pour votre publication. Par exemple, si on ajoute le code ci-dessous :

```markdown
{{</* alert type="success" */>}}
This is sample alert with `type="success"`.
{{</* /alert */>}}
```

L'alerte qui apparaîtra ressemblera à ça:

{{< alert type="success" >}}
This is sample alert with `type="success"`.
{{< /alert >}}

Les alertes suivantes sont également disponible dans ce thème.
```markdown
{{</* alert type="danger" */>}}
This is sample alert with `type="danger"`.
{{</* /alert */>}}
```

{{< alert type="danger" >}}
This is sample alert with `type="danger"`.
{{< /alert >}}

```markdown
{{</* alert type="warning" */>}}
This is sample alert with `type="warning"`.
{{</* /alert */>}}
```

{{< alert type="warning" >}}
This is sample alert with `type="warning"`.
{{< /alert >}}

```markdown
{{< alert type="info" */>}}
This is sample alert with `type="info"`.
{{</* /alert */>}}
```
{{< alert type="info" >}}
This is sample alert with `type="info"`.
{{< /alert >}}

```markdown
{{< alert type="dark" */>}}
This is sample alert with `type="dark"`.
{{</* /alert >}}
```

{{< alert type="dark" >}}
This is sample alert with `type="dark"`.
{{</* /alert */>}}

```markdown
{{</* alert type="primary" */>}}
This is sample alert with `type="primary"`.
{{</* /alert */>}}
```

{{< alert type="primary" >}}
This is sample alert with `type="primary"`.
{{< /alert >}}

```markdown
{{</* alert type="secondary" */>}}
This is sample alert with `type="secondary"`.
{{</* /alert */>}}
```

{{< alert type="secondary" >}}
This is sample alert with `type="secondary"`.
{{< /alert >}}

## Image

#### Une image sans attributs.

**Code:**

```markdown
{{</* img src="/posts/shortcodes/boat.jpg" title="A boat at the sea" */>}}
```

**Résultat:**

{{< img src="/posts/shortcodes/boat.jpg" title="A boat at the sea" >}}

{{< vs 3 >}}

#### Une image avec les attributs `height` et `width`.

**Code:**

```markdown
{{</* img src="/posts/shortcodes/boat.jpg" height="400" width="600" title="A boat at the sea" */>}}
```

**Résultat:**

{{< img src="/posts/shortcodes/boat.jpg" height="400" width="600" title="A boat at the sea" >}}

{{< vs 3 >}}

#### Une image centrée avec les attributs `height` et `width`.


**Code:**

```markdown
{{</* img src="/posts/shortcodes/boat.jpg" height="400" width="600" align="center" title="A boat at the sea" */>}}
```

**Résultat:**

{{< img src="/posts/shortcodes/boat.jpg" height="400" width="600" align="center" title="A boat at the sea" >}}

{{< vs 3 >}}

#### Une image avec l'attribut `float`.

**Code:**

```markdown
{{</* img src="/posts/shortcodes/boat.jpg" height="200" width="500" float="right" title="A boat at the sea" */>}}
```

**Résultat:**

{{< img src="/posts/shortcodes/boat.jpg" height="200" width="500" float="right" title="A boat at the sea" >}}

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies. Praesent tellus risus, eleifend vel efficitur ac, venenatis sit amet sem. Ut ut egestas erat. Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat. Suspendisse nec ipsum eu erat finibus dictum. Morbi volutpat nulla purus, vel maximus ex molestie id. Nullam posuere est urna, at fringilla eros venenatis quis.

Fusce vulputate dolor augue, ut porta sapien fringilla nec. Vivamus commodo erat felis, a sodales lectus finibus nec. In a pulvinar orci. Maecenas suscipit eget lorem non pretium. Nulla aliquam a augue nec blandit. Curabitur ac urna iaculis, ornare ligula nec, placerat nulla. Maecenas aliquam nisi vitae tempus vulputate.

## Diviser

Ce thème supporte le découpage de la page en autant de colonnes que vous le souhaitez.

#### Diviser en 2 colonnes

**Code:**

```markdown
{{</* split 6 6 */>}}
##### Colonne de gauche

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### Colonne de droite

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{</* /split */>}}
```

**Result:**

{{< split 6 6>}}

##### Colonne de gauche

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### Colonne de droite

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{< /split >}}

#### Diviser en 3 colonnes

**Code:**

```markdown
{{</* split 4 4 4 */>}}
##### Colonne de gauche

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### Colonne du milieu

Aenean dignissim dictum ex. Donec a nunc vel nibh placerat interdum.

---

##### Colonne de droite

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{</* /split */>}}
```

**Result:**

{{< split 4 4 4 >}}

##### Colonne de gauche

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### Colonne du milieu

Aenean dignissim dictum ex. Donec a nunc vel nibh placerat interdum.

---

##### Colonne de droite

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{< /split >}}

## Espace vertical

Donner un espace vertical entre deux lignes.

**Code:**

```markdown
Voici la ligne 1.
{{< vs 4>}}
Voici la ligne 2. Il devrait y avoir un espace vertical de `4rem` avec la ligne précédente.
```

**Résultat:**

Voici la ligne 1.
{{< vs 4>}}
Voici la ligne 2. Il devrait y avoir un espace vertical de `4rem` avec la ligne précédente.

## Vidéo

**Code:**

```markdown
{{</* video src="/videos/sample.mp4" */>}}
```

**Résultat:**

{{< video src="/videos/sample.mp4" >}}

<!-- markdown-link-check-disable-next-line -->
Vidéo de [Rahul Sharma](https://www.pexels.com/@rahul-sharma-493988) sur [Pexels](https://www.pexels.com).
