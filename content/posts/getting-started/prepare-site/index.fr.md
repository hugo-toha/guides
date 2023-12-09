---
title: "Préparer Votre Site"
date: 2023-11-06T21:44:20+02:00
menu:
  sidebar:
    name: Prepare votre site
    identifier: getting-started-prepare-site
    parent: getting-started
    weight: 10
---

Dans ce billet, nous allons créer un site hugo de zéro. Nous le configurerons avec le thème `toha`, le rendre multilingue, ajouter quelques exemples de billets. A la fin de ce billet, vous devriez être capable d'exécuter pleinement un site Hugo avec le thème `Toha` localement.

Si vous voulez un démarrage de la tête, vous pouvez juste forker le dépôt [hugo-toha/hugo-toha.github.io](https://github.com/hugo-toha/hugo-toha.github.io), renommez le et mettez le à jour avec vos propres données. Ce dépôt a déjà été configuré pour déployer sur [Github Pages](https://pages.github.com/) et [Netlify](https://www.netlify.com/).

Si vous avez déjà un site hugo, sautez à la section [Ajouter un theme](#add-theme) 

### Créer un dépôt

D'abord, créez un dépôt sur Github. Si vous voulez déployer ce site dans Github Pages, votre dépôt devrait être nommé `<votre username>.github.io`. Clonez le dépôt dans votre machine locale et naviguez dedans.

### Créer un site

Maintenant, assurez-vous d'avoir [Hugo](https://gohugo.io/getting-started/installing/) installé. Ce thème devrait fonctionner avec hugo version `v0.118.0` et plus. Maintenant, lancez la commande suivante depuis la racine de votre dépôt pour initier un site web hugo.

```console
$ hugo new site ./ -f=yaml --force
```

Cette commande créera une structure de base d'un site hugo. Ici, le flag `-f=yaml` indique à hugo de créer un fichier de configuration au format YAML et le flag `--force` force hugo à créer un site même si le répertoire cible n'est pas vide.

### Initialiser le dépôt git

Maintenant, il est temps d'ajouter git à votre site web. Initialisez le dépôt git en utilisant la commande suivante :

```
$ git init
```

### Ajouter un thème

Maintenant, il est temps d'ajouter un thème dans votre site. Ajoutez le thème Toha comme un sous-module git de votre dépôt en utilisant la commande suivante:

```console
$ git submodule add https://github.com/hugo-toha/toha.git themes/toha
```

{{< vs 1 >}}

>N'utilisez pas l'URL SSH du thème durant son ajout en tant que sous-module git. Aussi, ne clonez pas le thème dans votre répertoire `themes` en utilisant `git clone`. Sinon, nous ne pourrons pas automatiser la publication du site en utilisant Github Action ou Netlify. 

### Lancer le site localement

Maintenant, vous pouvez déjà exécuter votre site localement. Observons le site en mode veille en utilisant la commande suivante:

```console
$ hugo server -t toha -w
```

Si vous naviguez sur `http://localhost:1313`, vous devriez voir un site de base avec le thème Toha. Dans la section suivante, nous allons configurer le site pour ressembler au [hugo-toha.github.io](https://hugo-toha.github.io/). Comme nous avons exécuté le serveur en mode veille, tous les changements que nous feront au site seront instantanément visibles dans le navigateur. 

### Configurer le site

Maintenant, nous sommes prêt à configurer notre site. Dans cette section, nous allons ajouter les informations de l'auteur, différentes sections, et des echantillon de billets etc.

####  Mise à jour du `config.yaml`

Quand vous avez créé le site en utilisant la commande `hugo new site`, il a créé un fichier `config.yaml` à la racine de votre dépôt. Remplacer le contenu par défaut du fichier `config.yaml` avec ce qui suit:

```yaml
baseURL: https://hugo-toha.github.io

languageCode: en-us
title: "John's Blog"

# Use Hugo modules to add theme
module:
  imports:
  - path: github.com/hugo-toha/toha/v4
  mounts:
  - source: static/files
    target: static/files
  - source: ./node_modules/flag-icon-css/flags
    target: static/flags
  - source: ./node_modules/@fontsource/mulish/files
    target: static/files
  - source: ./node_modules/katex/dist/fonts
    target: static/fonts

# Manage languages
# For any more details, you can check the official documentation: https://gohugo.io/content-management/multilingual/
languages:
  en:
    languageName: English
    weight: 1
  fr:
    languageName: Français
    weight: 2

# Force a locale to be use, really useful to develop the application ! Should be commented in production, the "weight" should rocks.
# DefaultContentLanguage: bn

# Allow raw html in markdown file
markup:
  goldmark:
    renderer:
      unsafe: true
  tableOfContents:
    startLevel: 2
    endLevel: 6
    ordered: false

# At least HTML and JSON are required for the main HTML content and
# client-side JavaScript search
outputs:
  home:
    - HTML
    - RSS
    - JSON

# Enable global emoji support
enableEmoji: true

# Site parameters
params:
  # GitHub repo URL of your site
  gitRepo: https://github.com/hugo-toha/hugo-toha.github.io

  # specify whether you want to write some blog posts or not
  enableBlogPost: true

  # specify whether you want to show Table of Contents in reading page
  enableTOC: true

  # Provide newsletter configuration. This feature hasn't been implemented yet.
  # Currently, you can just hide it from the footer.
  newsletter:
    enable: true
```

Ici, vous voyez une configuration de base pour le thème Toha. Vous pouvez voir le fichier de configuration utilisé dans le site d'exemple [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/config.yaml). Pour des options de configurations plus détaillées, s'il vous plaît consultez [ce billet](https://toha-guides.netlify.app/posts/configuration/site-parameters/). 

#### Ajouter de données

La plupart des contenus de ce thème sont pilotés par quelques fichiers YAML dans le répertoire `data`. Dans cette section, nous allons ajouter quelques échantillons de données. Puisque nous sommes en train de bâtir un site multilingue, nous allons séparer les données de chaque langue dans leur propre répertoire local.

D'abord, créez le répertoire `en` dans votre répertoire `data`. Ici, nous sommes en train d'ajouter des données pour la langue `anglaise`.

##### Informations sur le site

Maintenant, créez un fichier `site.yaml` dans le répertoire `/data/en/` de votre dépôt. Ajoutez-y le contenu suivant:

```yaml
# Copyright Notice
copyright: © 2020 Copyright.

# Meta description de votre site.  Ca aidera les moteurs de recherche à retrouver votre site.
description: Portfolio and personal blog of John Doe.
```
Pour voir toutes les options disponibles pour les informations du site, consulter [cet extrait de fichier](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/site.yaml).

##### Informations sur l'auteur

Maintenant, créez un fichier `author.yaml` dans le répertoire `data/en` et ajoutez vos informations comme suit:

```yaml
# Quelques informations à propos de vous.
name: "John Doe"
nickname: "John"
# Le message de salutation avant votre nom. Par défaut, ce sera "Hi, I am" s'il n'est pas fournit.
greeting: "Hi, I am"
image: "images/author/john.png"
# Donner vos informations de contact. Elles seront affichées dans le pied de page.
contactInfo:
  email: "johndoe@example.com"
  phone: "+0123456789"
  stack-overflow:
    icon: stack-overflow
    url: "https://stackoverflow.com/users/1/exampleUser"
    text: "ExampleUser"

# Un résumé de ce que vous faites
summary:
  - I am a Developer
  - I am a Devops
  - I love servers
  - I work on open-source projects
  - I love to work with some fun projects
```

##### Ajouter des sections

Maintenant, nous allons ajouter différentes section dans notre page d'accueil. D'abord, créons un répertoire `sections` à l'intérieur de votre répertoire `data/en`. Ici, nous allons ajouter quelques sections avec des configurations minimales. Pour voir les options détaillées de configuration pour les sections, veuillez consulter [ici](https://toha-guides.netlify.app/posts/configuration/sections/).

###### La section A propos

Créons un fichier `about.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# Information de section
section:
  name: About
  id: about
  enable: true
  weight: 1
  showOnNavbar: true
  template: sections/about.html

# votre designation
designation: Software Engineer
# Les informations de votre société
company:
  name: Example Co.
  url: "https://www.example.com"

# Votre Curriculum Vitae. Le chemin de ce fichier doit être relatif vers le répertoire "static"
resume: "files/resume.pdf"

# Un résumé sur vous.
summary: 'I am a passionate software engineer with x years of working experience. I built OSS tools for [Kubernetes](https://kubernetes.io/) using GO. My tools help people to deploy their workloads in Kubernetes. Sometimes, I work on some fun projects such as writing a theme, etc.'

# Vos liens sur les réseaux sociaux
# Mettez-en autant que vous voulez. Utilisez font-awesome pour les icônes
socialLinks:
- name: Email
  icon: "fas fa-envelope"
  url: "example@gmail.com"

- name: Github
  icon: "fab fa-github"
  url: "https://www.github.com/example"

- name: Stackoverflow
  icon: "fab fa-stack-overflow"
  url: "#"

- name: LinkedIn
  icon: "fab fa-linkedin"
  url: "#"

- name: Twitter
  icon: "fab fa-twitter"
  url: "#"

- name: Facebook
  icon: "fab fa-facebook"
  url: "#"

# Affichez vos badges
# Vous pouvez montrer vos certifications depuis https://www.credly.com
# Vous pouvez aussi afficher des barres circulaire indiquant le niveau d'expertise de certaines compétences
badges:
- type: certification
  name: Certified Kubernetes Security Specialist
  url: "https://www.credly.com/org/the-linux-foundation/badge/exam-developer-certified-kubernetes-security-specialist"
  badge: "https://images.credly.com/size/680x680/images/f4bf92ed-8985-40b2-bc07-2f9308780854/kubernetes-security-specialist-logo-examdev.png"

- type: certification
  name: Istio and IBM Cloud Kubernetes Service
  url: "https://www.credly.com/org/the-linux-foundation/badge/exam-developer-certified-kubernetes-security-specialist"
  badge: "https://images.credly.com/size/680x680/images/8d34d489-84bf-4861-a4a0-9e9d68318c5c/Beyond_basics_of_Istio_on_Cloud_v2.png"

- type: certification
  name: Artificial Intelligence and Machine Learning
  url: "https://www.credly.com/org/grupo-bancolombia/badge/artificial-intelligence-and-machine-learning"
  badge: "https://images.credly.com/size/680x680/images/e027514f-9d07-4b29-862f-fe21a8aaebf1/ae.png"

- type: soft-skill-indicator
  name: Leadership
  percentage: 85
  color: blue

- type: soft-skill-indicator
  name: Team Work
  percentage: 90
  color: yellow

- type: soft-skill-indicator
  name: Hard Working
  percentage: 85
  color: orange

# Vous pouvez aussi fournir un code couleur à la place d'un nom de couleur
# - type: soft-skill-indicator
#   name: Example 1
#   percentage: 75
#   color: "#00adb5"
```
Mettre le fichier `resume.pdf` dans le répertoire `/static/files`. Vous pouvez trouver le fichier `about.yaml` utilisé dans le site exemple depuis [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/about.yaml).

###### Section Compétences

Créons un fichier `skills.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# Information de section
section:
  name: Skills
  id: skills
  enable: true
  weight: 2
  showOnNavbar: true
  # En option : Possibilité de masquer le titre dans les sections
  # hideTitle: true

# Vos compétences
# Donnez un bref résumé pour chaque compétence dans le champ summary
skills:
- name: Kubernetes
  logo: "/images/sections/skills/kubernetes.png"
  summary: "Capable of deploying, managing application on Kubernetes. Experienced in writing Kubernetes controllers for CRDs."
  url: "https://kubernetes.io/"

- name: Go Development
  logo: "/images/sections/skills/go.png"
  summary: "Using as the main language for professional development. Capable of writing scalable, testable, and maintainable program."
  url: "https://golang.org/"

- name: Cloud Computing
  logo: "/images/sections/skills/cloud.png"
  summary: "Worked with most of the major clouds such as GCP, AWS, Azure etc."
```

Mettez vos images de compétences dans le répertoire `images/sections/skills` de votre dépôt. Vous trouverez les images [ici](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/assets/images/sections/skills). Vous pouvez également trouver le fichier `skills.yaml` utilisé dans le site exemple par [là](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/skills.yaml).

###### Section Expériences

Créez un fichier `experiences.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# Information de section
section:
  name: Experiences
  id: experiences
  enable: true
  weight: 3
  showOnNavbar: true
  # En option : Possibilité de masquer le titre dans les sections
  # hideTitle: true 

# Vos expériences
experiences:
- company:
    name: Example Co.
    url: "https://www.example.com"
    location: Dhaka Branch
    # Aperçu de l'entreprise
    overview: Example Co. is a widely recognized company for cloud-native development. It builds tools for Kubernetes.
  positions:
  - designation: Senior Software Engineer
    start: Nov 2019
    # Si vous êtes toujours en poste, n'indiquez pas de date de fin. Ce sera remplacé par "Aujourd'hui"
    # end: Dec 2020
    # Indiquez quelques éléments à propos de vos responsabilités au sein de l'entreprise.  
    responsibilities:
    - Design and develop XYZ tool for ABC task
    - Design, develop and manage disaster recovery tool [Xtool](https://www.example.com) that backup Kubernetes volumes, databases, and cluster's resource definition.
    - Lead backend team.

- company:
    name: PreExample Co.
    url: "https://example.com"
    location: Nowhere
    overview: PreExample Co. is a gateway company to enter into Example co. So, nothing special here.
  positions:
  - designation: Software Engineer
    start: March 2016
    end: May 2017
    responsibilities:
    - Write lots of example codes.
    - Read lots of examples.
    - See lots of example videos.
```

Vous pouvez trouver le fichier `experiences.yaml` utilisé dans le site exemple par [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/experiences.yaml).

###### Section Projets

Créez un fichier `projects.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# Information de section
section:
  name: Projects
  id: projects
  enable: true
  weight: 5
  showOnNavbar: true
  # En option : Possibilité de masquer le titre dans les sections
  # hideTitle: true

# buttons de filtrage
buttons:
- name: All
  filter: "all"
- name: Professional
  filter: "professional"
- name: Academic
  filter: "academic"
- name: Hobby
  filter: "hobby"

# vos projets
projects:
- name: Kubernetes
  logo: /images/sections/projects/kubernetes.png
  role: Contributor
  timeline: "March 2018 - Present"
  repo: https://github.com/kubernetes/kubernetes # Si votre projet est un dépôt public sur GitHub, alors fournissez le lien. Ca affichera le compteur d'étoile.
  #url: ""  # Si votre projet n'est pas public mais il a un site web or quelques urls externes, alors fournissez les ici. Ne fournissez pas "repo" et "url" simultanément.
  summary: Production-Grade Container Scheduling and Management.
  tags: ["professional", "kubernetes", "cloud"]

- name: Tensorflow
  logo: /images/sections/projects/tensorflow.png
  role: Developer
  timeline: "Jun 2018 - Present"
  repo: https://github.com/tensorflow/tensorflow
  #url: ""
  summary: An Open Source Machine Learning Framework for Everyone.
  tags: ["professional", "machine-learning","academic"]

- name: Toha
  logo: /images/sections/projects/toha.png
  role: Owner
  timeline: "Jun 2019 - Present"
  repo: https://github.com/hossainemruz/toha
  summary: A Hugo theme for personal portfolio.
  tags: ["hobby","hugo","theme","professional"]
```
Mettez les images des projets dans le répertoire `images/sections/projects/`. Vous trouverez les images [ici](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/assets/images/sections/projects). Vous pouvez également trouver le fichier `projects.yaml` utilisé dans le site exemple par [là](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/projects.yaml).

###### Section Billets récents

Créez le fichier `recent-posts.yaml` dans votre répertoire `/data/en/sections/`. Puis ajoutez le contenu suivant:

```yaml
# Information de section
section:
  name: Recent Posts
  id: recent-posts
  enable: true
  weight: 6
  # En option : Possibilité de masquer le titre dans les sections
  # hideTitle: true

# Pas de configuration additionnelles requises
```

Vous pouvez trouver le fichier `recent-posts.yaml` utilisé dans le site d'exemple [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/recent-posts.yaml).

> Cette section sera vide jusqu'à ce que vous ajoutiez quelques billets dans votre site.

###### Section Réalisation

Créez un fichier `achievements.yaml` dans votre répertoire `/data/en/sections/`. Puis ajoutez le contenu suivant:

```yaml
# Information de section
section:
  name: Achievements
  id: achievements
  enable: true
  weight: 8
  showOnNavbar: true
  # En option : Possibilité de masquer le titre dans les sections
  # hideTitle: true

# Vos réalisations
achievements:
- title: Best Presenter
  image: /images/sections/achievements/presenter.jpg
  summary: Best presenter in the 2020 XYZ conference.
- title: Champion
  image: /images/sections/achievements/sport.jpg
  summary: Champion in cycling inter-city cycling championship 2020.
- title: Graduation
  image: /images/sections/achievements/graduation-cap.jpg
  summary: Received Bachelor of Science (B.Sc.) in Computer Science and Engineer from XYZ University.
- title: Award Winner
  image: /images/sections/achievements/woman-winner.jpg
  summary: Wined best paper award at IEE Conference 2020.
```
Mettez les images des projets dans le répertoire `images/sections/achievements/`. Vous trouverez les images [ici](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/assets/images/sections/achievements). Vous pouvez également trouver le fichier `achievements.yaml` utilisé dans le site exemple par [là](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/achievements.yaml).

#### Ajout de billets

Maintenant, nous sommes prêts à ajouter nos premiers billet dans notre site. Ici, nous allons ajouter ce [billet d'introduction](https://hugo-toha.github.io/posts/introduction/).

- D'abord, créez un répertoire `posts` à l'intérieur du répertoire `content` de votre site.
- Ensuite, créez un fichier `_index.md` à l'intérieur du répertoire `posts`. Copiez le contenu de ce [fichier](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/_index.md) et collez le dans le nouveau fichier `_index.md` récemment créé.
- Créez un répertoire `introduction` à l'intérieur du répertoire `posts`.
- Ajoutez le [hero.svg](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/introduction/hero.svg) suivant à l'intérieur de votre répertoire `introduction`.
- Maintenant, créez un fichier `index.md` à l'intérieur du répertoire `introduction`. Ce fichier `index.md` contiendra les contenus du billet.
- Ajoutez l'[extrait de contenus](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/introduction/index.md) suivant dans le fichier `index.md` récemment créé.

Maintenant, votre billet devrait apparaître à `http://localhost:1313/posts` et votre section `Billets Récents` devrait aussi afficher la carte de ce billet. Pour traduire ce billet, créez simplement un nouveau fichier `index.<langage code>.md` dans le même répertoire. Puis, ajoutez le contenu traduit dedans.

Pour plus de billets d'échantillon, s'il vous plaît consultez [ici](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/content/posts).

### Et ensuite ?

A ce stade, votre site doit avoir une apparence similaire au [site d'exemple](https://hugo-toha.github.io/). Maintenant, il est temps de déployer votre site. Vous pouvez suivre les guides de déploiement ci-dessous:

- [Déployer dans Github Pages](https://toha-guides.netlify.app/posts/getting-started/github-pages/)
- [Déployer dans Netlify](https://toha-guides.netlify.app/posts/getting-started/netlify/)
