---
title: "Configuración del tipado de Matemáticas"
date: 2020-06-08T06:15:35+06:00
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Guía de Matemáticas
    identifier: writing-post-math-guide
    parent: writing-post
    weight: 40
math: true
---

La notación matemática en un proyecto Hugo se puede habilitar mediante el uso de librerías JavaScript de terceros.
<!--more-->

En este ejemplo usaremos [KaTeX](https://katex.org/)

- Crea un partial debajo de `/layouts/partials/math.html`
- Dentro de esta referencia del partial, se hace referencia a la [Auto-render Extension](https://katex.org/docs/autorender.html) o al host de estos scripts localmente.
- Incluye el partial en tus plantillas de la siguiente forma:

```
{{ if or .Params.math .Site.Params.math }}
{{ partial "math.html" . }}
{{ end }}
```  
- Para habilitar Katex globalmente establece el parámetro `math` a `true` en la configuración del proyecto en el archivo `config.yaml`.
- Para habilitar Katex en publicaciones concretas, incluye el parámetro `math: true` en los archivos de contenido correspondientes.

**Nota:** Usa la referencia online de [Supported TeX Functions](https://katex.org/docs/supported.html)
{{< math.inline >}}
{{ if or .Page.Params.math .Site.Params.math }}
<!-- KaTeX -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
{{ end }}
{{</ math.inline >}}

### Ejemplos
{{< math.inline >}}
<p>
Inline math: \(\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887…\)
</p>
{{</ math.inline >}}

Bloque matemático:
$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } } 
$$
