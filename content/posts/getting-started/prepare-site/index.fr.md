---
title: "Préparer Votre Site"
date: 2023-11-06T21:44:20+02:00
menu:
  sidebar:
    name: Prepare Site
    identifier: getting-started-prepare-site
    parent: getting-started
    weight: 10
---


{{< alert type="danger" >}}
This doc is outdated. For up-to-date examples, please follow this sample [repo](https://github.com/hugo-toha/hugo-toha.github.io).
{{< /alert >}}

Dans ce billet, nous allons créer un site hugo de zéro. Alors, nous le configurerons avec le thème `toha`, le rendre multilingue, ajouter quelques exemples de billets. A la fin de ce billet, vous devriez être capable d'exécuter pleinement un site Hugo avec le thème `Toha`  localement.

Si vous voulez un démarrage de la tête, vous pouvez juste forker le dépôt [hugo-toha/hugo-toha.github.io](https://github.com/hugo-toha/hugo-toha.github.io), renommez le et mettez le à jour avec vos propres données. Ce dépôt a déjà été configuré pour déployer sur [Github Pages](https://pages.github.com/) et [Netlify](https://www.netlify.com/).

Si vous avez déjà un site hugo, sautez à la section [Ajouter un theme](#add-theme) 

### Créer un dépôt

D'abord, créez un dépôt sur Github. Si vous voulez déployer ce site dans Github Pages, votre dépôt devrait être nommé `<votre username>.github.io`. Clonez le dépôt dans votre machine locale et naviguez dedans.

### Créer un site

Maintenant, assurez-vous d'avoir [Hugo](https://gohugo.io/getting-started/installing/) installé. Ce thème devrait fonctionner avec hugo version `v0.68.0` et plus. Maintenant, lancez la commande suivante depuis la racine de votre dépôt pour initier un site web hugo.

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
theme: "toha"

# Manage languages
# For any more details, you can check the official documentation: https://gohugo.io/content-management/multilingual/
languages:
  en:
    languageName: English
    weight: 1

# Control TOC depth
markup:
  tableOfContents:
    startLevel: 2
    endLevel: 6
    ordered: false

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

Ici, vous voyez une configuration de base pour le thème Toha. Vous pouvez voir le fichier de configuration utilisé dans le formulaire du site d'exemple [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/config.yaml). Pour des options de configurations plus détaillées, s'il vous plaît consulter [ce billet](https://toha-guides.netlify.app/posts/configuration/site-parameters/). 

#### Ajouter de données

La plupart des contenus de ce thème sont pilotés par quelques fichiers YAML dans le répertoire `data`. Dans cette section, nous allons ajouter quelques échantillons de données. Puisque nous sommes en train de bâtir un site multilingue, noujs allons garder séparer les données de chaque langue dans leur propre répertoire local.

D'abord, créons le répertoire `en` dans votre répertoire `data`. Ici, nous sommes en train d'ajouter des données pour la langue `anglaise`.

##### Site Information

Maintenant, créons un fichier `site.yaml` dans le répertoire `/data/en/` de votre dépôt. Ajoutons-y le contenu suivant:

```yaml
# Copyright Notice
copyright: © 2020 Copyright.

# Meta description de votre site.  Ca aidera les moteurs de recherche à retrouver votre site.
description: Portfolio and personal blog of John Doe.
```
Pour voir toutes les options disponibles pour les informations du site, consulter [cet extrait de fichier](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/site.yaml).

##### Author Information

Maintenant, créons un fichier `author.yaml` dans le répertoire `data/en` et ajoutez vos informations comme suit:

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
# section information
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
# Mettez-en autant que vous voulez. Utilisez use font-awesome for the icons
socialLinks:
- name: Github
  icon: "fab fa-github"
  url: "https://www.github.com/example"

# Vos compétences génériques.
# Donnez un pourcentage entre 50 et 100 avec des intervalles de 5
# Les couleurs actuellement supportées : blue (bleu), yellow (jaune), pink (rose), green (vert), sky (ciel), orange (orange)
softSkills:
- name: Leadership
  percentage: 85
  color: blue
- name: Team Work
  percentage: 90
  color: yellow
```
Mettre le fichier `resume.pdf` dans le répertoire `/static/files`. Vous pouvez trouver le fichier `about.yaml` utilisé dans le site exemple depuis [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/about.yaml).

###### Section Compétences

Créons un fichier `skills.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# section information
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

Créons un fichier `experiences.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# section information
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
    # company overview
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

Créons un fichier `projects.yaml` dans votre répertoire `/data/en/sections`. Puis ajoutez le contenu suivant:

```yaml
# section information
section:
  name: Projects
  id: projects
  enable: true
  weight: 4
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

###### Recent Posts Section

Créons le fichier `recent-posts.yaml` dans votre répertoire `/data/en/sections/`. Puis ajoutez le contenu suivant:

```yaml
# section information
section:
  name: Recent Posts
  id: recent-posts
  enable: true
  weight: 5
  showOnNavbar: true
```

Vous pouvez trouver le fichier `recent-posts.yaml` utilisé dans le site d'exemple [ici](https://github.com/hugo-toha/hugo-toha.github.io/blob/source/data/en/sections/recent-posts.yaml).

> Cette section sera vide jusqu'à ce que vous ajoutiez quelques billets dans votre site.

###### Section Réalisation

Créons un fichier `achievements.yaml` dans votre répertoire `/data/en/sections/`. Puis ajoutez le contenu suivant:

```yaml
# section information
section:
  name: Achievements
  id: achievements
  enable: true
  weight: 6
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

#### Add Posts

Now, we are ready add our first post into our site. Here, we are going to add this [introduction post](https://hugo-toha.github.io/posts/introduction/).

- At first, create a `posts` folder inside `content` directory of your site.
- Then, create `_index.md` file inside the `posts` directory. Copy the content of [this file](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/_index.md) file and paste into the newly created `_index.md` file.
- Create `introduction` folder inside your `posts` directory.
- Add the following [hero.svg](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/introduction/hero.svg) inside your `introduction` folder.
- Now, create `index.md` file inside the `introduction` folder. This `index.md` file will hold the post contents.
- Add the following [sample contents](https://raw.githubusercontent.com/hugo-toha/hugo-toha.github.io/source/content/posts/introduction/index.md) in the newly created `index.md` file.

Now, your post should appear at `http://localhost:1313/posts` and your `Recent Posts` section also should show this post card. For translating a post, just create a new file with name `index.<language code>.md` in the same directory. Then, add the translated content there.

For more sample posts, please visit [here](https://github.com/hugo-toha/hugo-toha.github.io/tree/source/content/posts).

### What Next

At this point, your site should look similar to the [example site](https://hugo-toha.github.io/). Now, it's time to deploy your site. You can follow the following deployments guides:

- [Deploy in Github Pages](https://toha-guides.netlify.app/posts/getting-started/github-pages/)
- [Deploy in Netlify](https://toha-guides.netlify.app/posts/getting-started/netlify/)
