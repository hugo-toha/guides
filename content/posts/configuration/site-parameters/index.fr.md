---
title: "Configuration des paramètres du site"
date: 2020-06-08T06:20:55+06:00
menu:
  sidebar:
    name: Paramètres du site
    identifier: configuration-site-parameters
    parent: configuration
    weight: 105
---

Après l'installation du thème, quand vous lancez le site pour la première fois, cela démarrera avec les paramètres par défaut. Cela devrait avoir  l'apparence du site d'exemple excepté qu'il n'a pas de sections sur la page d'accueil. Ces sections sont ajoutées via quelques fichiers de données. Dans les prochains billets, je vais vous montrer comment vous pouvez ajouter ces sections en fournissant des fichiers de données.

Dans ce billet, je vais vous montrer comment vous pouvez changer les paramètres du site pour modifier l'arrière plan, le logo, les informations de l'auteur, et activer/désactiver différentes fonctionnalités.

### Ajouter une image d'arrière plan

D'abord, on va paramètrer un arrière plan sur votre site. Mettez l'image d'arrière plan désirée dans le répertoire `assets/images`. Ensuite, ajoutez ce qui suit dans la section `params` de votre fichier `config.yaml`.

```yaml
background: "images/<le nom de votre image d'arrière plan((avec l'extension du fichier)>"
```

### Ajouter un logo à votre site

Maintenant, ajoutons un logo pour votre site. Vous devez fournir deux logos différents. Un pour la barre de navigation transparente et un autre pour la barre de navigation non transparente. Placez vos logos dans le répertoire `assets/images` et ajoutez ce qui suit dans la section `params` du fichier `config.yaml`.

```yaml
# The inverted logo will be used in the initial transparent navbar and
# the main logo will be used in the non-transparent navbar.
logo:
  main: images/main-logo.png
  inverted: images/inverted-logo.png
  favicon: images/favicon.png
```

### Activer les articles de blog

Si vous voulez écrire quelques articles de blog, vous devez d'abord l'activer. Activons la publication d'articles de blog en ajoutant ce qui suit dans la section `params` de votre fichier `config.yaml`.

```yaml
enableBlogPost: true
```

### Activer `Table Of Contents`

Maintenant, si vous voulez afficher la section `Table Of Contents` dans votre article de blog, vous devez d'abord l'activer dans la section `params` de votre fichier `config.yaml`.

```yaml
enableTOC: true
```
Vous pouvez également contrôler le niveau de votre table des matières en ajoutant la configuration suivante dans la section `markup` de votre fichier `config.yaml`.

```yaml
markup:
  tableOfContents:
    startLevel: 2
    endLevel: 6
    ordered: false
```

Ici, nous avons configuré notre table des matières pour montrer tous les titres à partir de `h2` jusqu'à `h6`.

### Activer le bouton `<Improve This Page>`

Si vous voulez fournir à vos visiteurs un moyen facile d'améliorer un article (par exemple une faute de frappe, un correctif d'indentation, etc.), vous pouvez activer le bouton `<improve This Page>` en ajoutant l'URL de votre dépôt Git dans la section `params` de votre fichier `config.yaml`.

```yaml
gitRepo: <L'URL du dépôt Github de votre site>
```

Cela ajoutera un bouton labelisé `Improve This Page` au pied de chaque billet. Le bouton redirigera l'utilisateur directement vers le formulaire d'édition de Github de la page.

Si vous branche par défaut ne s'appelle pas `main`, alors vous aurez besoin d'ajouter votre branche git par défaut dans la section `params` de votre fichier `config.yaml`.
```yaml
gitBranch: <le nom de votre branche git par défaut>
```

### Activer/Désactiver la Newsletter

La fonctionnalité de newsletter supporte seulement Mailchimp actuellement.
Ajoutez ce qui suit dans la section `params` du fichier `config.yaml`.

```yaml
newsletter:
  enable: true
  provider: mailchimp
  mailchimpURL: https://github.us1.list-manage.com/subscribe/post?u=19de52a4603135aae97163fd8&amp;id=094a24c76e
```

Si vous ne voulez pas utliser la fonctionnalité de newsletter, vous pouvez la masquer en ajoutant ce qui suit dans la section `params` du fichier `config.yaml`.

