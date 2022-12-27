---
title: "Configuring Achievements Section"
date: 2020-06-08T06:20:30+06:00
menu:
  sidebar:
    name: Achievements Section
    identifier: achievements-section
    parent: sections
    weight: 160
---
{{< alert type="danger" >}}
This doc is outdated. For up-to-date examples, please follow this sample [repo](https://github.com/hugo-toha/hugo-toha.github.io).
{{< /alert >}}

The `Achievements` section has been designed to showcase your achievements in a gallery view. This post will show how to configure the `Achievements` section of your site.

At first,  create an `achievements.yaml` file in the `data` directory of your site. Then, follow the following instruction.

### Add Your Achievements

Now, add your achievements under the `achievements` section in your `achievements.yaml` file as below,

```yaml
achievements:
- title: Best Presenter
  image: images/sections/achievements/presenter.jpg
  summary: Best presenter in the 2020 XYZ conference.
```

Each achievements  entry should have the following fields,

- **title**: The title of the achievement.
- **image**: An image of the achievement.
- **summary**: A summary of the achievement.

>You can use markdown syntax in the `summary` field.

{{< vs 2 >}}

The following image shows how the contents of `achievements.yaml` are mapped into the `Achievements` section.

{{< img src="images/achievements.png" >}}

### Example `achievements.yaml` File

Here, is the `achievements.yaml` file that has been used to create the `Achievements` section of this site.

```yaml
# Your achievements achievements
achievements:
- title: Best Presenter
  image: images/achievements/presenter.jpg
  summary: Best presenter in the 2020 XYZ conference.
- title: Champion
  image: images/achievements/sport.jpg
  summary: Champion in cycling inter-city cycling championship 2020.
- title: Graduation
  image: images/achievements/graduation-cap.jpg
  summary: Received Bachelor of Science (B.Sc.) in Computer Science and Engineer from XYZ University.
- title: Award Winner
  image: images/achievements/woman-winner.jpg
  summary: Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus architecto minus facere vero?
```
