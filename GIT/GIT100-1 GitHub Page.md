- Can use to showcase some open source projects, host a blog or even share resume.
- Create a user site at:
```bash
<username>.github.io
```
# Creating Website
1. In the upper-right corner of any page, select +, then click New repository.
   ![[Pasted image 20260210001626.png]]
2. Enter ***username.github.io*** as the repository name. Replace ***username*** with GitHub username.
   If username is octocat, the repository name should be ***octocat.github.io***.
   ![[Pasted image 20260210001853.png]]
3. Choose a repository visibility.
4. Toggle Add README to On.
5. Click Create repository.
6. Under repository name, click Settings. If cannot see the ***Setting*** tab, select the dropdown menu, then click ***Settings***.
   ![[Pasted image 20260210002120.png]]
7. In the ***Code and automation*** section of the sidebar, click ***Pages***.
8. Under ***Build and deployment*** under ***Source***, select ***Deploy a branch***.
9. Under ***Build and deployment*** under ***Branch***, use the branch dropdown menu and select a publishing source.
   ![[Pasted image 20260210002359.png]]
10. Optionally, open the ***README.md*** file of repository. The ***README.md*** file is where will write the content of site. Can edit the file or keep the default content for now.
11. Visit ***username.github.io*** to view new website. Note that it can take up to 10 minutes for changes to site to publish after push the changes to GitHub.
# Changing the title and description
By default, the title of site is ***username.github.io***. Can change the title by editing the ***_config.yml*** file in repository.

1. Click the ***Code*** tab of repository.
2. In the file list, click ***_config.yml*** to open the file.
3. Click to edit file.
4. The ***_config.yml*** file already contains a line that specifies the theme for site. Add a new line with ***title:*** followed by the title want. Add a new line with ***description:*** followed by the description want. For example:
```bash
theme: jekyll-theme-minimal
title: Jim\'s Homepage
description: My projects updates!
```