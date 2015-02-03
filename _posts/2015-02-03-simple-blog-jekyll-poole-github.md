---
layout: post
title: How I Made This Blog Using Jekyll, Poole, and GitHub Pages
---

### About

I'm currently attending [Epicodus](http://www.epicodus.com/), which is an intensive 17-week programming bootcamp in Portland, Oregon. As part of my goal of becoming a developer, I've been wanting to create a blog so that I can practice writing while documenting my learning process. I tried to write the following tutorial to be as beginner-friendly as possible, but basic knowledge of Git and Ruby gems is assumed.

### Jekyll and Poole

[Jekyll](http://http://jekyllrb.com/) is a static site generator that works well with [GitHub Pages](http://pages.github.com). Instead of using a dynamic CMS like Wordpress where everything is created from a database on the server, Jekyll generates all of the HTML/CSS/Javascript files locally. This makes for extremely fast and lightweight sites that are easy to work with if you're comfortable with Git. Because GitHub provides their Pages service for free, it's a very attractive combination.

Following [Joshua Lande's excellent guide](http://joshualande.com/jekyll-github-pages-poole/), I decided to use [Poole](https://getpoole.com/), which is basically a template for building Jekyll sites that provides some extra features to build upon. Even better, it comes with a couple of official themes. I chose the [Hyde theme](http://hyde.getpoole.com/) to start with because I really like the simple two column layout.

### GitHub Setup

There are a few different ways to do this and I would recommend reading through the relevant documentation on both [Github](https://help.github.com/articles/using-jekyll-with-pages/) and [Jekyll](http://jekyllrb.com/docs/github-pages/). Below I will walk through the process that worked best for me.

First, I forked [the Poole theme](https://github.com/poole/hyde) that I liked to my GitHub account. Then, I renamed my forked repository to [clemf.github.io](http://www.github.com/clemf/clemf.github.io) (substitute your own GitHub username when you do it). To rename a repository in GitHub, click on the settings button in the sidebar on the right of the page. After the repository is renamed, GitHub should automatically publish it. It may take up to 30 minutes the first time, but after that changes appear within seconds.

### Setting Up Local Development

Now that the repository is set up on GitHub, it's time to set up your local environment. First, clone the repository to a directory on your computer.

```
$ git clone https://www.github.com/clemf/clemf.github.io.git
```

GitHub has provided a Ruby gem that makes sure your site will stay compatible with Pages. To use the gem, create a `Gemfile` in your repository, and add the following lines.

```
source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
```
After saving the file, run `bundle install` to install the gems.

### Configuring Jekyll

Basic configuration of Jekyll is done through the `_config.yml` file. The first thing I would recommend is to remove the default `url:` setting. If you don't do this, you won't be able to properly preview your site. Next, you can change some of the self-explanatory attributes like `title:` and `author:`.

Let's get our local Jekyll server running so that we can see the changes we've made:

```
$ bundle exec jekyll serve
```

Once the server is running, open your browser and navigate to `localhost:4000`. You should now see your site running with the default posts and whatever changes you have made. By default auto-regeneration should be on, so all you have to do is refresh the page to see changes as you edit your site and write posts.

### Writing Posts

[Writing posts with Jekyll](http://jekyllrb.com/docs/posts/) is as easy as editing a text file in the `_posts` directory, and all formatting is done using [Markdown](http://en.wikipedia.org/wiki/Markdown). If you've written a README for a GitHub project, you should already be familiar with the syntax. If you need help using Markdown, check out [Adam Pritchard's Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet). The easiest way to start is by editing one of the default posts that come with Jekyll.

### Post filenames

Jekyll interprets the date and title from the filename of the post in this manner:

```
YYYY-MM-DD-title.md
```

For instance, the filename of this post is:

```
2015-02-03-simple-blog-jekyll-poole-github.md
```

The date becomes the date, and the title becomes both the default title and URL of your post.

### YAML Front Matter

The beginning of a Jekyll post file contains a special block called the [YAML Front Matter](http://jekyllrb.com/docs/frontmatter/). It contains some YAML variables between a set of triple dashed lines. For this post, it looks like so:

```
---
layout: post
title: How I Made This Blog Using Jekyll, Poole, and GitHub Pages
---
```

There are many options that can be set here, but for now you can just change the post title if you want it to be different from the URL.

### Publish

The beauty of using Jekyll with GitHub is that all you have to do to publish a post is to push it to the repository using Git! Don't forget to commit any changes you've made beforehand.

```
$ git push origin master
```

Now your blog should be up and running on GitHub Pages (remember, that's *your-username*.gihub.io).

### Resources

There's a lot more that you can do with Jekyll that I haven't covered here, such as adding comments or Google Analytics to posts. Here are some of the resources I used to put together this tutorial, for further exploration:

* [GitHub Pages Documentation](https://help.github.com/categories/github-pages-basics/)
* [Jekyll Documentation](http://jekyllrb.com/docs/home/)
* [Joshua Lande: How I Created a Beautiful and Minimal Blog Using Jekyll, Github Pages, and poole](http://joshualande.com/jekyll-github-pages-poole/)
* [Smashing Magazine: Build A Blog With Jekyll And GitHub Pages](http://www.smashingmagazine.com/2014/08/01/build-blog-jekyll-github-pages/)
* [Adam Pritchard: Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [Github repository for this site](https://www.github.com/clemf/clemf.github.io)
