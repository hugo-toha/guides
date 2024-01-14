---
title: "Inicio Rápido"
date: 2022-08-09T00:00:00+06:00
description: Guía de inicio rápido para el tema Toha
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Inicio Rápido
    identifier: quickstart
    weight: 2
---

**¡Saludos!** Gracias por decidirte utilizar este tema. En esta guía, te enseñaré cómo puedes empezar con este tema rápidamente.

Aquí asumiré que quieres empezar de cero una página de Hugo utilizando este tema. Si ya estás usando Hugo para tu sitio, entonces ya sabes cómo utilizar un tema. En este caso, por favor, sigue este [repositorio de ejemplo](https://github.com/hugo-toha/hugo-toha.github.io) para más información.

### Requisitos

Para ejecutar el tema localmente, debes tener las siguientes herramientas instaladas.

1. Versión Hugo `v0.118.x` (extended) o posterior.
2. [Go](https://go.dev/doc/install) language versión `v1.18.x` o posterior.
3. Versión Node `v18.x` y versión npm `8.x` o posterior.

Asegúrate de que tienes las herramientas requeridas instaladas con la versión adecuada usando los siguientes comandos.

```bash
# Comprobar versión de Hugo
➜ hugo version
hugo v0.118.2+extended linux/amd64 BuildDate=unknown

# Comprobar versión de Go
➜ go version
go version go1.19.4 linux/amd64

# Comprobar versión de Node
➜ node -v
v18.12.1

# Comprobar versión de npm
➜ npm -v
8.19.2
```

### Empezando

Ahora, volvamos a nuestra misión. Simplemente, siga estos 6 pasos para empezar con tu página.

#### Paso 1: Haz un fork del repositorio de ejemplo y renómbralo

Al principio, haz **fork** del [repositorio de ejemplo](https://github.com/hugo-toha/hugo-toha.github.io) en su cuenta. Después, renombra el repositorio al nombre que desee. Si deseas utilizar [Github Pages](https://pages.github.com/) para desplegar su sitio, entonces renómbralo a `<tu usuario>.github.io`. El repositorio de ejemplo viene con Github Actions preconfiguradas para publicar el sitio en Github Pages y Netlify.

#### Paso 2: Clone su repositorio localmente

Una vez haya hecho el fork y cambiado el nombre del repositorio, ahora puede clonar su repositorio en su máquina local para realizar vuestros cambios.

```bash
git clone git@github.com:<su usuario>/<nombre de su repositorio>
```

#### Paso 3: Actualiza el archivo del módulo

Deberías ver los archivos `go.mod` y `go.sum` en la raíz de su repositorio. Actualice la primera línea del archivo `go.mod` como a continuación:

```bash
module github.com/<su usuario>/<nombre de su repositorio>
```

#### Paso 4: Cambie el archivo `config.yaml`

Ahora, abre el repositorio en un editor y, cambie las siguientes configuraciones en tu archivo `config.yaml` localizado en la raíz de su repositorio.

##### Cambia la `baseURL`

Primero, cambia la `baseURL` a la URL de su sitio web. Si quieres utilizar Github Pages para hostear su sitio, entonces establézcalo como a continuación:

```yaml
baseURL: https://<su usuario>.github.io
```

##### Cambia el `gitRepo`

Ahora, cambia el campo `gitRepo` debajo de la sección `params` para apuntar a su repositorio. Por ejemplo,

```yaml
gitRepo: https://github.com/<su usuario>/<su repositorio>
```

##### Deshabilite analíticas o configúralas adecuadamente

El repositorio de ejemplo viene con Google Analytics preconfigurado. El id de las analíticas apunta al sitio original. Entonces, deshabilita las analíticas o configúralas adecuadamente de acuerdo a [esta guía](/es/posts/analytics/).

Puede deshabilitar las analíticas estableciendo el siguiente campo debajo de la sección `params.features`:

```yaml
analytics:
  enabled: false
```

##### Deshabilite la funcionalidad del boletín informativo

El repositorio de ejemplo viene con un servicio de boletín informativo [mailchimp](https://mailchimp.com/) preconfigurado. Deshabilítelo estableciendo el siguiente campo debajo de la sección `params.footer`.

```yaml
newsletter:
  enable: false
```

#### Paso 5: Ejecuta el sitio localmente

Ahora, ejecuta el siguiente comando para ejecutar su sitio web localmente:

a. Cargar módulos de Hugo

```bash
hugo mod tidy
```

b. Instalar módulos de Node

```bash
hugo mod npm pack
npm install
```

c. Ejecutar el sitio web

```bash
hugo server -w
```

<br>

Si todo ha ido bien, deberías ver un output similar a este.
{{< img src="images/local_site.png" align="center" alt="Command to run site locally">}}

Ahora, dirígete a [localhost:1313](http://localhost:1313/) en tu navegador y deberías ver su sitio web ejecutándose.

#### Paso 6: Haz un push de tus cambios a Github

Si has llegado hasta aquí, significa que su sitio está ejecutándose localmente sin ningún fallo. Vamos a hacer un push de estos cambios a Github.

```bash
# añade todos sus cambios
git add .

# haz commit de los cambios
git commit -m "Initial site setup" -s

# haz push de los cambios a Github
git push origin HEAD
```

### Siguientes pasos

- Customiza el fondo, logo, y algunas otras cosas de su sitio siguiendo [esta guía](/posts/configuration/site-parameters/).
- Añade su información personal siguiendo [esta guía](/es/posts/configuration/sections/about/).
- Añade su información sobre habilidades siguiendo [esta guía](/es/posts/configuration/sections/skills/).
- Añade su información sobre experiencia siguiendo [esta guía](/es/posts/configuration/sections/experiences).
- Despliega su sitio web en Github Pages siguiendo [esta guía](/es/posts/getting-started/github-pages/).
- Despliega su sitio web en Netlify siguiendo [esta guía](/es/posts/getting-started/netlify/).