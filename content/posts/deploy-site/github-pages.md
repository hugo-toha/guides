---
title: "Deploy site in Github Pages"
date: 2020-06-08T06:00:20+06:00
hero: /images/posts/writing-posts/git.svg
menu:
  sidebar:
    name: Github Pages
    identifier: deploy-site-github
    parent: deploy-site
    weight: 10
---

## Draft

1. Modify the `config.yaml` 
	1. Include your GitHub.io URL: `baseURL: https://github-username.github.io/repository-name/`  
		*If your site loads without CSS, double-check this value matches your GitHub URL exactly.*
	2. Add at the root level: `publishDir: docs`

2. Compile the sites HTML.
	1. Open a terminal and navigate to your sites root directory. Simply run the command `hugo` without any other flags. You should see a new folder calls `docs`.

3. Commit your changes and push them to GitHub.

4. Open the GitHub repository in your web browser and navigate to the settings panel. In the GitHub pages section, choose `master branch/docs` as the source.

5. Optional: Add in a custom domain and enforce https.

6. Now, pull up the your GitHub web page. If everything when as expected your site should be live!
