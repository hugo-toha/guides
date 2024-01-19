---
title: "How to Contribute?"
date: 2024-01-19T02:30:00+06:00
description: A guide on how to contribute to toha
author:
  name: BernatBC
  image: images/author/bernatbc.png
menu:
  sidebar:
    name: Contributing
    identifier: contributing
    weight: 900
---

## Ways to Contribute

You can contribute to this theme in various ways.

### Code

Pull requests are most welcome and I will be happy to review. Just follow the following principles:

- Keep it simple.
- Keep it consistent with the design.
- Use as few dependencies as possible.
- Have patience.

### Testing and reporting issues

- You can report a [bug](https://github.com/hugo-toha/toha/issues/new?template=bug.md)
- File a [feature request](https://github.com/hugo-toha/toha/issues/new?template=feature_request.md)
- [share your thoughts](https://github.com/hugo-toha/toha/issues/new?template=question.md)

### Documentation

You can also contribute to the theme documentation by:
- Adding more sections
- Fixing errors and typos
- Updating obsolete documentation
- Translating it to a new language, [this](/posts/translation/content/) guide might be helpful.

### Translation

Finally, you can contribute to the translation of the theme to several languages, by completing missing words, or by adding a new language. You can follow the guide [How to add an unsupported language](/posts/translation/new-language/) for more information.

## How to contibute?

For local development, you can make changes in the theme submodule and test the changes against your own site or this [example site](https://github.com/hugo-toha/hugo-toha.github.io) locally.

### Fork

At first, fork [this repo](https://github.com/hugo-toha/toha). Then, follow the following steps to use the forked theme for local developments,

**Using the forked theme in your own site:**

If you want to run your local development against your own site, follow the following steps:

```bash
# add the original theme as a submodule of your site if you haven't done already
$ git submodule add https://github.com/hugo-toha/toha.git themes/toha
# navigate into the toha theme folder
$ cd themes/toha
# add your own fork as a remote
$ git remote add my-fork https://github.com/<your-github-user>/toha
# create a new branch for your changes
$ git checkout -b my-feature-branch
```

**Using the forked theme in the example site:**

If your want to run your local development against this [example site](https://github.com/hugo-toha/hugo-toha.github.io), follow the following steps:

```bash
# clone the example site along with the submodules
$ git clone git@github.com:hugo-toha/hugo-toha.github.io.git --recursive
# navigate into the toha theme folder
$ cd themes/toha
# add your own fork as a remote
$ git remote add my-fork https://github.com/<your-github-user>/toha
# create a new branch for your changes
$ git checkout -b my-feature-branch
```

From there you can make changes to the source code of the theme while testing with your running Hugo site or the example site.

### Open a PR

When the changes look good, commit and push them to your fork.

```bash
# stage all the changes
$ git add .
# commit the changes with a meaning full commit message
$ git commit -m "A meaningful commit message"
# push the commit to your fork
$ git push my-fork my-feature-branch
```

Then, open a PR against `main` branch of [hugo-toha/toha](https://github.com/hugo-toha/toha) from the `my-feature-branch` branch of your own fork.