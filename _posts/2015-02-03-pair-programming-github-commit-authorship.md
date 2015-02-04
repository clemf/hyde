---
layout: post
title: Pairing With Different Email Domains Using Pivotal
---

### Pairing

Pair programming is awesome. At Epicodus I am currently spending four days a week coding collaboratively with another student. There are so many benefits to learning and coding this way. It allows me to improve my communication and social abilities at the same time that I learn technical skills. I think that learning to effectively communicate and work well with others is at least as important as the technical side, if not more.

### Git Support for Pairing

Unfortunately, Git has no support for multiple authors in one commit. There are a number of scripts out there that deal with this problem, usually by concatenating both author's names and making a special email address. At Epicodus we are using the Ruby gem [simple-git-pair](https://github.com/fsproru/simple-git-pair), which is true to it's name. All simple-git-pair does is change the Git `user.name` to include both pairs (i.e. [Clem Freeman & Luke Chinworth](https://github.com/clemf/epicodus-rps/commit/e0938604fa205f0521332404d801ee156a6910fd)), but it leaves the `user.email` alone. For most of our work in class, this is set to `student@epicodus.com`.

### GitHub Commit Attribution

The problem with our setup is that GitHub relies on the email to credit the commit to your account When the `user.email` is `student@epicodus.com`, no one gets credit for it. This means that our GitHub profile will look a lot less active, and people will have to dig through individual repositories to see all the work we've been doing. I wanted to find a better solution that gave both pair members some credit for commits on their profiles.

### Pivotal Git Scripts

Pivotal is a software consulting company that maintains a set of [git scripts for pairing](https://github.com/pivotal/git_scripts). Unlike most scripts I found, theirs actually has a feature for switching email addresses when committing. Here is `git-pair-commit` described in their [README](https://github.com/pivotal/git_scripts/blob/master/README.md):


> **git-pair-commit**
>
> Makes a git commit as normal, but chooses one of the pair members randomly to get credit for the commit on github (by setting the author email to that member's email address). The author name on the commit will list all members of the pair, as usual.

It sounds perfect, right? Almost. The problem is that Pivotal assumes both pairs are using email addresses on the same domain. I'm sure this is great for their workflow, but it's a problem for pair members from different organizations. Not all students here at Epicodus are using the same email service, so this solution is not optimal.

### Undocumented Features to the Rescue

After spending a few days trying to figure out another way to solve to this problem, I found out that the feature I want is already in Pivotal's Git Scripts! GitHub user [zrob](https://github.com/zrob) added it last year, as [seen here](https://github.com/pivotal/git_scripts/pull/24). It's just not mentioned in the README.

Here is how you set up different email domains in your `.pairs` file:

```
# .pairs - configuration for 'git pair'
pairs:
  # <initials>: <Firstname> <Lastname>[; <email-id>]
  cf: Clem Freeman
  lc: Luke Chinworth
email_addresses:
  cf: clem@clem.com
  lc: luke@luke.com
```

This is all you need to get the random author email feature to work, just make sure you always use `git-pair-commit` when committing. Now both people can get some green squares on their GitHub profile.
