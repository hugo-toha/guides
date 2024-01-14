---
title: "Démarrage rapide"
date: 2022-08-09T00:00:00+06:00
description: "Guide de démarrage rapide pour le thème Toha"
menu:
  sidebar:
    name: "Démarrage rapide"
    identifier: quickstart
    weight: 2
---

**Salutation !** Merci d'avoir décidé d'utiliser ce thème. Dans ce guide, Je vais vous montrer comment commencer rapidement avec ce thème.

Ici, je vais supposer que vous voulez commencer un nouveau site Hugo en utilisant ce thème. Si vous utilisez déjà Hugo pour votre site, alors vous devez savoir comment utiliser un thème. Dans ce cas, veuillez suivre ce [dépôt échantillon](https://github.com/hugo-toha/hugo-toha.github.io) pour plus de détails.

### Le nécessaire

Pour exécuter ce thème localement, vous devez avoir les outils suivants installés.

1. Hugo version `v0.118.x` (extended) ou plus.
2. Langage [Go](https://go.dev/doc/install) version `v1.18.x` or plus.
3. Node version `v18.x` et npm version `8.x` ou plus.

Assurez-vous d'avoir les outils nécessaires dans les versions appropriées en utilisant les commandes suivantes.

```bash
# Contrôle de la version de Hugo
➜ hugo version
hugo v0.118.2+extended linux/amd64 BuildDate=unknown

# Contrôle de la version de Go
➜ go version
go version go1.19.4 linux/amd64

# Contrôle de la version de Node
➜ node -v
v18.12.1

# Contrôle de la version de NPM
➜ npm -v
8.19.2
```

### Commencer

Maintenant, revenons à notre mission. Suivez simplement les 5 étapes pour commencer avec votre site.

#### Etape 1: Forker le dépôt d'exemple et renommer

D'abord, **forkez** ce [dépôt échantillon](https://github.com/hugo-toha/hugo-toha.github.io) sur votre compte. Ensuite, renommez ce dépôt commme vous voulez. Si vous voulez utiliser les [Github Pages](https://pages.github.com/) pour déployer votre site, alors renommez le en `<your username>.github.io`. Ce dépôt échantillon fourni des Github Actions pré-configurés pour publier le site dans Github Pages et Netlify.

#### Etape 2: Cloner le dépôt forké localement

Lorsque vous avez forké et renommé votre dépôt d'échantillon, vous pouvez maintenant cloner le dépôt forké sur votre machine locale pour d'autres changements.

```bash
git clone git@github.com:<votre username>/<nom du dépôt forké>
```

#### Etape 3: Mettre à jour le fichier du module

Vous devriez voir les fichiers `go.mod` et `go.sum` à la racine du dépôt. Mettez à jour la première ligne du fichier `go.mod` comme suit:

```bash
module github.com/<votre username>/<nom du dépôt forké>
```

#### Etape 4: Modifier le fichier `config.yaml`

Maintenant, ouvrez le dépôt dans un éditeur et modifiez les configurations dans votre fichier `config.yaml` situé à la racine de votre dépôt.

##### Modifier le `baseURL`

D'abord, modifiez le `baseURL` avec l'URL de votre site. Si vous voulez utilisez Github Pages pour héberger votre site, alors paramètrez comme suit:

```yaml
baseURL: https://<votre username>.github.io
```

##### Modifier le `gitRepo`

Maintenant, modifiez le `gitRepo` sous la section `params` pour pointer sur votre dépôt forké. Exemple,

```yaml
gitRepo: https://github.com/<votre username>/<votre nom de dépôt forké>
```

##### Désactiver l'analytique ou la configurer correctement

Le dépôt d'échantillon fournit le service Google Analytics pré-configuré. L'identifiant analytics indique le site d'origine. Donc, soit vous désactivez les analyses, soit vous les configurez correctement selon ce [guide](/posts/analytics/).

Vous pouvez désactiver les analyses en paramètrant le champ suivant sous la section `params.features` :

```yaml
analytics:
  enabled: false
```

##### Désactiver la fonctionnalité de lettre d'information

Le dépôt d'échantillon fournit un service de lettre d'information [mailchimp](https://mailchimp.com/) pré-configuré. Désactivez-le en paramètrant le champ suivant sous la section `params.footer`.

```yaml
newsletter:
  enable: false
```

#### Step 5: Exécuter le site localement

Maintenant, exécutez les commandes suivantes pour lancer votre site localement:

a. Charger les modules Hugo

```bash
hugo mod tidy
```

b. Installer les modules Node

```bash
hugo mod npm pack
npm install
```

c. Exécuter le site

```bash
hugo server -w
```  

<br>

Si tout se passe bien, vous devriez voir une sortie similaire à ceci.
{{< img src="images/local_site.png" align="center" alt="Command to run site locally">}}

Maintenant, allez sur [localhost:1313](http://localhost:1313/) dans votre navigateur et vous devriez voir vous site en cours d'exécution.

#### Etape 6: Pousser les modifications sur Github

Si vous êtes arrivé aussi loin, cela signifie que votre site s'exécute localement sans aucuns problèmes. Poussons ces modifications sur Github.

```bash
# stage all the changes
git add .

# commit the changes
git commit -m "Initial site setup" -s

# push the changes to Github
git push origin HEAD
```

### Et ensuite ?

- Personnaliser l'arrière-plan, le logo, et quelques autres choses de votre site en suivant [ce guide](/fr/posts/configuration/site-parameters/).
- Ajouter des informations sur vous en suivant [ce guide](/fr/posts/configuration/sections/about/).
- Ajouter les informations sur vos compétences en suivant [ce guide](/fr/posts/configuration/sections/skills/).
- Ajouter les informations sur vos expériences en suivant [ce guide](/fr/posts/configuration/sections/experiences/).
- Déployer votre site sur Github Page en suivant le guide par [ici](/fr/posts/getting-started/github-pages/).
- Déployer votre site sur Netlify en suivant le guide par [ici](/fr/posts/getting-started/netlify/).

