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
- Adding information and sections
- Fixing errors and typos
- Updating obsolete documentation
- Translating the documentation to a new language, [this](/posts/translation/content/) guide might be helpful.

### Translation

Finally, you can contribute to the translation of the theme to several languages, by completing missing words, or by adding a new language. You can follow the guide [How to add an unsupported language](/posts/translation/new-language/) for more information.

## How to contibute?

For local development, you can make changes in the theme submodule and test the changes against your own site or this [example site](https://github.com/hugo-toha/hugo-toha.github.io) locally.

### Fork

At first, fork [this repo](https://github.com/hugo-toha/toha). Then, follow the following steps to use the forked theme for local developments,

#### Running the forked theme against the example site

If your want to run your local development against this [example site](https://github.com/hugo-toha/hugo-toha.github.io), follow the following steps:

```bash
# go to exampleSite directory
$ cd exampleSite
# install hugo modules
$ hugo mod tidy
# install dependencies
$ hugo mod npm pack
$ npm install
# run the example site locally
$ hugo server -w
```

Now, you can make change in the theme and they will be reflected immediately on the running site. If you need to change any configuration, you can do that in the `config.yaml` file inside `exampleSite` folder. If you need to add any content or data, you can create the respective folder inside `exampleSite` directory and add your desired content or data there.

#### Running the forked theme against your own site

If you want to run your local development against your own site, follow the following steps:

**Replace the theme module:**

Open your site's `go.mod` file and replace the `github.com/hugo-toha/toha/v4` with your forked repo's path. For example, if your forked repo is `github.com/<your-github-user>/toha`, then replace the `github.com/hugo-toha/toha/v4` with `github.com/<your-github-user>/toha/v4`.

```go
module github.com/hugo-toha/hugo-toha.github.io

go 1.19

require github.com/hugo-toha/toha/v4 v4.0.1-0.20231229170427-d3968ca711ef // indirect

replace(
    github.com/hugo-toha/toha/v4 => github.com/<your-github-user>/toha/v4 <git branch>
)
```

For interactive development, you can replace the theme with your locally cloned fork. For example, if you have cloned your fork in `/home/my-projects/toha`, then replace the `github.com/hugo-toha/toha/v4` with `/home/my-projects/toha`.

```go
module github.com/hugo-toha/hugo-toha.github.io

go 1.19

require github.com/hugo-toha/toha/v4 v4.0.1-0.20231229170427-d3968ca711ef // indirect

replace(
    github.com/hugo-toha/toha/v4 => /home/my-projects/toha
)
```

**Update dependencies:**

```bash
# update hugo modules
$ hugo mod tidy
# install dependencies
$ hugo mod npm pack
$ npm install
```

**Run your site locally:**

```bash
$ hugo server -w
```

From there you can make changes to the source code of the theme while testing with your running Hugo site or the example site.

### Open a Pull Request

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