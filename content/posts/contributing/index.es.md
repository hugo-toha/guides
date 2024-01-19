---
title: "Cómo contribuir?"
date: 2024-01-19T02:30:00+06:00
description: Una guía de cómo contribuir al tema de toha
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Contribuyendo
    identifier: Contribuyendo
    weight: 900
---

## Maneras de contribuir

Puedes contribuir a este tema de varias maneras.

### Código

Los Pull Requests son bienvenidos y estaré encantado de revisarlos. Simplemente siga los siguientes principios:

- Manténgalo simple.
- Manténgalo consistente con el diseño.
- Utilice la menor cantidad de dependencias posible.
- Ten paciencia.

### Testeando y reportando errores

- Puedes reportar un [bug](https://github.com/hugo-toha/toha/issues/new?template=bug.md)
- También puedes [pedir una característica](https://github.com/hugo-toha/toha/issues/new?template=feature_request.md)
- [Dar ideas y sugerencias](https://github.com/hugo-toha/toha/issues/new?template=question.md)

### Documentación

También puedes contribuir con la documentación del tema:
You can also contribute to the theme documentation by:
- Añadiendo información y secciones.
- Corrigiendo errores y faltas de ortografía.
- Actualizando documentación obsoleta.
- Traduciendo la documentación a un nuevo idioma, [esta](/es/posts/translation/content/) guía te podría ser útil.

### Traducción

Finalmente, puedes contribuir a la traducción del tema a distintos idiomas, completando palabras que faltan, o añadiendo un nuevo idioma. Puedes seguir la guía [Cómo añadir un idioma sin soporte](/es/posts/translation/new-language/) para más información.

## Cómo contribuir?

Para el desarrollo local, puedes hacer cambios al submódulo del tema y probar los cambios con tu propio sitio o con el [sitio de ejemplo](https://github.com/hugo-toha/hugo-toha.github.io) localmente.

### Fork

Para comenzar, haz fork de [este repositorio](https://github.com/hugo-toha/toha). Después, sigue los siguientes pasos para usar el tema forkeado para el desarrollo local,

#### Usando el tema forkeado en tu propio sitio:

Si quiéres ejecutar el desarrollo local con tu propio sitio, sigue los siguientes pasos:

```bash
# añade el tema original como submódulo de tu sitio si aún no lo has hecho
$ git submodule add https://github.com/hugo-toha/toha.git themes/toha
# navega hacia el directorio del tema de toha
$ cd themes/toha
# añade un fork a github
$ git remote add my-fork https://github.com/<tu-usuario-de-github>/toha
# crea una nueva rama para tus cambios
$ git checkout -b mi-nueva-rama
```

#### Usando el tema forkeado en el sitio de ejemplo

Si quiéres ejecutar el desarrollo local con este [sitio de ejemplo](https://github.com/hugo-toha/hugo-toha.github.io), sigue los siguientes pasos:

```bash
# clona el sitio de ejemplo junto con los submódulos
$ git clone git@github.com:hugo-toha/hugo-toha.github.io.git --recursive
# navega hacia el directorio del tema de toha
$ cd themes/toha
# añade un fork a github
$ git remote add my-fork https://github.com/<tu-usuario-de-github>/toha
# crea una nueva rama para tus cambios
$ git checkout -b mi-nueva-rama
```

Desde aquí ya puedes hacer cambios al código fuente del tema mientras lo pruebas con to sitio Hugo o con el de ejemplo.

### Abre un Pull Request

Cuando ya hayas hecho los cambios, haz commit y haz push a tu fork.

```bash
# añade todos los cambios
$ git add .
# haz commit de los cambios con un mensaje significativo
$ git commit -m "Un mensaje de commit significativo"
# haz push del commit a tu fork
$ git push my-fork mi-nueva-rama
```

Después, abre un Pull Request en la rama `main` de [hugo-toha/toha](https://github.com/hugo-toha/toha) desde la rama `mi-nueva-rama` de tu propio fork.