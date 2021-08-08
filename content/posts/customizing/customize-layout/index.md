---
title: "Customizing the layout"
date: 2021-08-07T06:20:50+06:00
hero: /images/posts/configuration/about-section-hero.svg
author:
  name: James Ray
  image: images/author/james.jpg
menu:
  sidebar:
    name: Layout Customization
    identifier: customizing-layout
    parent: customizing
    weight: 411
---

## We've all been there
We all want to be able to customize the layout of a given theme, and in this short tutorial I will show you how. I stumbled my way through this, and I hope you won't have to as well.

### Step 1 / CSS
Finding what you are wanting to customize. The first thing I wanted to do was customize the css styles. I stumbled through a few git issues, and posts and found that truly the author made it easy, I just didn't think it through (as I was new to Hugo as well).

All you will need to do is create the following structure in your root directory: `/static/css/style.css` Congrats! You're done! The rest is just styling things how you like.

{{< alert type="warning" >}}
The following steps will prevent you from seeing updates on any files that you overwrite.
{{< /alert >}}

### Step 2 / Layout Changes
After accomplishing the layout changes I wanted to look at what it would take to add SCSS into the theme. However, as stated, being new to Hugo set me back just a bit. Unfortunately, I was unable to find a better method, however you can overwrite the layout files by simply place the file you want in the same structure that is in the theme's layout directory.

### Step 3 / Adding SCSS
As stated I wanted to change the layout so that I could use SCSS. Well, we're to that point. Now that we know how to update the layout files you will need to update them to grab SCSS files instead. I personally used the following code and it seems to work well.
```markdown
<!--================= custom style overrides =========================-->
    {{ $options := (dict "targetPath" "style.css" "outputStyle" "compressed" "enableSourceMap" true "includePaths" (slice "")) }}
    {{ $sass := resources.Get "/sass/style.scss" }}
    {{ $style := $sass | resources.ToCSS $options }}
    <link rel="stylesheet" href="{{ $style.Permalink }}"/>
```
You can leave our the `"includePaths" (slice "")` portion if you are not wanting to combine external files with it. SCSS will still be able to import files as expected.

After adding the changes to the layouts, you will want to add your sass files into `/assests/sass/style.scss`

#### Recommended files
These are the files I recommend to update to add SCSS.
- `_default`
  - `baseof.html`
- `index.html`
