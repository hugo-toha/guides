---
title: "Guide Syntaxique Markdown"
date: 2020-06-08T06:15:40+06:00
hero: /images/posts/writing-posts/code.svg
menu:
  sidebar:
    name: Guide Markdown
    identifier: writing-post-md-guide
    parent: writing-post
    weight: 30
---

Cet article propose un échantillon des syntaxes de base du Markdown qui peut être utilisé dans les fichiers de contenu d'Hugo, et montre également des balises HTML de base décorés avec CSS dans un thème Hugo.

<!--more-->

## En-têtes

Les éléments HTML suivant `<h1>`—`<h6>` représentent six niveaux de titres de section. `<h1>` est le niveau le plus élevé tandis que le `<h6>` est le plus bas.

# H1
## H2
### H3
#### H4
##### H5
###### H6

## Paragraphe

Xerum, quo qui aut unt expliquam qui dolut labo. Aque venitatiusda cum, voluptionse latur sitiae dolessi aut parist aut dollo enim qui voluptate ma dolestendit peritin re plis aut quas inctum laceat est volestemque commosa as cus endigna tectur, offic to cor sequas etum rerum idem sintibus eiur? Quianimin porecus evelectur, cum que nis nust voloribus ratem aut omnimi, sitatur? Quiatem. Nam, omnis sum am facea corem alique molestrunt et eos evelece arcillit ut aut eos eos nus, sin conecerem erum fuga. Ri oditatquam, ad quibus unda veliamenimin cusam et facea ipsamus es exerum sitate dolores editium rerore eost, temped molorro ratiae volorro te reribus dolorer sperchicium faceata tiustia prat.

Itatur? Quiatae cullecum rem ent aut odis in re eossequodi nonsequ idebis ne sapicia is sinveli squiatum, core et que aut hariosam ex eat.

## Bloc de citation

Les éléments blockquote représentent le contenu qui est coté à partir d'une autre source, éventuellement avec une citation qui doit être dans un élément `footer` ou `cite`, et éventuellement avec des changments en ligne tel que les annotations et les abrévations.

#### Bloc de citation sans attribution

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Notez** que vous pouvez utiliser la *syntaxe Markdown* à l'intérieur d'un bloc de citation.

#### Bloc de citation avec attribution

> Don't communicate by sharing memory, share memory by communicating.</p>
> — <cite>Rob Pike[^1]</cite>


[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Tableaux

Les tableaux ne font pas partie de la spécification de base du Markdown, mais Hugo les supportent hors-des-clous.

   | Name  | Age |
   | ----- | --- |
   | Bob   | 27  |
   | Alice | 23  |

#### Markdown en ligne dans les tableaux

| Inline&nbsp;&nbsp;&nbsp; | Markdown&nbsp;&nbsp;&nbsp; | In&nbsp;&nbsp;&nbsp;                | Table  |
| ------------------------ | -------------------------- | ----------------------------------- | ------ |
| *italics*                | **bold**                   | ~~strikethrough~~&nbsp;&nbsp;&nbsp; | `code` |

## Blocs de code

#### Bloc de code avec backticks

```
html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
```
#### bloc de code indenté avec quatre espaces

    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>
    
#### Bloc de code avec code abrégé de mise en évidence d'Hugo
{{< highlight html >}}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

## Types de liste

#### Liste ordonnée

1. Première point
2. Second point
3. Troisième point

#### Liste non ordonnée

* Element de la liste
* Autre élément
* Et un autre élément

#### listes imbriquées

* Fruit
  * Pomme
  * Orange
  * Banane
* Selle
  * Lait
  * Fromage

## Autres Elements — abbr, sub, sup, kbd, mark

Ici, vous trouverez d'autres balises HTML décorées par CSS: 
```
<abbr title="Graphics Interchange Format">GIF</abbr> est un format d'image bitmap.
```
<abbr title="Graphics Interchange Format">GIF</abbr> est un format d'image bitmap.
```
H<sub>2</sub>O
```
H<sub>2</sub>O
```
X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>
```
X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>
```
Pressez <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> pour terminer la session.
```
Pressez <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> pour terminer la session.
```
La plupart des <mark>salamandres</mark> sont nocturnes, et chassent les insectes, les vers, et d'autres petites créatures.
```
La plupart des <mark>salamandres</mark> sont nocturnes, et chassent les insectes, les vers, et d'autres petites créatures.