```yaml
newsletter:
  enable: false
```

### Activer le RAW HTML dans le fichier Markdown

Si vous voulez utiliser le RAW HTML dans vos fichiers markdown, vous devez activier le rendu non sécurisé. Sinon, Hugo n'affichera pas le rendu HTML. Vous pouvez activer le rendu markdown non sécurisé en ajoutant les paramètres `goldmark` suivants dans la section `markup` du fichier `config.yaml`.

```yaml
markup:
  goldmark:
    renderer:
      unsafe: true
```

### Ajouter les informations de l'auteur

Maintenant, fournissons vos informations de base. Créez un fichier `author.yaml` dans le répertoire `/data` et ajoutez-y les informations sur l'auteur.

```yaml
# some information about you
name: "John Doe"
nickname: "John"
# greeting message before your name. it will default to "Hi! I am" if not provided
greeting: "Hi, I am"
image: "images/author/john.png"
# give your some contact information. they will be used in the footer
contactInfo:
  email: "johndoe@example.com"
  phone: "+0123456789"
  github: johndoe
  linkedin: johndoe

# some summary about what you do
summary:
  - I am a Developer
  - I am a Devops
  - I love servers
  - I work on open-source projects
  - I love to work with some fun projects
```

> Note: Les paramètres `contactInfo` utiliseront le paramètre `icon` pour trouver l'icône. Ce paramètre doit correspondre au nom de l'icône géniale [examples](https://fontawesome.com/search?o=r&f=brands)

### Ajouter l'avis du droit d'auteur

On va jouter un avis de droit d'auteur pour votre site. Ca sera affiché en bas du pied de page. Créez un fichier `site.yaml` dans votre répertoire `data` et ajoutez-y la section suivante.

```yaml
copyright: © 2020 Copyright.
```

### La description du site

Maintenant, ajoutez une description de votre site qui aidera les moteurs de recherche à trouver votre site. Ajoutez une section de description dans votre votre fichier `site.yaml`.

```yaml
# Meta description for your site.  This will help the search engines to find your site.
description: Example site for hugo theme Toha.
```

### Ajout d'un menu personnalisé

Si vous voulez ajouter quelques menus personnalisé dans la barre de navigation, vous pouvez facilement les ajouter par l'ajout de ce qui suit dans le fichier `site.yaml`.

Les menus personnalisés sont visibles dans la barre de navigation par défaut. Pour les masquer, paramètrez `hideFromNavbar` sur `true`. Les menus personnalisés sont masqués par défaut dans la zone de navigation du pied de page. Pour afficher un élément de menu personnalisé dans le pied de page, paramètrez sa propriété `showOnFooter` sur `true`.

```yaml
customMenus:
- name: Notes
  url: https://hossainemruz.gitbook.io/notes/
  hideFromNavbar: false
  showOnFooter: true
```

Cela peut être particulièrement utile lorsque vous souhaitez ajouter un lien vers un autre site dans votre barre de navigation.

### Exemple de Section `params`

Pour terminer, voici la section `params` utilisée dans le site d'exemple.

```yaml
# Site parameters
params:
  # background image of the landing page
  background: "images/background.jpg"

  # Provide logos for your site. The inverted logo will be used in the initial
  # transparent navbar and the main logo will be used in the non-transparent navbar.
  # It will default to the theme logos if not provided.
  logo:
    main: images/main-logo.png
    inverted: images/inverted-logo.png
    favicon: images/favicon.png

  # GitHub repo URL of your site
  gitRepo: https://github.com/hossainemruz/toha-example-site

  features:
    # Enable and configure blog posts
    blog:
      enable: true

    # specify whether you want to show Table of Contents in reading page
    toc:
      enable: true

    # Show/hide newsletter section in the footer. Default is "true".
    # Currently, it supports "mailchimp".
    newsletter:
      enable: false
      # provider: mailchimp
      # mailchimpURL: https://github.us1.list-manage.com/subscribe/post?u=19de52a4603135aae97163fd8&amp;id=094a24c76e

    # Show/hide disclaimer notice in the footer. Default is "false".
    disclaimer:
      enable: true
```
