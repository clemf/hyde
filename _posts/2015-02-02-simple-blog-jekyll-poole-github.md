---
layout: post
title: How I Made This Blog Using Jekyll, Poole, and GitHub Pages
---

### Why I'm Blogging

I'm currently attending [Epicodus](http://www.epicodus.com/), which is an intensive 17-week programming bootcamp in Portland, Oregon. As part of my goal of becoming a developer, I've been wanting to create a blog so that I can practice writing while documenting my learning process.

### Jekyll and Poole

[Jekyll](http://http://jekyllrb.com/) is a static site generator that works well with [GitHub Pages](http://pages.github.com). Instead of using a dynamic CMS like Wordpress where everything is created from a database on the server, Jekyll generates all of the HTML/CSS/Javascript files locally. This makes for extremely fast and lightweight sites that are easy to work with if you're comfortable with Git. Because GitHub provides their Pages service for free, it's a very attractive combination.

Following [Joshua Lande's excellent guide](http://joshualande.com/jekyll-github-pages-poole/), I decided to use [Poole](https://getpoole.com/), which is basically a template for building Jekyll sites that provides some extra features to build upon. Even better, it comes with a couple of official themes. I chose the [Hyde theme](http://hyde.getpoole.com/) to start with because I really like the simple two column layout.

### GitHub Setup

There are a few different ways to do this and I would recommend reading through the relevant documentation on both [Github](https://help.github.com/articles/using-jekyll-with-pages/) and [Jekyll](http://jekyllrb.com/docs/github-pages/). Below I will walk through the process that worked best for me.

First, I forked [the Poole theme](https://github.com/poole/hyde) that I liked to my GitHub account. Then, I renamed my forked repository to *github_username*.github.io (in my case, [clemf.github.io](http://www.github.com/clemf/clemf.github.io)). To rename a repository in GitHub, click on the settings button in the sidebar to the right of the page. After the repository is renamed, GitHub should automatically publish it. It may take up to 30 minutes the first time, but after that changes appear within seconds.

Now that the repository is set up on GitHub, you can clone it to your local computer and start modifying it to fit your needs.

### Configuring Jekyll





http://www.smashingmagazine.com/2014/08/01/build-blog-jekyll-github-pages/


