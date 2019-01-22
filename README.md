[![pipeline status](https://gitlab.com/FairCustodian/blog/badges/master/pipeline.svg)](https://gitlab.com/FairCustodian/blog/commits/master)
![Jekyll Version](https://img.shields.io/gem/v/jekyll.svg)

---

# Fair Custodian Specific

## Creating a post

1. Create a markdown file in the `_posts` folder named `YYYY-MM-DD-url-title.md`. This will create the URL `blog.faircustodian.com/2019/01/01/url-title.html`. This should not the whole title, just something short and unique.
2. The file **must** start with a header containg at the very least `layout: post` , `title: The full title of the post` and `date: YYYY-MM-DD HH:MM:SS -0000`.
3. Additionally, you can add `excerpt: "This will show when posted on socail media < 160 chars` (if not provided, it defaults to the first 160 chars of the post) and `image: A link to an image that will be shown when posted on social media` (if not provided, it defaults to the 1:1 image we use for the app).
4. You need to build the site using jekyll before committing and pushing to github by running `bundle exec jekyll build -d docs` from the root directory.

Example:

```
---
layout: post
title:  "Hello, world!"
date:   2019-01-01 10:00:00 -0000
image: "https://s3-eu-west-1.amazonaws.com/fc-app-assets/FC-Image_01_1x1.jpg"
excerpt: "A little intro to Fair Custodian and the team behind it."
---
```

---

Example [Jekyll] website using GitLab Pages.  View it live at https://pages.gitlab.io/jekyll

[Learn more about GitLab Pages](https://pages.gitlab.io) or read the the [official GitLab Pages documentation](https://docs.gitlab.com/ce/user/project/pages/).

---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Getting Started](#getting-started)
  - [Start by forking this repository](#start-by-forking-this-repository)
  - [Start from a local Jekyll project](#start-from-a-local-jekyll-project)
- [GitLab CI](#gitlab-ci)
- [Using Jekyll locally](#using-jekyll-locally)
- [GitLab User or Group Pages](#gitlab-user-or-group-pages)
- [Did you fork this project?](#did-you-fork-this-project)
- [Other examples](#other-examples)
- [Troubleshooting](#troubleshooting)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Getting Started

You can get started with GitLab Pages using Jekyll easily by either forking this repository or by uploading a new/existing Jekyll project.

Remember you need to wait for your site to build before you will be able to see your changes.  You can track the build on the **Pipelines** tab.

### Start by forking this repository

1. Fork this repository.
1. **IMPORTANT:** Remove the fork relationship.
Go to **Settings (⚙)** > **Edit Project** and click the **"Remove fork relationship"** button.
1. Enable Shared Runners.
Go to **Settings (⚙)** > **Pipelines** and click the **"Enable shared Runners"** button.
1. Rename the repository to match the name you want for your site.
1. Edit your website through GitLab or clone the repository and push your changes.

### Start from a local Jekyll project

1. [Install][] Jekyll.
1. Use `jekyll new` to create a new Jekyll Project.
1. Add [this `.gitlab-ci.yml`](.gitlab-ci.yml) to the root of your project.
1. Push your repository and changes to GitLab.


GITHUB: `bundle exec jekyll build -d docs`


## GitLab CI

This project's static Pages are built by [GitLab CI][ci], following the steps
defined in [`.gitlab-ci.yml`](.gitlab-ci.yml):

```
image: ruby:2.3

variables:
  JEKYLL_ENV: production

pages:
  script:
  - bundle install
  - bundle exec jekyll build -d public
  artifacts:
    paths:
    - public
  only:
  - master
```

## Using Jekyll locally

To work locally with this project, you'll have to follow the steps below:

1. Fork, clone or download this project
1. [Install][] Jekyll
1. Download dependencies: `bundle`
1. Build and preview: `bundle exec jekyll serve`
1. Add content

The above commands should be executed from the root directory of this project.

Read more at Jekyll's [documentation][].

## GitLab User or Group Pages

To use this project as your user/group website, you will need one additional
step: just rename your project to `namespace.gitlab.io`, where `namespace` is
your `username` or `groupname`. This can be done by navigating to your
project's **Settings**.

Read more about [user/group Pages][userpages] and [project Pages][projpages].

## Did you fork this project?

If you forked this project for your own use, please go to your project's
**Settings** and remove the forking relationship, which won't be necessary
unless you want to contribute back to the upstream project.

## Other examples

* [jekyll-branched](https://gitlab.com/pages/jekyll-branched) demonstrates how you can keep your GitLab Pages site in one branch and your project's source code in another.
* The [jekyll-themes](https://gitlab.com/groups/jekyll-themes) group contains a collection of example projects you can fork (like this one) having different visual styles.

## Troubleshooting

1. CSS is missing! That means two things:
    * Either that you have wrongly set up the CSS URL in your templates, or
    * your static generator has a configuration option that needs to be explicitly
    set in order to serve static assets under a relative URL.

[ci]: https://about.gitlab.com/gitlab-ci/
[Jekyll]: http://jekyllrb.com/
[install]: https://jekyllrb.com/docs/installation/
[documentation]: https://jekyllrb.com/docs/home/
[userpages]: https://docs.gitlab.com/ce/user/project/pages/introduction.html#user-or-group-pages
[projpages]: https://docs.gitlab.com/ce/user/project/pages/introduction.html#project-pages
