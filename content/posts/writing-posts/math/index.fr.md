---
title: "Paramètres de type Maths"
date: 2020-06-08T06:15:35+06:00
menu:
  sidebar:
    name: Paramètre de type Maths
    identifier: writing-post-math-guide
    parent: writing-post
    weight: 40
math: true
---

La notation Mathématique dans un projet Hugo peut être activée en utilisant des librairies JavaScript tierces.
<!--more-->

Dans cet exemple, nous utiliserons [KaTeX](https://katex.org/)

- Créez un partiel sous `/layouts/partials/math.html`
- A l'intérieur de ce partiel référencez l'[Auto-render Extension](https://katex.org/docs/autorender.html) ou hébergez ces scripts localement.
- Inclure le partiel dans votre template comme suit:  

```bash
{{ if or .Params.math .Site.Params.math }}
{{ partial "math.html" . }}
{{ end }}
```

- Pour activer KaText globalement mettez le paramètre `math` à `true` dans la configuration du projet.
- Pour activer KaTex par page, incluez le paramètre `math: true` dans le front matter de votre fichier de contenu.

**Note:** Utilisez le référentiel en ligne des [Fonctions TeX supportées](https://katex.org/docs/supported.html)

{{< math.inline >}}
{{ if or .Page.Params.math .Site.Params.math }}
<!-- KaTeX -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
{{ end }}
{{</ math.inline >}}

### Exemples

{{< math.inline >}}
<p>
Inline math: \(\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887…\)
</p>
{{</ math.inline >}}

Bloc de math:
$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } } 
$$
